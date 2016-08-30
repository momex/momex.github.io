---
type: posts
layout: post
lang: ca
comments: true
title: Tacòmetre Digital per a Harley Davidson Sportster (Part 13 - Cablejat i instal·lació a la moto)
name: HD-tacho-part13
permalink: HD-tacho-part13
category: tacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, SAE, cablejat, moto, instal·lació
---

Un cop tenim la PCB, la carcassa i el suport, ara "només" faltarà el cablejat. Hi ha mil i una maneres de connectar la PCB i els 3 cables necessaris per fer-la funcionar (12V, Massa i bus de dades J1850), passant per l'opció més econòmica (3 cables des de la PCB fins a algun punt de la moto) fins a la més cara (cablejat ref# 68811-07 que ve amb el kit de tacòmetre ref#67182-07).<br>
Anem primer a l'esquemàtic de la moto (referència velocímetre) per veure que hi tenim:

<center>
<img src="/images/Part13/servicemanual.png" width="99%" alt="Contingut: HD Sportster esquemàtic. Source: google" title="HD Sportster, esquemàtic velocímetre">
</center>

Com veiem, hi ha un cablejat que va des del velocímetre a través del connector 39A/B fins al cablejat de l'HD mitjançant el connector 20A. Aquest connector es troba situat just a sota el dipòsit de benzina, tal i com es pot veure a continuació.

<!--more-->
<center>
<img src="/images/Part13/MolexConnectorHD.JPG" width="99%" alt="Contingut: HD Molex Connector (33482-1210 i 33472-1210). Source: Momex.cat" title="HD Molex Connector">
</center>

L'objetiu és connectar els cables d'alguna manera que no alteri la moto si algun dia ho volem desinstal·lar i la idea de punxar els cables ni se'm passa pel cap. Així doncs, decideixo crear un cablejat que vagi connectat entre els connectors 20A (33482-1210) i 20B (33472-1210), això permetrà no haber de desmuntar el dipòsit si algun dia volem portar-nos a casa el tacòmetre per algun motiu.<br>
A la imatge inferior trobareu resumit l'esquemàtic final i quants cablejats i connectors em faran falta.

<center>
<img src="/images/Part13/HarnessParts.JPG" width="60%" alt="Contingut: Esquemàtic del cablejat del Tacòmetre digital. Source: Momex.cat" title="Esquemàtic del cablejat del tacòmetre digital">
</center>

Com veieu, hauré de fer 4 cablejats. 2 (AUXILIAR HARNESS i MAIN HARNESS) aniran connectats a la moto  i els altres 2 (TEST HARNESS i REPRO HARNESS) els utilitzaré en cas que vulgui testejar la PCB o vulgui reprogramar el tacòmetre amb el PICkit. A continuació detallo els terminals de cadascun dels cablejats.

### TACHO PCB CONNECTOR
Aquests són els terminals del connector DB9 de la PCB. A misses dites, potser hauria escollit un altre tipus de connector..però bé, amb la carcassa ja impressa era difícil de canviar.
<p>
<img src="/images/Part13/TachoPCB_pinout.JPG" width="40%" alt="Contingut: Pins del connector DB9 de la PCB. Source: Momex.cat" title="Pins del connector DB9 de la PCB">
</p>

### MAIN HARNESS
Aquest cablejat permetrà extendre els cables fins al connector del cablejat auxiliar a sota el dipòsit. A part, hi ha un connector extra que permetrà, amb ajuda d'un MAX232 o similar, enviar informació del bus de dades a l'ordinador i poder fer quelcom semblant a un datalogger.
<p>
<img src="/images/Part13/MainHarness.JPG" width="70%" alt="Contingut: Esquemàtic del cablejat. Source: Momex.cat" title="Esquemàtic del cablejat">
</p>
Imatges durant el muntatge dels cablejats. Com veieu, també es va afegir un fusible de 2A per protegir la moto davant d'un curtciurcuit.
<center>
<img style="display:inline" src="/images/Part13/1.jpg" width="45%" alt="Contingut: Procés de muntatge del cablejat. Source: Momex.cat" title="Procés muntatge">
<img style="display:inline" src="/images/Part13/2.jpg" width="45%" alt="Contingut: Procés de muntatge del cablejat. Source: Momex.cat" title="Procés muntatge">
</center>
Els connectors utilitzats per connectar els dos cablejats (imatge inferior) els tenia a la caixa dels trastos.
<img src="/images/Part13/spareconn.jpg" width="45%" alt="Contingut: Connectors. Source: Momex.cat" title="Connectors">

### AUXILIAR HARNESS
Aquest cablejat és el que ens permetrà deixar la moto de sèrie. La idea és desconnectar el connector 20A/B i posar un cablejat entremig, utilitzant és clar, els mateixos connectors.
<p>
<img src="/images/Part13/AuxiliarHarness.JPG" width="80%" alt="Contingut: Pinout connectors Harley 20A (33482-1210) i 20B (33472-1210). Source: Momex.cat" title="Pinout connectors Harley 20A (33482-1210) i 20B (33472-1210)">
</p>

A continuació teniu les taules amb les referències de cada part dels connectors.
<table cellspacing="0" border="0">
 <thead>
    <tr bgcolor="gray">
      <th colspan="3"><font color="white">Connector MOLEX Femella</font></th>
    </tr>
    <tr bgcolor="gray">
      <th><font color="white" size="4">Peça</font></th>
      <th><font color="white" size="4">Referència</font></th>
      <th><font color="white" size="4">Comentari</font></th>
    </tr>
 </thead>
<tbody>

<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">Carcassa</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">33472-1201</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">MX150™ Sealed Female Connector, Dual Row, 12 Circuits, Polarization A, without Connector Position Assurance, Black</font></td>
</tr>
<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">Terminals</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">33012-2002</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">MX150™ Female Terminal Sealed, Tin Plating, 18 and 20 AWG, Right Reel Payoff</font></td>
</tr>
<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">Terminal buit</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">34345-0001</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">MLX 150 Cavity Plug Sealed. És un pin de plàstic usat per sellejar el connector en cas de que no hi hagi terminal.</font></td>
</tr>
</tbody>
</table>

<table cellspacing="0" border="0">
 <thead>
    <tr bgcolor="gray">
      <th colspan="3"><font color="white">Connector MOLEX Mascle</font></th>
    </tr>
    <tr bgcolor="gray">
      <th><font color="white" size="4">Peça</font></th>
      <th><font color="white" size="4">Referència</font></th>
      <th><font color="white" size="4">Comentari</font></th>
    </tr>
 </thead>
<tbody>
<font size="4">
<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">Carcassa</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">33482-1201</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">MX150™ Sealed Male Connector, Dual Row, 12 Circuits, Polarization A, without Connector Position Assurance, Black</font></td>
</tr>
<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">Terminals</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">33000-0002</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">MX150™ Male Terminal, Tin Plating, 16, 18 and 20 AWG, Right Reel Payoff</font></td>
</tr>

</font>
</tbody>
</table>

I unes imatges durant el muntatge:
<center>
<img style="display:inline" src="/images/Part13/3.jpg" width="45%" alt="Contingut: Procés de muntatge del cablejat. Source: Momex.cat" title="Procés muntatge">
<img style="display:inline" src="/images/Part13/4.jpg" width="45%" alt="Contingut: Procés de muntatge del cablejat. Source: Momex.cat" title="Procés muntatge">
</center>

<center>
<img style="display:inline" src="/images/Part13/5.jpg" width="45%" alt="Contingut: Procés de muntatge del cablejat. Source: Momex.cat" title="Procés muntatge">
<img style="display:inline" src="/images/Part13/6.jpg" width="45%" alt="Contingut: Procés de muntatge del cablejat. Source: Momex.cat" title="Procés muntatge">
</center>

Us deixo amb un video (en anglès) del Youtube on s'explica com muntar i desmuntar aquest tipus de connectors.
<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/ZxrChXXkxo4" frameborder="0" allowfullscreen></iframe>
</center>

### TEST HARNESS
Aquest cablejat em va ser molt útil durant la fase de desenvolupament del codi, ja que em permetia d'una manera molt fàcil comprobar que el codi funcionava. Consta d'un connector que va directe al connector DLC (Data Link Connector) i l'altre a la PCB.
<p>
<img src="/images/Part13/TestHarness.JPG" width="40%" alt="Contingut: Terminals connectors test harness. Source: Momex.cat" title="Terminals connectors test harness">
</p>

### REPRO HARNESS
Igual que l'anterior, aquest cablejat permet connectar la PCB directament al PICkit per poder reprogramar.
<p>
<img src="/images/Part13/ReproHarness.JPG" width="40%" alt="Contingut: Terminals connectors repro harness. Source: Momex.cat" title="Terminals connectors repro harness">
</p>

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
<a href="/HD-tacho-part10"> Part10 </a>/
<a href="/HD-tacho-part11"> Part11 </a>/
<a href="/HD-tacho-part12"> Part12 </a>/
<b> Part13 </b>/
 Part14 /
 Part15
 </font>
</p>
