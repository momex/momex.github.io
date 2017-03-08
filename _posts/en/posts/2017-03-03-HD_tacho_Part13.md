---
type: posts
layout: post
lang: en
comments: true
title: Digital Tachometer for Harley Davidson Sportster (Part 13 - Wiring harness and installation)
name: HD-tacho-part13
permalink: en/HD-tacho-part13
category: ENtacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, SAE, harness, moto, installation
---
<p>
<font size="2"> 
<a href="/en/HD-tacho-part1">Part1 </a>/
<a href="/en/HD-tacho-part2"> Part2 </a>/
<a href="/en/HD-tacho-part3"> Part3 </a>/
<a href="/en/HD-tacho-part4"> Part4 </a>/
<a href="/en/HD-tacho-part5"> Part5 </a>/
<a href="/en/HD-tacho-part6"> Part6 </a>/
<a href="/en/HD-tacho-part7"> Part7 </a>/
<a href="/en/HD-tacho-part8"> Part8 </a>/
<a href="/en/HD-tacho-part9"> Part9 </a>/
<a href="/en/HD-tacho-part10"> Part10 </a>/
<a href="/en/HD-tacho-part11"> Part11 </a>/
<a href="/en/HD-tacho-part12"> Part12 </a>/
<b> Part13 </b>/
<a href="/en/HD-tacho-part14"> Part14 </a>/
<a href="/en/HD-tacho-part15"> Part15 </a>
 </font>
</p>
Once we have the PCB, the housing and the bracket, now we "only" need the harness. There are a thousand ways to connect the PCB to the 3 wires that will allow it to operate (12V, Ground and J1850 data bus). We can choose the cheap option (3 wires from the PCB to some part of the harness) or the expensive one (ref# 68811-07 HD harness that comes with the tachometer ref#67182-07).<br>
Let's go first to take a look on the schematic (spedometer side) to understand what do we have there:

<center>
<img src="/images/Part13/servicemanual.png" width="99%" alt="Content: HD Sportster schematic. Source: google" title="HD Sportster, esquemàtic velocímetre">
</center>

As you see, there is a harness that goes from the speedometer through the 39A/B connector to a subharness and from there to the HD main harness through the 20A connector. This connector is located just under the fuel tank, as seen in the following pictures.

<!--more-->
<center>
<img src="/images/Part13/MolexConnectorHD.JPG" width="99%" alt="Content: HD Molex Connector (33482-1210 i 33472-1210). Source: Momex.cat" title="HD Molex Connector">
</center>

The objective is to connect the wires to the bike in a way that it is not altered, this means it can be undone. So, this choice only gives me a solution..to make a subharness that will be connected between the connectors 20A (33482-1210) and 20B (33472-1210) and to leave a new connector in a more accessible area. This will allow me to unplug easily the tachometer without the need of removing the fuel tank.<br>
Next image shows the schematic of what I had in mind, this way I was able to understand how many wires and connectors were needed..

<center>
<img src="/images/Part13/HarnessParts.JPG" width="60%" alt="Content: HD Tachometer Harness schematic. Source: Momex.cat" title="HD Tachometer Harness schematic">
</center>

As you see, 4 subharness will be needed. 2 (AUXILIAR HARNESS i MAIN HARNESS) will be connected to the bike and the other 2 (TEST HARNESS i REPRO HARNESS) will be used when needed in case I want to test or reprogram the PCB. Following sections will detail the pinout of each one of the subharnesses.

### TACHO PCB CONNECTOR
This is the pinout for the PCB DB9 connector. In hindsight, it would have been better to use a different type of connector..but, with the housing already printed it was not possible to change (basically I didn't want to spend more time..).
<p>
<img src="/images/Part13/TachoPCB_pinout.JPG" width="40%" alt="Content: Pinout for PCB DB9 connector. Source: Momex.cat" title="Pinout for PCB DB9 connector">
</p>

### MAIN HARNESS
This harness will allow us to bring the 3 needed wires from under the fuel tank to a much accessible part close to the handlebar. Furthermore, there will be an extra connector that with a MAX232 or similar, will allow us to broadcast messages from the J1850 data bus to the computer and to use it as a datalogger.
<p>
<img src="/images/Part13/MainHarness.JPG" width="70%" alt="Content: Harness schematic. Source: Momex.cat" title="Harness schematic">
</p>
Pictures taken during the harness assembly. As you see, a 2A fuse was also included to protect the bike in case an internal shortcircuit.
<center>
<img style="display:inline" src="/images/Part13/1.jpg" width="45%" alt="Content: Harness assembly process. Source: Momex.cat" title="Harness assembly process">
<img style="display:inline" src="/images/Part13/2.jpg" width="45%" alt="Content: Harness assembly process. Source: Momex.cat" title="Harness assembly process">
</center>
The connectors used to connect both harnesses (image below) were in my miscellaneous box.
<img src="/images/Part13/spareconn.jpg" width="45%" alt="Contingut: Connectors. Source: Momex.cat" title="Connectors">

### AUXILIAR HARNESS
This harness will allow us to leave the bike in stock condition. The idea was to create a kind of "man in the middle" harness to be in between 20A/B connectors.
<p>
<img src="/images/Part13/AuxiliarHarness.JPG" width="80%" alt="Content: Pinout connectors Harley 20A (33482-1210) and 20B (33472-1210). Source: Momex.cat" title="Pinout connectors Harley 20A (33482-1210) and 20B (33472-1210)">
</p>

Find below the reference tables for each one of the connectors.
<table cellspacing="0" border="0">
 <thead>
    <tr bgcolor="gray">
      <th colspan="3"><font color="white">Connector MOLEX Female</font></th>
    </tr>
    <tr bgcolor="gray">
      <th><font color="white" size="4">Part</font></th>
      <th><font color="white" size="4">Reference</font></th>
      <th><font color="white" size="4">Comment</font></th>
    </tr>
 </thead>
<tbody>

<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">Housing</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">33472-1201</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">MX150™ Sealed Female Connector, Dual Row, 12 Circuits, Polarization A, without Connector Position Assurance, Black</font></td>
</tr>
<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">Terminals</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">33012-2002</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">MX150™ Female Terminal Sealed, Tin Plating, 18 and 20 AWG, Right Reel Payoff</font></td>
</tr>
<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">Empty Terminal</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">34345-0001</font></td>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">MLX 150 Cavity Plug Sealed. És un pin de plàstic usat per sellejar el connector en cas de que no hi hagi terminal.</font></td>
</tr>
</tbody>
</table>

<table cellspacing="0" border="0">
 <thead>
    <tr bgcolor="gray">
      <th colspan="3"><font color="white">Connector MOLEX Male</font></th>
    </tr>
    <tr bgcolor="gray">
      <th><font color="white" size="4">Part</font></th>
      <th><font color="white" size="4">Reference</font></th>
      <th><font color="white" size="4">Comment</font></th>
    </tr>
 </thead>
<tbody>
<font size="4">
<tr>
  <td style="border-top: 1px solid #000000; border-bottom: 1px solid #000000; border-left: 1px solid #000000; border-right: 1px solid #000000" align="left"><font size="3">Housing</font></td>
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

Find some images during the connectors assembly:
<center>
<img style="display:inline" src="/images/Part13/3.jpg" width="45%" alt="Content: Harness assembly process. Source: Momex.cat" title="Harness assembly process">
<img style="display:inline" src="/images/Part13/4.jpg" width="45%" alt="Content: Harness assembly process. Source: Momex.cat" title="Harness assembly process">
</center>

<center>
<img style="display:inline" src="/images/Part13/5.jpg" width="45%" alt="Content: Harness assembly process. Source: Momex.cat" title="Harness assembly process">
<img style="display:inline" src="/images/Part13/6.jpg" width="45%" alt="Content: Harness assembly process. Source: Momex.cat" title="Harness assembly process">
</center>

Watch this youtube video in order to learn how to assembly and disassembly Molex connectors.
<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/ZxrChXXkxo4" frameborder="0" allowfullscreen></iframe>
</center>

### TEST HARNESS
This harness was very useful during the code development phase. It allowed me to test new code improvements very easily. It is basically a connector that goes directly to the DLC(Data Link Connector) and another that goes to the PCB.
<p>
<img src="/images/Part13/TestHarness.JPG" width="40%" alt="Content: Test harness pinout. Source: Momex.cat" title="Test harness pinout">
</p>

### REPRO HARNESS
As before, this harness allowed me to connect the PCB directly to the pickit in order to reprogram new code.
<p>
<img src="/images/Part13/ReproHarness.JPG" width="40%" alt="Content: Repro harness pinout. Source: Momex.cat" title="Repro harness pinout">
</p>

<p>
<font size="2"> 
Project index:<br>
<a href="/en/HD-tacho-part1">Part1 </a>/
<a href="/en/HD-tacho-part2"> Part2 </a>/
<a href="/en/HD-tacho-part3"> Part3 </a>/
<a href="/en/HD-tacho-part4"> Part4 </a>/
<a href="/en/HD-tacho-part5"> Part5 </a>/
<a href="/en/HD-tacho-part6"> Part6 </a>/
<a href="/en/HD-tacho-part7"> Part7 </a>/
<a href="/en/HD-tacho-part8"> Part8 </a>/
<a href="/en/HD-tacho-part9"> Part9 </a>/
<a href="/en/HD-tacho-part10"> Part10 </a>/
<a href="/en/HD-tacho-part11"> Part11 </a>/
<a href="/en/HD-tacho-part12"> Part12 </a>/
<b> Part13 </b>/
<a href="/en/HD-tacho-part14"> Part14 </a>/
<a href="/en/HD-tacho-part15"> Part15 </a>
 </font>
</p>
