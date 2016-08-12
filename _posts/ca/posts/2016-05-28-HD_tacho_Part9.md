---
type: posts
layout: post
lang: ca
comments: true
title: Tacòmetre Digital per a Harley Davidson Sportster (Part 9 - Disseny de la PCB)
name: HD-tacho-part9
permalink: HD-tacho-part9
category: tacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, SAE, PCB, disseny, Altium
---

Sense ànim d'ésser un tutorial, en aquesta 9a part mostraré una sèrie de passos que vaig seguir per realitzar el disseny de la <i>PCB</i> (<i>Printed Circuit Board</i> o Placa de Circuit Imprès).<br>

<b>1)</b> Tant per fer l'esquemàtic com per fer la <i>PCB</i>, l'Altium Designer requereix d'unes llibreries on trobar la informació dels components que utilitzarem. Serà necessari tenir una llibreria d'esquemàtics on trobar, per exemple, el número de terminals (<i>pins</i>) i una llibreria de <i>PCB</i> on trobar la petjada o <i>footprint</i>, és a dir, la superfície que ocupa la peça sobre la <i>PCB</i> i la posició dels seus terminals. Si a més a més també volem disposar d'una visió en 3D de la placa, haurem d'incloure els fitxers 3D (format STEP) en aquesta segona llibreria. Les següents figures mostren un parell d'exemples on podem veure d'esquerra a dreta (esquemàtic, llista de pins, petjada o <i>footprint</i> i vista 3D mitjançant fitxers STEP). <br>

<u><b>7 SEGMENTS</b></u>
<center><img style="display:inline" src="/images/Part9/7Seg_sch.PNG" width="24%" alt="Contingut: 7-Segments esquemàtic. Source: Xavier Morales">
<img style="display:inline" src="/images/Part9/7Seg_sch_pins.PNG" width="22%" alt="Contingut: Pinout 7-Segments. Source: Xavier Morales">
<img style="display:inline" src="/images/Part9/7Seg_PCB.PNG" width="18%" alt="Contingut: Petjada (footprint) 7-Segments. Source: Xavier Morales">
<img style="display:inline" src="/images/Part9/7Seg_PCB_3d.PNG" width="22%" alt="Contingut: STEP vista 3D 7-Segments. Source: Xavier Morales"></center>

<u><b>PIC18F2553</b></u>
<center><img style="display:inline" src="/images/Part9/PIC_sch.PNG" width="24%" alt="Contingut: PIC esquemàtic. Source: Xavier Morales">
<img style="display:inline" src="/images/Part9/PIC_sch_pins.PNG" width="11%" alt="Contingut: Pinout PIC. Source: Xavier Morales">
<img style="display:inline" src="/images/Part9/PIC_PCB.PNG" width="19%" alt="Contingut: Petjada (footprint) PIC. Source: Xavier Morales">
<img style="display:inline" src="/images/Part9/PIC_PCB_3d.PNG" width="30%" alt="Contingut: STEP vista 3D PIC. Source: Xavier Morales"></center>

<b>2)</b> Un cop fet l'esquemàtic (<a href="/HD-tacho-part8">part8</a>) podem procedir a volcar tota la informació a la part de disseny de <i>PCB</i>. Allà, hi apareixeran tots els <i>footprints</i> associats als components (CI, resistències, transistors,...) que hem inclòs a l'esquemàtic.<br>

<center><img style="display:inline" src="/images/Part9/volcatPCB.PNG" width="99%" alt="Contingut: Volcat de l'esquemàtic a la PCB, Altium Designer. Source: Xavier Morales"></center>

<!--more-->

<b>3)</b> Abans de començar a posicionar cadascun dels components, també s'haurà de definir el contorn de la <i>PCB</i>. Aquí és important saber qui serà el nostre fabricant de <i>PCB</i>s per tal de poder seguir les seves normes de fabricació (per exemple, màximes dimensions de la <i>PCB</i> o si permeten troquelar i amb quines dimensions). <br>

<center><img style="display:inline" src="/images/Part9/pcbshape.PNG" width="30%" alt="Contingut: PCB, forma i dimensions a Altium Designer. Source: Xavier Morales"></center>


<b>4)</b> Posicionar, i si fes falta, rotar els components sobre l'àrea definida com a <i>PCB</i>. Com es veu a la imatge, el programa indica les connexions entre els terminals. Al principi semblarà un caos, però ja veureu com ens ajudarà després a definir les traces i les vies.

<center><img style="display:inline" src="/images/Part9/pcb_routing2.PNG" width="70%" alt="Contingut: Col·locació dels components dins de la PCB, Altium Designer. Source: Xavier Morales"></center>

<b>5)</b> Hi ha moltes maneres per procedir amb tot el traçat de la <i>PCB</i> i val a dir que tenir dues capes disponibles ajuda molt. Potser la més comú és la de fer totes les traces verticals en una cara i les horitzontals en un altre intentant minimitzar la quantitat de vies d'una cara a un altra. Una de les coses en les que alguns dissenyadors electrònics coincideixen és la d'evitar el traçador automàtic (en anglès, <i>auto routing</i>) que ve en alguns softwares de disseny de PCB (cal destacar aquesta samarreta si hom vol reivindicar aquest argument)

<center><img src="/images/Part9/chrisgamm.jpg" width="40%" alt="Contingut: Samarreta NEVER trust the autorouter. Source: teespring.com"></center>

<b>6)</b> En definitiva, aquí hi teniu el resultat final després d'hores rumiant com connectar tots els terminals i d'intentar mantenir el disseny original.<br>

<b>PART FRONTAL</b>
<center><img style="display:inline" src="/images/Part9/3d front.PNG" width="49%" alt="Contingut: Frontal PCB Harley tacòmetre. Source: Xavier Morales">
<img style="display:inline" src="/images/Part9/3d lateral.PNG" width="49%" alt="Contingut: Perfil PCB Harley tacòmetre. Source: Xavier Morales"></center>

<b>PART POSTERIOR</b>
<center><img style="display:inline" src="/images/Part9/3d back.PNG" width="49%" alt="Contingut: Part posterior PCB Harley tacòmetre. Source: Xavier Morales">
<img style="display:inline" src="/images/Part9/3d back side.PNG" width="49%" alt="Contingut: Perfil Posterior PCB Harley tacòmetre. Source: Xavier Morales"></center>

<b>7)</b> Com a últim punt necessitarem els fitxers en format <a href="https://en.wikipedia.org/wiki/Gerber_format" target="_blank">Gerber</a> per enviar-los al nostre fabricant de <i>PCB</i>s. Un altre cop, és molt important saber quins requeriments i quines capes necessiten per poder fabricar la nostra <i>PCB</i>.

<center><img src="/images/Part9/gerberrules.png" width="70%" alt="Contingut: Normativa del fabricant per produir una PCB mitjançant fitxers Gerber. Source: seeedstudio.com"></center>

Visió del contingut dels fitxers <i>Gerber</i> (part frontal i posterior)

<center><img style="display:inline" src="/images/Part9/gerber top.PNG" width="49%" alt="Contingut: Fitxers Gerber, part frontal PCB Harley tacòmetre. Source: Xavier Morales">
<img style="display:inline" src="/images/Part9/gerber bottom.PNG" width="45%" alt="Contingut: Fitxers Gerber, part posterior PCB Harley tacòmetre. Source: Xavier Morales"></center>


A continuació, descarrega't els fitxers d'Altium Designer i els fitxers <i>Gerber</i> d'aquest projecte:<br>

<table>
<thead>
<tr bgcolor="#F8E0E0">
<th><a href="/images/Part9/J1850_Tacho.SchDoc"> Esquemàtic </a><br>
<a href="/images/Part9/J1850_Tacho.PcbDoc"> <i>PCB</i> </a> <br>
<a href="/images/Part9/J1850_Harley_tacho_gerber files.zip"> Fitxers Gerber</a> <br>
</th>
</tr>
</thead>
</table>


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
 <b>Part9</b>/
<a href="/HD-tacho-part10"> Part10 </a>/
<a href="/HD-tacho-part11"> Part11 </a>/
<a href="/HD-tacho-part12"> Part12 </a>/
 Part13 /
 Part14 /
 Part15
 </font>
</p>
