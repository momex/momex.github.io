---
type: posts
layout: post
lang: ca
comments: true
title: Tacòmetre Digital per a Harley Davidson Sportster (Part 7 - Components)
name: HD-tacho-part7
permalink: HD-tacho-part7
category: tacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, components
---

En aquesta part llistaré els components i circuits integrats (CI) que he utilitzat. A continuació teniu un diagrama bàsic del circuit (l'esquemàtic sencer detallat vindrà a la secció posterior).<br>
<center><img src="/images/Part7/schematic1.PNG" width="80%" alt="Diagrama bàsic del circuit. Source: Xavier Morales" title="Diagrama bàsic del circuit"></center>

<font size="3"><b>Nota</b>: El Digit3 s'alternarà amb la barra de revolucions. En el mode RPM es veuran tots 4 dígits però en la resta de modes el Digit3 romandrà OFF i serà la barra la que mostarà les RPM. La resta de modes poden funcionar amb només 3 dígits.</font>

### Microchip PIC18F2553<br>

El <a href="http://www.microchip.com/wwwproducts/en/PIC18F2553" target="_blank">PIC18F2553</a> és el cervell del projecte. Us mentiria si digués que vaig escollir aquesta marca i model en concret per ser el que incorporava les millors prestacions en relació amb el preu. Simplement el vaig escollir perquè era la familia de MCU amb la qual vaig començar en aquest món de l'electrònica digital i era el model el qual tenia un nombre de pins suficients per poder desenvolupar el compta-revoucions que tenia al cap.<br>
<!--more-->
<center>
<img style="display:inline" src="/images/Part7/PIC18F2553.png" width="29%" alt="PIC18F2553. Source: Microchip Technology" title="PIC18F2553">
<img style="display:inline" src="/images/Part7/PIC18F2553_sch.jpg" width="70%" alt="PIC18F2553 pinout. Source: Microchip Technology" title="PIC18F2553 pinout">
</center>

Característiques i requeriments:
<dl>
- <b>Velocitat de processament</b>: segons el seu pdf d'especificacions, aquest PIC pot arribar fins als 48MHz. Per aquesta aplicació, 20MHz seran suficients.<br>
- <b>Interrupcions</b>: en necessitarem només una per poder parar temporalment el loop infinit i llegir el missatge entrant pel bus J1850.<br>
- <b>Timers</b>: n'hi ha 4 disponibles i els utilitzaré de la següent manera.<br>
<dd>TO: funcions relacionades amb l'enviament i recepció de missatges del protocol SAE j1850.</dd>
<dd>T1: codi principal (<i>main</i>).</dd>
<dd>T2: regular la lluminositat via control PWM pel <i>LED display driver</i>.</dd>
<dd>T3: enviar la informació al <i>driver</i> dels 7-Segments (CLK).</dd>
- <b>I/O</b>: necessaris pel botó, transistors, senyals cap al <i>driver</i> dels 7-segments, etc. <br>
- <b>PWM</b>: regular la lluminositat via control PWM pel <i>LED display driver</i>.<br>
- <b>USART</b>: Si volem tenir la possibilitat de fer un <i>datalogger</i> aquesta característica ens anirà bé.<br>
</dl>

A part, necessitarem també:<br>

- <b>In-Circuit Debugger/Programmer</b>: és a dir, un Programador específic per PICs. En aquest projecte vaig utilitzar el <a href="https://en.wikipedia.org/wiki/PICkit" target="_blank">PICkit 2 i PICkit 3</a>, de la mateixa casa Microchip Technology. Aquests aparells es connecten entre l'ordinador (via USB) i el circuit integrat programable o PIC (via 3 pins; PGC, PGD i MCLR) i et permeten reprogramar el PIC amb el codi que has compilat previament.<br>
<center><img style="display:inline" src="/images/Part7/pickit3.png" width="50%" alt="PICkit 3. Source: Microchip Technology" title="PICkit 3"></center>
- <a href="https://en.wikipedia.org/wiki/MPLAB" target="_blank"><b>MPLAB</b></a> és un IDE (<i>Integrated Development Environtment</i>) o editor pel desenvolupament d'aplicacions en microcontroladors PIC. Et permet editar i compilar codi que després, amb ajuda del PICkit, podràs programar al teu PIC. <br>


### Micrel/Microchip MM5450YN<br>
Si el PIC és el cervell del projecte, l'<a href="http://ww1.microchip.com/downloads/en/DeviceDoc/mm5450.pdf" target="_blank">MM5450</a> és el cor. Aquest CI et permet controlar un munt de pins d'una manera molt fàcil. Com a curiositat, segons el seu web, al 2015 Microchip va comprar Micrel.
<center>
<img style="display:inline" src="/images/Part7/MM5450.png" width="29%" alt="MM5450. Source: Micrel" title="MM5450">
<img style="display:inline" src="/images/Part7/Micrel_sch.jpg" width="50%" alt="MM5450 pinout. Source: Micrel" title="MM5450 pinout">
</center>

Característiques principals:<br>
<dl>
- <b>Control de lluminositat</b>: Aquest CI té 1 pin (#19) específic per regular la lluminositat de tots els pins. Amb un senyal PWM del PIC i una resistència podrem regular la lluminositat digitalment variant el DC (<a href="https://en.wikipedia.org/wiki/Duty_cycle" target="_blank">Duty cycle</a>) del senyal PWM.<br>

- <b>Serial Data input</b>: Els 34 inputs d'aquest <i>LED driver</i> es controlen mitjançant 2 pins; un senyal de rellotge (CLK) i un senyal de data (DATA). 
<center><img style="display:inline" src="/images/Part7/MM5450_CLK_DATA.PNG" width="60%" alt="Senyals DATA i CLK. Source: Xavier Morales" title="Senyals DATA i CLK"></center>
L'MM5450 sempre espera 36 senyals de rellotge (flancs de pujada). En el primer, verificarà que el senyal al pin DATA sigui de valor alt. Si és així, començarà a guardar els valors de DATA que llegeixi a mesura que rebi els 35 <i>clocks</i> següents. Un cop rebi l'últim <i>clock</i> (a l'MM5450 amb només 34 pins operatius, el valor llegit al 35è flanc de pujada no es considerarà, però s'ha d'enviar igualment) el CI volcarà els valors a les sortides i tornarà a esperar els 36 nous valors següents.<br>

- <b>34 pins</b>: El següent diagrama mostra com s'utilitzaran tots els pins de l'MM5450. L'alternativa seria la de multiplexar els 7-Segments, això em portaria a consumir 12 pins en comptes de 29, però per causes que explicaré a la Part 14 (Problemes durant el projecte) vaig optar per aquesta configuració.<br>
<center><img style="display:inline" src="/images/Part7/MM5450_non_multi.PNG" width="80%" alt="Diagrama de connexió. Source: Xavier Morales" title="Diagrama de connexió"></center>
</dl>

### LM340T-5.0/NOPB<br>
Sens dubte, per a mi aquest <a href="http://www.ti.com/lit/ds/symlink/lm340-n.pdf" target="_blank">Regulador de Voltatge Fix</a> de 5V de Texas Instruments (TI) ofereix la millor solució en format circuit integrat per tenir una font d'alimentació senzilla, fiable i a 5V.<br>
<center><img style="display:inline" src="/images/Part7/LM340T.png" width="20%" alt="LM340T Source: desconegut" title="LM340T-5V"></center>
Característiques:<br>
- Capaç de proporcionar un màxim d'1A de corrent a la sortida. S'ha de combinar amb un <i>heat sink</i> (disipador de calor).<br>
- Protecció contra excés de temperatura.<br>
- Protecció contra curtcircuits (limitació de corrent)<br>

### Trasnceiver
Per poder llegir els senyals del bus J1850 necessitem primer adaptar els nivells de tensió entre el bus i el PIC. Hi ha circuits integrats com  el <a href="http://www.nxp.com/files/analog/doc/data_sheet/MC33990.pdf" target="_blank">MC33990</a> (NXP Feescale Semiconductor) o <a href="http://alt.ife.tugraz.at/datashts/Harris/hip7020.pdf" target="_blank">HIP7020</a> (HARRIS Semiconductor), però al ser una tecnologia tan antiga estan descatalogats i trobar-los no és tasca fàcil.
<center><img style="display:inline" src="/images/Part7/MC33990_chip.PNG" width="20%" alt="MC33990 Source: Xavier Morales" title="LM340T-5V">
<img style="display:inline" src="/images/Part7/j1850_chip_comparison.PNG" width="70%" alt="MC33990 i HIP7020 Source: Xavier Morales" title="MC33990 i HIP7020 pinout"></center>

 No obstant, actualment utilitzo el MC33990 per enviar senyals de marxa i revolucions fictícies a un bus J1850 que uneix aquesta unitat de control amb el compta-revolucions, d'aquesta manera puc introduir millores sense necessitat d'anar físicament a la moto.<br>
<center>
<img style="display:inline" src="/images/Part7/MC33990_sch.PNG" width="49%" alt="MC33990 Diagrama Source: Xavier Morales" title="Diagrama de MC33990">
<img style="display:inline" src="/images/Part7/MC33990_osc.png" width="49%" alt="Forma dels senyals amb MC33990 Source: Xavier Morales" title="Forma dels senyals amb MC33990">
</center>

L'alternativa a aquests circuits integrats és utilitzar transistors i resistències per adaptar els nivells entre el bus i el PIC. Com només necessitarem llegir del bus, el circuit quedarà molt simplificat tal i com es pot veure a la imatge inferior. Un detall a destacar és veure com canvien els nivells de voltage a mesura que avancem pel circuit i com queden invertits al final (veieu la captura de l'oscil·loscopi per etendre-ho millor). Si es vol utilitzar el mateix codi que amb el MC33990, a nivell de software només s'haurà d'invertir el valor de l'entrada al PIC amb un "!" i el més important, canviar el tipus d'interrupció per una de tipus "flanc de baixada".
<center>
<img style="display:inline" src="/images/Part7/transceiver_levels.PNG" width="49%" alt="Diagrama transceiver Source: Xavier Morales" title="Diagrama transceiver">
<img style="display:inline" src="/images/Part7/transceiver.png" width="49%" alt="Forma dels senyals Source: desconegut" title="Forma dels senyals a l'oscil·loscopi">
</center>
<br>


<p>
<font size="2"> 
Índex de projecte:<br>
<a href="/HD-tacho-part1">Part1 </a>/
<a href="/HD-tacho-part2"> Part2 </a>/
<a href="/HD-tacho-part3"> Part3 </a>/
<a href="/HD-tacho-part4"> Part4 </a>/
<a href="/HD-tacho-part5"> Part5 </a>/
<a href="/HD-tacho-part6"> Part6 </a>/
<b> Part7 </b>/
<a href="/HD-tacho-part8"> Part8 </a>/
<a href="/HD-tacho-part9"> Part9 </a>/
<a href="/HD-tacho-part10"> Part10 </a>/
<a href="/HD-tacho-part11"> Part11 </a>/
<a href="/HD-tacho-part12"> Part12 </a>/
 Part13 /
 Part14 /
 Part15
 </font>
</p>
