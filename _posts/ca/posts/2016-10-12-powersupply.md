---
type: posts
layout: post
lang: ca
comments: true
title: Reparació de dues fonts d'alimentació Agilent E3644A (DC Power Supply)
name: PSAgilent
permalink: reparació-agilent-E3644A
category: powersupply
keywords: reparació, repair, font alimentació, power supply, Agilent, HP, Keysight, E3644A
---

Fins a dia d'avui he estat treballant amb una font d'alimentació bastant rudimentària provinent d'un ordinador que s'anava a llençar. Amb això i gràcies a un parell de modificacions senzilles, vaig aconseguir unes sortides a 12, 5 i 3,3 Volts.<br>
El mes passat, donant un cop d'ull a llocs web de segona mà, vaig trobar un parell de fonts d'alimentació que es venien com a peces ja que no funcionaven. Es tractava de dues fonts d'alimentació <i>Agilent E3644A</i> amb una única sortida que es podia sel·leccionar en dos rangs; de 0-8V (8A) o 0-20V (4A). La descripció de l'article deia:<br>

<i><font size="4">These power supplies are not working properly.  Both displays are quite dim.  Neither can be adjusted by means of the knob on the front panel.  One has the display stuck at 46.5V and the other is stuck at -0.58V.  Both respond to button presses. No other testing was done. No manuals, cords/cables, or additional items are included if not listed or shown.</font></i><br>

Jo, que sóc un aficionat d'aquest món, la idea de comprar-les i reparar-les era una gran tentació. Només mirant les especificacions i el preu d'una unitat nova (1000€) era clar que pagava la pena córrer el risc.<br>
<center>
<img style="display:inline" src="/images/161012-E3644A/E3644A.png" width="45%" alt="Contingut: E3644A. Source: Keysight">
<img style="display:inline" src="/images/161012-E3644A/spec.png" width="45%" alt="Contingut: E3644A especificació. Source: Keysight">
</center>

<!--more-->

<b>Què m'envalentia?</b><br>
- L'article estava localitzat als USA i les dues fonts tenien un adhesiu que indicava connectar-les a una xarxa 115V 60Hz. Per sort, aquest model en concret, d'acord al manual d'usuari, permet connectar-ho a les xarxes europees (230V 50Hz) mitjançant un selector que hi ha a l'interior de l'aparell i canviant el fusible.<br>
- Dues unitats amb símptomes similars (però diferents) em permetrien comparar diferents components i facilitar la cerca del problema.<br>
- Les unitats engegen i les pantalles funcionen.<br>
<br>
<b>Què em feia enrere?</b><br>
- Donat el cas que fos molt complicat perdria diners.<br>
- No hi ha manual de servei per aquest model. És una pena ja que moltes unitats Agilent si que els tenen (circuits, llista de components i fins i tot <i>rootcause</i> analisys).<br>

<center>
<img style="display:inline" src="/images/161012-E3644A/2-E3644A.JPG" width="45%" alt="Contingut: E3644A frontal. Source: -">
<img style="display:inline" src="/images/161012-E3644A/2-E3644A-2.JPG" width="45%" alt="Contingut: E3644A part posterior. Source: -">
</center>

Total, que les vaig acabar comprant i gairebé un mes i poc després ja les tenia a casa (m'agradaria destacar el servei lamentable que ofereix adtpostales com a gestor d'aduanes). Els passos que vaig seguir fins a trobar el problema van ser:<br>
<b>1 -</b> Canviar l'ajustament de voltatge amb els seleccionadors a l'interior de l'aparell (230Vac).<br>
<b>2 -</b> Canviar el fusible (Fusible de 2A 250V per 230Vac) <br>
<center>
<img style="display:inline" src="/images/161012-E3644A/ajustamentvoltage.png" width="45%" alt="Contingut: E3644A Ajustador de voltatge d'entrada. Source: Momex.cat" title="E3644A Ajustador de voltatge d'entrada">
<img style="display:inline" src="/images/161012-E3644A/20160922_213143.jpg" width="25%" alt="Contingut: E3644A Fusible. Source: Momex.cat" title="E3644A Fusible">
</center>
<b>3-</b> Aprofitant que la tapa ja estava fora, fer una inspecció visual per entendre la configuració de la PCB i per veure si hi havia algun component fregit que es pogués identificar a simple vista. Desgraciadament, o no, tot semblava estar perfecte (cap condensador reventat, cap IC, resistència, via o pista cremada,... ) <br>
<center>
<table border="0" cellspacing="0" cellpadding="0">
	<tr>
		<td width="59%">
		<img src="/images/161012-E3644A/pcbparts.jpg" alt="Contingut: E3644A PCB parts. Source: Momex.cat" title="E3644A PCB Parts">
		</td>
		<td rowspan="2">
		<img src="/images/161012-E3644A/20160922_213305.jpg" alt="Contingut: E3644A PCB Part dreta. Source: Momex.cat" title="E3644A PCB part dreta">
		</td>
	</tr>
	<tr>
		<td>
		<img src="/images/161012-E3644A/20160922_212113.jpg" alt="Contingut: E3644A PCB Part esquerra. Source: Momex.cat" title="E3644A PCB part esquerra">
		</td>
	</tr>
</table>
</center>
<font size="4"><b>Nota:</b> els números 9935 que es veuen a sobre d'un dels condensadors gegants indiquen l'any i la setmana de la data en que aquest component es va fabricar. La majoria d'elements indiquen anys al voltant de l'any 2000, així que podem intuir que aquesta font d'alimentació es va fabricar cap aquell any (ara fa 16 anys). Segons els adhesius a la part davantera de les fonts, les dues es van calibrar ara farà un any. </font><br>

<b>4-</b> Encendre les dues fonts d'alimentació (sense la tapa) i verificar que el comportament era el mateix que el descrit.<br>
<b>PSA (<i>Power Supply A</i>):</b> La pantalla mostrava 39,6V i 1688A. Amb l'ajut d'un multímetre, el valor a la sortida era de 0V i 0A. A l'ajustar manualment el límit de V i A amb el <i>rotary encoder</i>, el sistema responia i el Voltage augmentava segons el multímetre, però la font d'alimentació no proporcionava corrent per exemple per alimentar un ventilador de 12V.<br>
<b>PSB (<i>Power Supply B</i>):</b>  La pantalla mostrava -0,58V i 0.132A que corresponia amb el valor llegit a la sortida amb un multímetre. A l'ajustar manualment el límit de V i A amb el <i>rotary encoder</i>, el sistema et permetia variar el valor del límit però la sortida no variava.<br>

<b>5-</b> Un intercanvi ràpid dels panells frontals entre les dues unitats ens permet descartar que tinguin un problema. El resultat és el mateix.<br>

<b>6-</b> Aquestes unitats tenen una rutina interna anomenada <i>Self Test</i> que fa una sèrie d'evaluacions internes (nivells voltatge, memòria, ...) que permeten fer una diagnosi ràpida. Per fer-la, s'ha de mantenir qualsevol botó del panell frontal, excepte <i>View</i>, durant més de 5 segons quan s'engega la unitat. L'aparell emetrà un <i>bip</i> i començarà el test. Si la rutina no troba cap error veurem un missatge a la pantalla que dirà <i>PASS</i>, en canvi, si hi ha un error veurem un número a la pantalla que, amb l'ajut del manual d'usuari, ens dirà quin és el problema.<br>
A les dues unitats el resultat del <i>Self Test</i> va ser <i>PASS</i>.<br>

<b>7-</b> Al manual d'usuari, a part del <i>Self Test</i>, també hi ha un conjunt de comprovacions recomanades per trobar el problema sota el títol <i>Bias Supplies Problems</i>.
<table cellspacing="0" border="0">
 <thead>
    <tr bgcolor="gray">
      <th colspan="4"><font color="white">BIAS supplies Voltages</font></th>
    </tr>
    <tr bgcolor="gray">
      <th><font color="white">Bias Supply</font></th>
      <th><font color="white">Mínim</font></th>
      <th><font color="white">Màxim</font></th>
      <th><font color="white">Mira-ho a:</font></th>
    </tr>
 </thead>
<tbody>

<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">+5V Floating</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">+4,75V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">+5,25V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">U110 pin 2</td>
</tr>
<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">-5,1V Floating</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">-4,75V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">-5,25V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">CR114 Ànode</td>
</tr>
<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">+15V Floating</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">+14,25V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">+15,75V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">CR104 Ànode</td>
</tr>
<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">-15V Floating</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">-14,25V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">-15,75V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">CR105 Càtode</td>
</tr>
</tbody>
</table>

<center>
<img style="display:inline" src="/images/161012-E3644A/20160922_230429.jpg" width="40%" alt="Contingut: E3644A PCB U110. Source: Momex.cat" title="E3644A PCB U110">
<img style="display:inline" src="/images/161012-E3644A/bias.jpg" width="25%" alt="Contingut: E3644A PCB CR104 CR105. Source: Momex.cat" title="E3644A PCB CR104 CR105">
<img style="display:inline" src="/images/161012-E3644A/bias2.jpg" width="28%" alt="Contingut: E3644A PCB CR114. Source: Momex.cat" title="E3644A PCB CR114">
</center>

El resultat és que les dues fonts estan dins d'especificació.<br>

Fins aquí la part fàcil, 7 passos bàsics per trobar de manera ràpida algun problema a les fonts d'alimentació. A partir d'ara, només tindrem un pdf anomenat <i>Component Localization</i> que ens permetrar anar marcant els components que anem investigant.<br>

Multímetre en mà, aquests són els components que vaig seguir fins trobar indicis del problema a les dues fonts d'alimentació.<br>

<i>C503, C504 18000 uF CAPS<br>
CR101 DF045 Bridge Rectifier<br>
CR100, CR102, CR110, CR111,CR115, CR116, CR117, CR118, CR119 A7 BAV99<br> 
CR106, CR126 Z43 Diode <br>
CR109, CR112, CR113, CR124, CR125, CR402, CR403  A6 FAIRCHILD BAS16 Small Signal Diode<br>
CR401, CR404, CR405, CR406, CR407, CR408, CR120, CR122, CR123 Diode<br>
CR500 U1615 Switch Mode Power Rectifier<br>
CR501,CR502,CR504 MCR264 Silicon Controlled Rectifier<br>
CR503 GBU8J Single Phase Bridge Rectifier<br>
Q101 IRF9530 Power Mosfet P-Channel<br>
Q102, Q103 1P J NPN<br>
Q400 IRF2807 Power Mosfet N-Channel<br>
Q401, Q402 2N3904 NPN Transistor<br>
Q500 IRF540 Power Mosfet N-Channel<br>
R510, R511 Shunt Resistors 0,3 Ohm<br>
U105 7805CT Positive Voltage Regulator<br>
U111 AC74 Dual D-Type Positive Edge-Triggered Flip-Flop<br>
U114 LM317T Positive Adjustable Voltage Regulator<br>
U116 LM337T Negative Adjustable Voltage Regulator<br>
U121 N80C196KB16 uController C-MOS 16bit 16MHz 32Kbytes ROM<br>
U125 D432568GU-702 RAM 8-bit<br>
U130 SCX6206AKO IC-ASIC GT-ARY 600 GATES CMOS SCX6200<br>
U132, U139, U140 QTC MOC3020 Optocouplers, Optoisolators<br>
U136 TL074C JFET OPAMP<br>
U142 7905CT Negative Voltage Regulator<br>
U400 LINFINITY SG3525ADW<br>
U402 LM340 Positive Voltage Regulator<br>
U403 7912CT Negative Voltage Regulator <br>
VR400 TL431C Precision programable reference<br></i>

Un cop comprovat que no era un problema dels reguladors de voltatge o dels components tipus díodes, transistors, condensadors,... es va veure que els valors llegits als següents <i>opamps</i> (Amplificadors Operacionals) no eren correctes. <br><br>
<b>U134, U129, U122 AD706 DUAL PICOAMPERE INPUT CURR BIP OPAMP</b><br>
<center>
<img style="display:inline" src="/images/161012-E3644A/opamp.jpg" width="40%" alt="Contingut: AD706 Amplificador Operacional - opamp. Source: Momex.cat" title="E3644A PCB AD706">
<img style="display:inline" src="/images/161012-E3644A/opamp2.jpg" width="30%" alt="Contingut: E3644A PCB U134 U129 U122. Source: Momex.cat" title="E3644A PCB U134 U129 U122">
</center>

<table>
 <thead>
    <tr bgcolor="gray">
      <th colspan="7"><font color="white">OPAMP PIN Check (Voltage reference in U110 pin3)</font></th>
    </tr>
    <tr bgcolor="gray">
      <th rowspan="2"><font color="white">Pins</font></th>
      <th><font color="white">PSA</font></th>
      <th><font color="white">PSB</font></th>
      <th><font color="white">PSA</font></th>
      <th><font color="white">PSB</font></th>
      <th><font color="white">PSA</font></th>
      <th><font color="white">PSB</font></th>
    </tr>
    <tr bgcolor="gray">
      <th colspan="2"><font color="white">U134</font></th>
      <th colspan="2"><font color="white">U129</font></th>
      <th colspan="2"><font color="white">U122</font></th>
    </tr>
 </thead>
<tbody>

<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">Ohm 6&7</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">82kOhm</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">82kOhm</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">20kOhm</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">20kOhm</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">50kOhm</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">50kOhm</td>
</tr>

<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">Ohm 2&1</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">460kOhm</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">460kOhm</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">10kOhm</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">10kOhm</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">18,65kOhm</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">18,65kOhm</td>
</tr>

<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">V+ (pin8)</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">14,2V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">14,2V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">14,2V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">15V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">15V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">15V</td>
</tr>

<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">V- (pin4)</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">-15,4V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">-15,4V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">-15,4V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">-15V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">-15V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">-15V</td>
</tr>

<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">V pin 1</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">13,8V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center"><font color="red"><b>-15V</b></font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">10V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">10V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">0V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center"><font color="red"><b>14V</b></font></td>
</tr>

<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">V pin 2-</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">4,2V-4,5V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center"><font color="red"><b>4,3V</b></font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">5V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">5V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">0V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center"><font color="red"><b>1,6V</b></font></td>
</tr>

<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">V pin 3+</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">4,8V-4,9V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center"><font color="red"><b>5,04V</b></font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">5V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">5V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">0V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center"><font color="red"><b>0V</b></font></td>
</tr>

<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">V pin 7</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">0V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">1,6V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center"><font color="red"><b>14V</b></font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center"><font color="red"><b>-10V</b></font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">14V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">3,7V</td>
</tr>

<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">V pin 6-</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">0V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">0V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center"><font color="red"><b>4,3V</b></font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center"><font color="red"><b>0V</b></font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">0,8V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">2,3V</td>
</tr>

<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">V pin 5+</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">0V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">0V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center"><font color="red"><b>0V</b></font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center"><font color="red"><b>0V</b></font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">1,5V</td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="center">3,5V</td>
</tr>

</tbody>
</table>

En teoria, els <i>opamps</i> connectats en "realimentació negativa" haurien de tenir les entrades "-" i "+" al mateix nivell de voltatge. En vermell he marcat tots aquells <i>opamps</i> que tenen una diferència major o igual a 0,7V i una sortida de l'<i>opamp</i> propera als nivells d'alimentació (+15V, -15V).<br>
És a dir, si la teoria no falla, per la PSA hauria de mirar el component U129 i per la PSB hauria de mirar la U134 i U122.<br><br>
<b>PSA</b><br>
Com no ens costa res anar poc a poc, el primer que farem serà resoldar tots els pins del component amb una mica de flux, estany i una estació de soldadura prou bona com per a mantenir la temperatura de la punta mentre s'aplica calor al component.
<center>
<img style="display:inline" src="/images/161012-E3644A/A/20161009_235236_reparat.jpg" width="40%" alt="Contingut: E3644A PCB vista del U129. Source: Momex.cat" title="E3644A PCB U129">
<img style="display:inline" src="/images/161012-E3644A/A/20161009_235356.jpg" width="30%" alt="Contingut: E3644A PCB vista del U129. Source: Momex.cat" title="E3644A PCB U129">
</center>
Un cop resoldat i sense esperances que funcionés, aquí tenim la primera font d'alimentació totalment operativa alimentant el ventilador de 12V a 0.283A :D.<br>
<center>
<img style="display:inline" src="/images/161012-E3644A/A/20161009_235220_reparat.jpg" width="50%" alt="Contingut: E3644A després de resoldar U129. Source: Momex.cat" title="E3644A després de resoldar U129">
</center>

<b>PSB</b><br>
El que no passa mai a la vida segurament no passarà dos cops seguits,no? Repetim l'operació al components U134:<br>
<center>
<img style="display:inline" src="/images/161012-E3644A/B/20161010_005309.jpg" width="30%" alt="Contingut: E3644A PCB vista del U134. Source: Momex.cat" title="E3644A PCB U134">
<img style="display:inline" src="/images/161012-E3644A/B/20161010_003906_After_U134.jpg" width="40%" alt="Contingut: E3644A després de resoldar U134. Source: Momex.cat" title="E3644A després de resoldar U134">
</center>
Sembla que el voltímetre torna a funcionar..ara toca resoldar el component U122:<br>
<center>
<img style="display:inline" src="/images/161012-E3644A/B/20161010_005348.jpg" width="30%" alt="Contingut: E3644A PCB vista del U122. Source: Momex.cat" title="E3644A PCB U122">
<img style="display:inline" src="/images/161012-E3644A/B/20161010_005427.jpg" width="40%" alt="Contingut: E3644A després de resoldar U122. Source: Momex.cat" title="E3644A després de resoldar U122">
</center>

Per increïble que sembli, ja tenim la segona font d'alimentació arreglada en questió de minuts de diferència..això si, ha costat pràcticament una setmana arribar fins aquí.<br><br>

Ara ja podem retirar la nostra font d'alimentació casolana que tant ens ha servit durant aquests anys i instal·lar els nostres tresors al nostre espai de treball.<br>
<center>
<img style="display:inline" src="/images/161012-E3644A/20161010_010909.jpg" width="43%" alt="Contingut: E3644A vs antiga font d'alimentació. Source: Momex.cat" title="E3644A vs antiga font d'alimentació">
<img style="display:inline" src="/images/161012-E3644A/20161010_012918.jpg" width="56%" alt="Contingut: 2x E3644A resultat. Source: Momex.cat" title="2x E3644A resultat àrea de treball">
</center>

