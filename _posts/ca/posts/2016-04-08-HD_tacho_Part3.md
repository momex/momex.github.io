---
type: posts
layout: post
lang: ca
comments: true
title: Tacòmetre Digital per a Harley Davidson Sportster (Part 3 - Harley Davidson i SAE J1850 VPW)
name: HD-tacho-part3
permalink: HD-tacho-part3
category: tacho
keywords: HD, harley, davidson, tachometer, tacho, rpm, J1850, SAE, VPW, especificacions
---

La manera curta i millor d'entendre aquest protocol és llegint <a href="http://download.intel.com/design/intarch/papers/j1850_wp.pdf" target="_blank">aquest document</a> (en anglès). La manera llarga és llegint directament la SAE J1850. De totes maneres, tot seguit resumiré els punts bàsics que s'han d'entendre per a poder programar un codi per rebre i interpretar els missatges de l'ECU motor. <br>

D'acord amb l'estandard SAE J1850 VPW, a la moto tindrem un sol cable per on circularà la informació en funció d'uns nivells de voltatge i d'un temps de transmissió. Els nivells són: <br>
- <u>Passiu</u>: 0 - 3,5V (estat natural del bus)<br>
- <u>Actiu</u>: 4,25V - 20V (les unitats de control poden activar el bus mitjançant transistors)<br>
<br>
Les principals propietats del bus són:<br>
- <u>Serial bus</u>: l'informació s'envia bit a bit.<br>
- <u>Asíncron</u>: la informació que s'envia entre nodes és controlada pel mateix emissor en comptes de ser sincronitzada per un señal de rellotge.<br>
- <u>Master-less</u>: cap node té superioritat o té el control sobre els altres.<br>
- <u>Peer to peer</u>: tots els nodes tenen la mateixa capacitat de transmetre en tot moment.<br>
<br>
Una propietat molt important dels nodes és que quan un node parla, ell mateix analitza el bus per saber si el que està dient és efectivament el que hi ha al bus, més endavant entendrem el per què.<br>
<!--more-->
<dl></dl>

### Arbitrarietat:

En aquest tipus de busos tothom podrà parlar quan vulgui i per això s'ha d'establir unes regles per a que tothom s'entengui. N'hi haurà dues:<br>
<dl>
<b>1-</b> El node escolta el bus.
   <dd><b>a)</b> Si ningú està transmetent un missatge durant un temps predefinit, llavors el node pot començar a transmetre.<br></dd>
   <dd><b>b)</b> Si algú està transmetent, llavors s'espera a que acabi i després s'espera un temps determinat abans de començar a transmetre.<br></dd>
<b>2-</b> Un cop està transmetent el missatge, en el cas en que el bit que està transmetent no sigui el mateix que el que s'està transmetent al bus, automàticament pararà ja que ha perdut l'arbitrarietat. Això vol dir que un altre node està transmetent un missatge que té més prioritat que el seu.
</dl>

<img src="/images/Part3/02.PNG" alt="Xavier Morales">

<dt>I com és defineix la prioritat dels missatges?</dt>
Tot es resol físicament. Com ja hem dit, el bus està en estat natural en mode passiu i per tant, els nodes només han d'activar o desactivar el transistor per posar el bus en mode actiu o passiu. Si un node està transmetent un bit passiu però llegeix que el bus està actiu, això vol dir que algun altre node està parlant a la vegada.
<dt>Idò?</dt> 
Tot radica als 3 bytes de la capçalera del missatge. Allà, un d'aquests bytes indica la prioritat del missatge que l'enginyer haurà establert amb anterioritat (per exemple: un missatge de RPM ha de ser més important que un missatge de temperatura, ja que en un segon la temperatura és bastant estable degut a la inèrcia tèrmica però les RPM poden variar molt).<br>
Els missatges amb més prioritat seran per tant aquells amb més bits actius al començament del missatge.

### Composició d'un missatge:
Parts d'un missatge típic a Harley Davidson:
<img src="/images/Part3/01.PNG" alt="Xavier Morales">

Amb aquest format el màxim número de bytes que es pot enviar al cos del missatge és d'11.<br>

<dt>SOF (Start Of Frame = Inici de Missatge)</dt>
El node que vulgui començar a transmetre un missatge ha de començar amb un bit actiu de 200us. Després d'aquest temps, a continuació vindrà la informació de la capçalera.

<dt>Header (Capçalera)</dt>
Pot estar composta des d'un fins a tres bytes. En el cas particular d'HD hi trobarem 3 bytes:<br>
<dd><b>Byte #1:</b> Indicarà als altres nodes la configuració de la capçalera (p.exemple: 1 o 3 bytes)<br>
<img src="/images/Part3/03.PNG" alt="Xavier Morales"></dd>
<dd><b>Byte #2:</b> Adreça Objectiu o ID primari. Aquest valor el trobarem a la SAE J2178-4 i pot ser un Command ID o un Status ID.</dd>
<dd><b>Byte #3:</b> Adreça Origen</dd>

Significat del byte#1 de la capçalera:<br>
<img src="/images/Part3/04.PNG" alt="Xavier Morales">

<br>
Exemple (RPM: $28 $1B $10)<br>
<b>$28</b>
<img src="/images/Part3/05.PNG" alt="Xavier Morales">

<dl>
<dd>001: Valor proper a alta prioritat </dd>
<dd>0: Capçalera de 3 bytes</dd>
<dd>1: IFR no necessari</dd>
<dd>0: Adreça funcional</dd>
<dd>00:-</dd>
<b>$1B</b>
<dd> Adreça objectiu/ ID primari: RPM - Status ID</dd>
<b>$10</b>
<dd> Adreça d'Origen (ECM: ecu motor)</dd>
<dd> <b>Nota:</b> Altres adreces: 40 (Display), 61 (Body Control)</dd>
</dl>

<dt>Cos del Missatge</dt>
Tant l'adreça objectiu com el cos del missatge venen definits a la SAE 2178-4 (Message Definition for Three Byte Headers).<br>
Els ID primaris solen tenir ID secondaris que permeten obtenir informació més detallada. A l'exemple de les RPM, l'ID primari ($1B) en té 3:<br>

<dd> Sec ID 01- Baixa Resolució - PRN 1022</dd>
<dd> Sec ID 02 - Alta Resolució - PRN 000C</dd>
<dd> Sec ID 20 - RPM ralentí - PRN 1023</dd>
<br>
El PRN (Paremeter Reference Number) és una referència que surt especificada en aquesta SAE 2178-4 per a cadascun dels Sec ID. Amb aquest PRN podrem anar a la SAE 2178-2 (Data Parameter Definitions) i saber quants bytes rebrem, fórmula per convertir els bytes rebuts en un valor decimal i quines unitats seran. <br>

Per exemple, si busquem pel PRN 000C (RPM - Alta Resolució), ens diu que les unitats són RPM i que la resolució és d'1/4 (1bit=0,25 rpm). Per tant, si rebem pel bus els bytes <b>28 1B 10 02 0A F0</b> tindrem:<br>

<dd><b>28 1B 10</b>: Capçalera d'RPM</dd>
<dd><b>02</b>: ID Secondari per RPM d'alta resolució</dd>
<dd><b>0A F0</b>: Valor d'RPM. Per calcular-lo farem:<br> 
<dd>(byte0 * 0x100+byte1)/4= (0x0A * 0x100+0xF0)/4<br></dd>
<dd>(10 * 256+240)/4= (2560+240)/4= 2800/4= 700rpm</dd>
<br>

<dt>CRC (Cyclical Redundant Check = Comprobació cíclica de redundància)</dt>
És 1 byte després del cos del missatge que s'ha obtingut pel node emissor mitjançant un càlcul matemàtic. Aquést número (CRC) és únic per aquesta combinació de bytes (capçalera + cos del missatge). Quan el node receptor ha rebut els bytes pel bus de dades també realitza la mateixa operació i obté un CRC. Si CRC enviat i calculat són el mateix, llavors vol dir que no hi ha hagut cap error de transmissió i que la informació rebuda és bona. En cas contrari, s'hauria de desestimar la informació perquè és corrupta o compromesa. <br>

<dt>End of Data (EOD)</dt>
Després del CRC, es deixa el bus en mode passiu durant 200us. Després de l'EOD, els receptors poden respondre el missatge o enviar-ne un altre de nou.

<h3>DATA BITS:</h3>

La informació enviada a través del bus és a base de 0s i 1s. Aquest protocol té la característica de que els 1s i 0s transmesos poden ser actius i passius.<br>
<dt>I què vol dir això?</dt>
Doncs que com el bus pot estar en mode actiu o passiu (explicat a dalt), podem transmetre per exemple un 1 en mode actiu o passiu, variant únicament el temps. La taula següent ho resumeix:<br>

<center>
<img style="display:inline" src="/images/Part3/06.PNG" alt="Xavier Morales"> 
<img style="display:inline" src="/images/Part3/07.PNG" alt="Xavier Morales">
</center>
<br>

Exemple amb el primer byte de la capçalera anterior (<b>0x28</b>: <b>0b</b>00101000):

<img src="/images/Part3/08.PNG" alt="Xavier Morales">

Com veieu els bits es van alternant entre actiu i passiu. Com el SOF dicta quin és el primer en començar (Actiu), el primer bit de la capçalera serà passiu i la resta ja vindrà forçada per l'alternança. Tots els bits dels bytes del missatge es transmetran començant pel bit més significatiu, és a dir, bit7, bit6,..., bit0.<br>

<b>Nota:</b> Com veieu, un 0 Passiu sempre guanyarà a un 1 Passiu (El 0 és temporalment més curt i per tant canviarà al següent bit que tocarà ser Actiu abans i per tant l'1 haurà perdut l'arbitrarietat). El mateix passa amb el 0 Actiu, aquest és temporalment més llarg que l'1 Actiu.<br>

<h3>Taules d'especificació</h3>

<img src="/images/Part3/09.PNG" alt="Xavier Morales">

<h3> Capa física:</h3>
- El bus serà d'1 cable pel qual es transmetrà informació (1s i 0s) a una velocitat de 10,4 Kb/s mitjançant Pulsos d'Amplada Variable. <br>
- Màxima longitud del cable: 40m <br>
- Màxim número de nodes (unitats de control): 32 <br>
- Un bit 0 sempre ha de dominar sobre un bit 1<br>
- Màxim número de bytes al cos del missatge: 12 <br>
<br>

<img src="/images/Part3/10.PNG" alt="Xavier Morales">

<p>
<font size="2"> 
Índex de projecte:<br>
<a href="/HD-tacho-part1">Part1 </a>/
<a href="/HD-tacho-part2"> Part2 </a>/
<a href="/HD-tacho-part3"> Part3 </a>/
<a href="/HD-tacho-part4"> Part4 </a>/
<a href="/HD-tacho-part5"> Part5 </a>/
<a href="/HD-tacho-part6"> Part6 </a>/
<a href="/HD-tacho-part7"> Part7 </a>/
<a href="/HD-tacho-part8"> Part8 </a>/
<a href="/HD-tacho-part9"> Part9 </a>/
 Part10 /
 Part11 /
 Part12 /
 Part13 /
 Part14
 </font>
</p>
