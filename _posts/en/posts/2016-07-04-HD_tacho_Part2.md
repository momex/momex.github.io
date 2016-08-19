---
type: posts
layout: post
lang: en
comments: true
title: Digital Tachometer for Harley Davidson Sportster (Part 2 - Communication Bus and sensors)
name: HD-tacho-part2
permalink: en/HD-tacho-part2
category: ENtacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, SAE, bus, dades, sensors
---

In this second part we will focus in the motorcycle electronics and in knowing what we can/cannot use.<br>
Nowadays, all vehicles with a minimum of technology have a communication bus that connects all different control units. The main advantadge is pretty clear, if each control unit had its own sensors, the weight and cost of the vehicle would be higher due to some sensors and harnesses would be redundant. With a communication bus, each control unit can have a mínimum of sensors attached and then broadcast the information through the bus to the other control units and in case it needs other information, find it there.<br>
<!--more-->
Until 2014, HD used to have a 1-wire bus communication based in the SAE J1850 VPW (Variable Pulse Width) at 10,4 kbit/s as communication protocol. In order to understand how this protocol works, please check the following<a href="/en/HD-tacho-part3"> post </a>. Since 2014, all HD use another communication bus called  <a href="https://en.wikipedia.org/wiki/Controller_area_network" target="_blank">CAN bus (Controller Area Network)</a>.
<p>

<table>
  <thead>
    <tr>
      <th>HD model</th>
      <th>Model Year</th>

      <th>Comm bus</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Sportster 883/1200</td>
      <td>2001 - 2013</td>
      <td>1-wire J1850</td>
    </tr>
    <tr>
      <td>Sportster 883/1200</td>
      <td>2014 - current</td>
      <td>2-wires CAN bus</td>
    </tr>
  </tbody>
</table>

In a HD Sportster (2007-2013) we can find the following ECUs (Electronic Control Units): <br>
* ECM (Engine Control Unit) <br>
* Display <br>
* Body Control <br><br>

In this project we will be focus only in the information broadcasted by ECM because it will give us the RPMs and the current gear. In order to access the J1850 VPW bus we will use the DLC (Data Link Connector), located under the battery cover (rear left side).<p>

<center><img src="/images/Part2/4pinconnector.png"  alt="Content: HD Data Link Connector. Source: Xavier Morales"></center>

Pinout of the connector is: <br>
1- <br>
2- GND<br>
3- Bus J1850 VPW<br>
4- IGN (+12V when key ON, not related to emergency switch position)<br>
<p>


<p>
<font size="2"> 
Project Index:<br>
<a href="/en/HD-tacho-part1">Part1 </a>/
<b> Part2 </b>/
<a href="/en/HD-tacho-part3"> Part3 </a>/
<a href="/en/HD-tacho-part4"> Part4 </a>/
<a href="/en/HD-tacho-part5"> Part5 </a>/
<a href="/en/HD-tacho-part6"> Part6 </a>/
 Part7 /
 Part8 /
 Part9 /
 Part10 /
 Part11 /
 Part12 /
 Part13 /
 Part14 /
 Part15
 </font>
</p>
