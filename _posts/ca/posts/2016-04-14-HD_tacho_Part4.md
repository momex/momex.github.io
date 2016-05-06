---
type: posts
layout: post
lang: ca
comments: true
title: Tacòmetre Digital per a Harley Davidson Sportster (Part 4 - Missatges al bus)
name: HD-tacho-part4
permalink: HD-tacho-part4
category: tacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, missatges, ID, capçalera
---

### Missatges i capçaleres:
Les següents taules recullen els missatges que circulen pel bus J1850 VPW d'una Sportster Iron (XL883N) de l'any 2011 per a cadascuna de les ECUs presents (Motor, Display i Body Controller). La informació l'he obtinguda de:<br>
- SAE J2178-4.<br>
- Assajos propis amb datalogger.<br>
- Projecte <a href="https://github.com/stelian42/HarleyDroid">stelian42/HarleyDroid</a>.<br>
- Projecte <a href=" https://github.com/matsekberg/j1850decoder">matsekberg/j1850decoder</a>.<br>
<font size="3">Nota1: Els Missatges amb ??? són no identificats.<br>
Nota2: l'últim byte dels missatges sempre serà el CRC (no l'he representat a les taules).</font>
<br>

<font size="2.5">
<table>
  <thead>
    <tr bgcolor="gray">
      <th rowspan="2"><font color="white">ECU</font></th>
      <th rowspan="2"><font color="white">Informació</font></th>
      <th rowspan="2"><font color="white">R/S</font></th>
      <th colspan="6"><font color="white">byte#</font></th>
      <th rowspan="2"><font color="white">Fórmula</font></th>
    </tr>
    <tr bgcolor="gray">
      <th><font color="white">#0</font></th>
      <th><font color="white">#1</font></th>
      <th><font color="white">#2</font></th>
      <th><font color="white">#3</font></th>
      <th><font color="white">#4</font></th>
      <th><font color="white">#5</font></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="19">M<br>O<BR>T<BR>O<BR>R</td>
      <td title="28 1B 10 02 XX YY">RPM</td>
      <td>S</td>
      <td>28</td>
      <td>1B</td>
      <td>10</td>
      <td>02</td>
      <td>XX</td>
      <td>YY</td>
      <td>rpm = (hex2dec(xx)*256+hex2dec(yy)) / 4</td>
    </tr>
    <tr>
      <td title="48 29 10 02 XX YY">Velocitat</td>
      <td>S</td>
      <td>48</td>
      <td>29</td>
      <td>10</td>
      <td>02</td>
      <td>XX</td>
      <td>YY</td>
      <td>kph= (hex2dec(xx)*256+hex2dec(yy)) / 128</td>
    </tr>
    <tr>
      <td rowspan="2" title="68 88 10 03">MIL</td>
      <td rowspan="2">S</td>
      <td rowspan="2">68</td>
      <td rowspan="2">88</td>
      <td rowspan="2">10</td>
      <td>03</td>
      <td>-</td>
      <td>-</td>
      <td>Indicador de fallada Actiu</td>
    </tr>
    <tr>
      <td title="68 88 10 83">83</td>
      <td>-</td>
      <td>-</td>
      <td>Indicador de fallada inactiu</td>
    </tr>
    <tr>
      <td title="A8 3B 10 03 XX">Marxa</td>
      <td>S</td>
      <td>A8</td>
      <td>3B</td>
      <td>10</td>
      <td>03</td>
      <td>XX</td>
      <td>-</td>
      <td>0xXX = 0x00, 0x02, 0x04, 0x08, 0x0A, 0x14 <br> (decimal: 0,2,4,8,10,20) per les marxes de 1era-5ena</td>
    </tr>
    <tr>
      <td title="A8 49 10 10 XX">Temp Motor</td>
      <td>S</td>
      <td>A8</td>
      <td>49</td>
      <td>10</td>
      <td>10</td>
      <td>XX</td>
      <td>-</td>
      <td>ºC = hex2dec(XX) - 40</td>
    </tr>
    <tr>
      <td title="A8 69 10 06 XX XX">Comptakm</td>
      <td>S</td>
      <td>A8</td>
      <td>69</td>
      <td>10</td>
      <td>06</td>
      <td>XX</td>
      <td>XX</td>
      <td>Resolució de bit=0,4 metres</td>
    </tr>
    <tr>
      <td title="A8 69 10 86 XX XX">Comptakm2</td>
      <td>S</td>
      <td>A8</td>
      <td>69</td>
      <td>10</td>
      <td>86</td>
      <td>XX</td>
      <td>XX</td>
      <td>Igual que l'anterior <br>Resolució de bit=0,4 metres</td>
    </tr>
    <tr>
      <td title="A8 83 10 0A XX XX">Consum benzina</td>
      <td>S</td>
      <td>A8</td>
      <td>83</td>
      <td>10</td>
      <td>0A</td>
      <td>XX</td>
      <td>XX</td>
      <td>Resolució de bit=0,00005 litres</td>
    </tr>
    <tr>
      <td title="A8 83 10 8A XX XX">Consum benzina 2</td>
      <td>S</td>
      <td>A8</td>
      <td>83</td>
      <td>10</td>
      <td>8A</td>
      <td>XX</td>
      <td>XX</td>
      <td>Igual que l'anterior <br>Resolució de bit=0,00005 litres</td>
    </tr>
    <tr>
      <td title="C8 88 10 0E">Indicador Voltage Baix</td>
      <td>R</td>
      <td>C8</td>
      <td>88</td>
      <td>10</td>
      <td>0E</td>
      <td>-</td>
      <td>-</td>
      <td>Petició a METER.<br>Resposta:C8 88 61</td>
    </tr>
    <tr>
      <td title="8C FE 10 60">#6 ??? - Network Control</td>
      <td>R</td>
      <td>8C</td>
      <td>FE</td>
      <td>10</td>
      <td>60</td>
      <td>-</td>
      <td>-</td>
      <td>ID Secondari (60) desconegut</td>
    </tr>
    <tr>
      <td title="28 FF 10 01 XX">#7 ??? - Network Control</td>
      <td>S</td>
      <td>28</td>
      <td>FF</td>
      <td>10</td>
      <td>01</td>
      <td>XX</td>
      <td>-</td>
      <td>XX:0x07 o 0x06 (Desconegut)</td>
    </tr>
    <tr>
      <td title="68 FF 10 XX">ECU Motor Status - Network Control</td>
      <td>S</td>
      <td>68</td>
      <td>FF</td>
      <td>10</td>
      <td>XX</td>
      <td>-</td>
      <td>-</td>
      <td>XX:0x03 (Node despert) o 0x04 (Node dormit)</td>
    </tr>
    <tr>
      <td title="28 93 10 02 XX">#11 ??? - Vehicle Security</td>
      <td>S</td>
      <td>28</td>
      <td>93</td>
      <td>10</td>
      <td>02</td>
      <td>XX</td>
      <td>-</td>
      <td>XX:0x00 (Desconegut)</td>
    </tr>
    <tr title="">
      <td title="68 93 10 20 XX">#12 ??? - Vehicle Security</td>
      <td>S</td>
      <td>68</td>
      <td>93</td>
      <td>10</td>
      <td>20</td>
      <td>XX</td>
      <td>-</td>
      <td>XX:0x01 (Desconegut)</td>
    </tr>
    <tr>
      <td title="68 63 10 26 XX">#13 ??? - Vehicle Speed Control</td>
      <td>S</td>
      <td>68</td>
      <td>63</td>
      <td>10</td>
      <td>26</td>
      <td>XX</td>
      <td>-</td>
      <td>XX:0x00 i 0x01 (Desconegut)</td>
    </tr>
    <tr>
      <td title="68 32 10 XX">Vehicle Speed Control</td>
      <td>R</td>
      <td>68</td>
      <td>62</td>
      <td>10</td>
      <td>XX</td>
      <td>-</td>
      <td>-</td>
      <td>XX:0x01 (Sistema Control Velocitat ON/OFF)<br> XX:0x21 (Botó ON/OFF actiu)</td>
    </tr>
    <tr>
      <td title="09 63 10 XX">#15 ??? - Vehicle Speed Control</td>
      <td>S</td>
      <td>09</td>
      <td>63</td>
      <td>10</td>
      <td>XX</td>
      <td>-</td>
      <td>-</td>
      <td>XX:0x20 (Desconegut)</td>
    </tr>

  </tbody>
</table>

<!--more-->

<table>
  <thead>
    <tr bgcolor="gray">
      <th rowspan="2"><font color="white">ECU</font></th>
      <th rowspan="2"><font color="white">Informació</font></th>
      <th rowspan="2"><font color="white">R/S</font></th>
      <th colspan="6"><font color="white">byte#</font></th>
      <th rowspan="2"><font color="white">Fórmula</font></th>
    </tr>
    <tr bgcolor="gray">
      <th><font color="white">#0</font></th>
      <th><font color="white">#1</font></th>
      <th><font color="white">#2</font></th>
      <th><font color="white">#3</font></th>
      <th><font color="white">#4</font></th>
      <th><font color="white">#5</font></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="7">D<br>I<BR>S<BR>P<BR>L<BR>A<BR>Y</td>
      <td title="A8 83 61 12 0X">Nivell Benzina</td>
      <td>S</td>
      <td>A8</td>
      <td>83</td>
      <td>61</td>
      <td>12</td>
      <td>0X</td>
      <td>-</td>
      <td>X:0-F (0 a 15 ratlles)</td>
    </tr>
    <tr>
      <td title="29 FE 61 01">#1 ??? - Network Control</td>
      <td>R</td>
      <td>29</td>
      <td>FE</td>
      <td>61</td>
      <td>01</td>
      <td>-</td>
      <td>-</td>
      <td>ID Secondari (01) desconegut</td>
    </tr>
    <tr>
      <td title="68 93 61 XX YY ZZ">#5 ??? - Vehicle Security</td>
      <td>S</td>
      <td>68</td>
      <td>93</td>
      <td>61</td>
      <td>XX</td>
      <td>YY</td>
      <td>ZZ</td>
      <td>XX,YY,ZZ Desconeguts</td>
    </tr>
    <tr>
      <td title="69 93 61 XX">#16 ??? - Vehicle Security</td>
      <td>S</td>
      <td>69</td>
      <td>93</td>
      <td>61</td>
      <td>XX</td>
      <td>-</td>
      <td>-</td>
      <td>XX:0x2A (Desconegut)</td>
    </tr>
    <tr>
      <td title="68 FF 61 XX">Display - Network Control</td>
      <td>S</td>
      <td>68</td>
      <td>FF</td>
      <td>61</td>
      <td>XX</td>
      <td>-</td>
      <td>-</td>
      <td>XX:0x03 (Node despert) o 0x04 (Node dormit)</td>
    </tr>
    <tr>
      <td title="C8 89 61 0E XX">Indicador Voltage Baix</td>
      <td>S</td>
      <td>C8</td>
      <td>89</td>
      <td>61</td>
      <td>0E</td>
      <td>XX</td>
      <td>-</td>
      <td>Resposta a ECM.<br>XX:0x03 (Ind.OFF) o 0x83 (Ind.ON)<br>Llum ON si (0xXX & 0x80)&#8800;0</td>
    </tr>
    <tr>
      <td title="E8 89 61 0E">Indicador Voltage Baix</td>
      <td>S</td>
      <td>E8</td>
      <td>89</td>
      <td>61</td>
      <td>0E</td>
      <td>-</td>
      <td>-</td>
      <td>Desconec el motiu pel qual s'envia aquest missatge.</td>
    </tr>

  </tbody>
</table>

<table>
  <thead>
    <tr bgcolor="gray">
      <th rowspan="2"><font color="white">ECU</font></th>
      <th rowspan="2"><font color="white">Informació</font></th>
      <th rowspan="2"><font color="white">R/S</font></th>
      <th colspan="6"><font color="white">byte#</font></th>
      <th rowspan="2"><font color="white">Fórmula</font></th>
    </tr>
    <tr bgcolor="gray">
      <th><font color="white">#0</font></th>
      <th><font color="white">#1</font></th>
      <th><font color="white">#2</font></th>
      <th><font color="white">#3</font></th>
      <th><font color="white">#4</font></th>
      <th><font color="white">#5</font></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="6">B<br>O<BR>D<BR>Y<BR> <BR>C<BR>O<BR>N<BR>T</td>
      <td title="48 3B 40 XX">Clutch & Neutral</td>
      <td>S</td>
      <td>48</td>
      <td>3B</td>
      <td>40</td>
      <td>XX</td>
      <td>-</td>
      <td>-</td>
      <td>Neutral si (0xXX & 0x20)&#8800;0<br>Clutch open si (0xXX & 0x80)&#8800;0</td>
    </tr>
    <tr>
      <td title="48 DA 40 39 XX">Intermitents</td>
      <td>R</td>
      <td>48</td>
      <td>DA</td>
      <td>40</td>
      <td>39</td>
      <td>XX</td>
      <td>-</td>
      <td>ID Secondari 39-Intermitents<br>turn signals, 0xXX = 01,02,03 per esq/dreta/els dos </td>
    </tr>
    <tr>
      <td title="29 FE 40 01">#2 ??? - Network Control</td>
      <td>R</td>
      <td>29</td>
      <td>FE</td>
      <td>40</td>
      <td>01</td>
      <td>-</td>
      <td>-</td>
      <td>ID Secondari (01) desconegut</td>
    </tr>
    <tr>
      <td title="68 FF 40 XX">Body Cont - Network Control</td>
      <td>S</td>
      <td>68</td>
      <td>FF</td>
      <td>40</td>
      <td>XX</td>
      <td>-</td>
      <td>-</td>
      <td>XX:0x03 (Node despert) o 0x04 (Node dormit)</td>
    </tr>
    <tr>
      <td title="48 92 40 XX YY">Indicador Voltage Baix</td>
      <td>R</td>
      <td>48</td>
      <td>92</td>
      <td>40</td>
      <td>XX</td>
      <td>YY</td>
      <td>ZZ</td>
      <td>XX,YY,ZZ Desconeguts</td>
    </tr>
    <tr>
      <td title="08 62 40 XX">#8 ??? - Vehicle Speed Control</td>
      <td>R</td>
      <td>08</td>
      <td>62</td>
      <td>40</td>
      <td>XX</td>
      <td>-</td>
      <td>-</td>
      <td>XX:0x20 (Desconegut)</td>
    </tr>

  </tbody>
</table>

</font>

<p>
<font size="2"> 
Índex de projecte:<br>
<a href="/HD-tacho-part1">Part1 </a>/
<a href="/HD-tacho-part2"> Part2 </a>/
<a href="/HD-tacho-part3"> Part3 </a>/
<a href="/HD-tacho-part4"> Part4 </a>/
<a href="/HD-tacho-part5"> Part5 </a>/
<a href="/HD-tacho-part6"> Part6 </a>/
 Part7 /
 Part8 /
 Part9 /
 Part10 /
 Part11 /
 Part12 /
 Part13
 </font>
</p>

