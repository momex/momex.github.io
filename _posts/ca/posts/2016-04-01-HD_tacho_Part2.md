---
type: posts
layout: post
lang: ca
comments: true
title: Tacòmetre Digital per a Harley Davidson Sportster (Part 2 - Bus de dades i sensors)
name: HD-tacho-part2
permalink: HD-tacho-part2
category: tacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, SAE, bus, dades, sensors
---

En aquesta segona part ens centrarem en l'eléctrònica de la moto i en saber què podem i què no podem utilitzar.<br>
Pràcticament tots els vehicles d'avui dia amb un mínim de tecnologia porten un bus de dades que connecta les diferents unitats de control que existeixen. L'avantatge és ben evident, si cadascuna de les unitats de control tingués els seus propis sensors, el vehicle pesaria i costaria molt i hi hauria sensors repetits... Amb un bus de dades, cada unitat de control pot tenir un mínim de sensors associats a ella, compartir la informació mitjançant aquest bus i en cas de què necessiti més informació, pot trobar-la allà.<br>
<!--more-->
Fins al 2014, HD utilitzava un bus de dades d'un sol cable mitjançant el protocol de comunicació en sèrie SAE J1850 VPW (Variable Pulse Width = Pols d'Amplitud Variable) a 10,4 kbit/s. Per entendre els ets i uts d'aquest protocol consulteu el següent <a href="/HD-tacho-part3/"> post </a>. A partir del 2014, totes les HD utilitzen un altre bus de dades anomenat <a href="https://ca.wikipedia.org/wiki/Controller_area_network" target="_blank">bus CAN (Controller Area Network)</a>.
<p>

<table>
  <thead>
    <tr>
      <th>HD model</th>
      <th>Periode</th>

      <th>Bus de dades</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Sportster 883/1200</td>
      <td>2001 - 2013</td>
      <td>1-cable J1850</td>
    </tr>
    <tr>
      <td>Sportster 883/1200</td>
      <td>2014 - avui</td>
      <td>2-cables CAN bus</td>
    </tr>
  </tbody>
</table>

En una HD Sportster (2007-2013) hi trobem les ECUs (Unitats de Control Electrònic) següents: <br>
* ECM (unitat de control de motor) <br>
* Display <br>
* Body Control <br><br>

En aquest projecte ens centrarem bàscicament en la informació enviada per la ECM ja que ens proporcionarà les RPM i la marxa actual. Per accedir al bus J1850 VPW utilitzarem el connector (Data Link Connector) que hi ha sota la tapa de la bateria (lateral posterior esquerre).<p>

<center><img src="/images/Part2/4pinconnector.png"  alt="Contingut: HD Data Link Connector. Source: Xavier Morales"></center>

El pins són: <br>
1- <br>
2- Massa<br>
3- Bus J1850 VPW<br>
4- IGN (+12V quan el contacte està donat, independent del botó de parada d'emergència)<br>
<p>

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
 Part9 /
 Part10 /
 Part11 /
 Part12 /
 Part13 /
 Part14
 </font>
</p>
