---
type: posts
layout: post
lang: ca
comments: true
title: Segona reparació d'una font d'alimentació Agilent E3644A (DC Power Supply)
name: PSAgilent2
permalink: reparació2-agilent-E3644A
category: reparació
keywords: reparació, repair, font alimentació, power supply, Agilent, HP, Keysight, E3644A
---

Sí, ho he fet..he cremat <a href="http://momex.cat/reparaci%C3%B3-agilent-E3644A" target="_blank">la font d'alimentació</a> que fa un temps vaig arreglar. Tot va passar molt ràpid, jugant amb una bateria, la vaig connectar i el <i>magic smoke</i> va impregnar tota l'habitació. Així que ara només toca fer una cosa, arreglar-la un altre cop!<br>

Com que hi ha alguna cosa cremada però la font segueix funcionant, o això sembla mirant la pantalla, crec que és una bona oportunitat per veure com reacciona la font quan li demano d'incrementar el voltatge.<br>
<center>
<img style="display:inline" src="/images/170123-E3644A_2/00.jpg" width="99%" alt="Contingut: E3644A failure. Source: Momex.cat">
</center>

Com veieu, a l'incrementar el voltatge el corrent augmenta lliurement encara que no hi hagi res connectat als borns de sortida. Aparentment no sembla que s'hagi fet malbé cap microcontrolador ja que el sistema respon als botons. A més a més, que la font pugui mesurar la intensitat em fa pensar que hi ha alguna cosa curtcircuitant els borns + i - entre la sortida i els <i>shunt resistors</i> (resistències de valor i tolerància molt baixos que permeten, mesurant la caiguda de voltatge entre pins, calcular el corrent que les travessa). El següent pas serà treure la tapa i guiar-nos per l'olor i la vista.<br>
<!--more-->
<center>
<img style="display:inline" src="/images/170123-E3644A_2/01.jpg" width="49%" alt="Contingut: E3644A MCR264-4 failure. Source: Momex.cat">
<img style="display:inline" src="/images/170123-E3644A_2/02.jpg" width="49%" alt="Contingut: E3644A MCR264-4 failure. Source: Momex.cat">
</center>

En menys de 3 segons ja veig el component culpable d'aquesta olor tan profunda a plàstic cremat. Un tal CR504 <i>a.k.a.</i> Motorola MCR264-4 (<i>Silicon Controlled Rectifier</i>).

<center>
<img style="display:inline" src="/images/170123-E3644A_2/03.jpg" width="99%" alt="Contingut: E3644A MCR264-4 failure. Source: Momex.cat">
</center>

Podria desoldar el component, comprar-ne un altre i soldar-lo de nou, però podria emportar-me una sorpresa i veure més <i>magic smoke</i> fluint d'altres parts. Crec que el més sensat seria primer mirar què fa aquest <i>SCR</i> i a quins components està connectat per veure si tenen indicis d'estar afectats. Llapis, llibreta, multímetre a la mà i començo a dibuixar el circuit amb una mica de dificultat ja que la <i>PCB</i> és de 3 capes. Amb una mica de traça aconsegueixo dibuixar un petit esquemàtic:<br>
<center>
<img style="display:inline" src="/images/170123-E3644A_2/04.jpg" width="39%" alt="Contingut: E3644A PCB 3 capes. Source: Momex.cat">
<img style="display:inline" src="/images/170123-E3644A_2/05.png" width="59%" alt="Contingut: E3644A esquemàtic. Source: Momex.cat">
</center>

Paral·lelament començo a fer una mica d'arqueologia a Google i em trobo amb uns <a href="http://exodus.poly.edu/~kurt/manuals/manuals/HP%20Agilent/HP%20E3640A,%2041A,%2042A,%2043A,%2044A,%2045A%20User.pdf" target="_blank">esquemàtics</a> amb data Gener 2000 per a les fonts d'alimentació E3640A, E3641A, E3642A, E3643A, E3644A i E3645A. A la pàgina 199 em trobo amb la part d'esquemàtic <i>A-Power Circuit and protection circuit</i> i veig que una part del circuit em resulta familiar.
<center>
<img style="display:inline" src="/images/170123-E3644A_2/06.png" width="99%" alt="Contingut: E3642A esquemàtic. Source: Momex.cat">
</center>
<center>
<img style="display:inline" src="/images/170123-E3644A_2/07.png" width="70%" alt="Contingut: E3642A esquemàtic SCR Crowbar protection circuit. Source: Momex.cat">
</center>

Efectivament, ara tot comença a cobrar sentit. El que s'ha cremat és l'SCR que forma part d'un dels sistemes de protecció contra l'<i>overvoltage</i>. En anglès se'l coneix com a <i>Crowbar protection circuit</i>. El funcionament és a simple vista bastant senzill, hi ha un circuit que controla la sortida de voltatge i ràpidament genera un curtcircuit entre terminals si el voltatge de sortida supera un llindar que es pot ajustar per <i>hardware</i> o <i>software</i>. La funció del <i>crowbar</i> és la de protegir el <i>DUT</i>, de l'anglès <i>Device Under Test</i>, contra aquesta possibilitat i assegura que la font d'alimentació mai superarà el valor predeterminat. Els elements i CIs principals utilitzats en aquest sistema són:<br>
<br>
- <u>MCR264 (CR504)</u>: <i>Silicon Controlled Rectifier</i>. És l'element que curtcircuita els terminals + i - i per tant si el fusible no falla abans (en cas de fallada interna de la font), aquest component acabarà cremat degut a la insuficient dissipació de calor (és el que ens ha passat a nosaltres).<br>
- <u>OC3020 (U132)</u>: <i>Optocoupler / Optoisolator</i>. Aquest element serà l'encarregat, un cop rebut el senyal corresponent, d'activar l'SCR.<br>
- <u>MC3423 (U135)</u>: <i>Overvoltage Crowbar Sensing Circuit</i>. Aquest CI és l'encarregat d'enviar el senyal d'activació de l'SCR quan detecta que el voltatge als terminals és superior al valor per defecte.<br>
- <u>TL074C (U127)</u>: <i>OPAMP</i>. <a href="https://ca.wikipedia.org/wiki/Amplificador_operacional" target="_blank">Amplificador Operacional</a>.


He de reconèixer que tot això ha passat per no aplicar el sentit comú i per no llegir el <a href="http://cp.literature.agilent.com/litweb/pdf/E3640-90001.pdf" target="_blank">manual</a> (<a href="https://en.wikipedia.org/wiki/RTFM" target="_blank">RTFM</a>) de la font. Allà hi diu clarament:<br>

<i><font size="4">The power supply’s OVP circuit contains a crowbar SCR, which effectively shorts the output of the power supply whenever the overvoltage condition occurs. If an external voltage source such as a battery is connected across the output, and the overvoltage condition inadvertently occurs, the SCR will continuously sink a large current from the source and possibly damaging the power supply. To avoid this, a diode must be connected in series with the output as shown in Figure 2-1</font></i><br>
<center>
<img style="display:inline" src="/images/170123-E3644A_2/00b.jpg" width="40%" alt="Contingut: E3644A Manual d'usuari per connectar una bateria a la font d'alimentació. Source: Momex.cat">
</center>

És a dir, si hagués col·locat un diode com ho hagués fet una persona amb dos dits de front o hagués llegit el manual, res de tot això hagués passat, però... on està la diversió sinó?<br>

Un cop ja sabem tot això, què ens queda? Doncs comprar un substitut i com que aquest CI ja està descatalogat ens toca comprar un alternatiu de característiques similars com el TYN640RG (<i>Repetitive peak off-stat voltage</i>: 600V, <i>On-state max current</i>: 40A, <i>Sensitivity</i>: 35mA). Recordem que l'original era el MCR264-4 (200V, 40A i 50mA).<br>
 Un cop el rebem a casa, desoldem l'antic i soldem el nou, al ser <a href="https://en.wikipedia.org/wiki/Through-hole_technology" target="_blank"><i>through-hole</i></a> l'operació és molt senzilla (donem gràcies). Un cop finalitzat, comprovem la resistència entre terminals amb el multímetre i veiem que no és molt alta..per no dir que hi ha literlament continuïtat (14 Ohms). No hi ha res a simple vista que sembli cremat així que penso que pot ser alguna altra part del circuit i que sigui totalment normal..si? mmm...<br>

Moment de la veritat, connectem l'endoll i engegem l'aparell... vaja, el que em temia, tot segueix igual. Ara em tocarà tornar a fer tota aquella feinada de mirar component a component aviam si està dins dels valors que vaig veure l'altre cop. De totes maneres, decideixo donar-hi un altre cop d'ull i afinar una mica més el nas. La veritat és que encara hi ha alguna cosa que fa olor a cremat. Començo a mirar els <a href="https://ca.wikipedia.org/wiki/Varistor" target="_blank">varistors</a> un per un i de cop i volta, allà, amagat a sota del transformador, veig un altre CI TO220-3 cremat.<br>

<center>
<img style="display:inline" src="/images/170123-E3644A_2/09.jpg" width="32%" alt="Contingut: E3644A MUR1615CT Cremat. Source: Momex.cat">
<img style="display:inline" src="/images/170123-E3644A_2/10.jpg" width="66%" alt="Contingut: E3644A MUR1615CT Cremat. Source: Momex.cat">
</center>

I aquest component és el CR500 <i>a.k.a.</i> MUR1615CT (Switch-mode power rectifier). En aquest cas, si que el trobo disponible al web i demano recanvis (mínim un paquet de 10). Mentrestant arriba el recanvi, aprofito per mirar un altre cop l'esquemàtic per entendre quina és la seva connexió.<br>
<center>
<img style="display:inline" src="/images/170123-E3644A_2/11.png" width="80%" alt="Contingut: E3642A esquemàtic MUR1615CT. Source: Momex.cat">
</center>

Com veieu, està a tocar dels terminals de sortida i mirant la caiguda de voltatge entre ànode i càtode dels diodes estaven clarament cremats. Per tant ara m'explico perquè encara hi havia continuïtat entre terminals. Un cop rebut el recanvi, el substitueixo, engego la font d'alimentació i el problema està efectivament <b>resolt!!</b>.<br>
Us deixo amb unes últimes imatges del recanvi i dels dos caiguts...<br>
<center>
<img style="display:inline" src="/images/170123-E3644A_2/13.jpg" width="49%" alt="Contingut: E3642A MUR1615CT substituït. Source: Momex.cat">
<img style="display:inline" src="/images/170123-E3644A_2/12.jpg" width="49%" alt="Contingut: E3642A MCR264-4 i MUR1615CT cremats. Source: Momex.cat">
</center>



