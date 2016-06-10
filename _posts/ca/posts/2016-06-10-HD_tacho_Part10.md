---
type: posts
layout: post
lang: ca
comments: true
title: Tacòmetre Digital per a Harley Davidson Sportster (Part 10 - Evolució dels prototips)
name: HD-tacho-part10
permalink: HD-tacho-part10
category: tacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, SAE, PCB, disseny, prototips, evolució
---

Aprofito aquesta entrada per guanyar una mica de temps i així acabar de retocar el codi. A continuació, mostraré les diferents fases del projecte amb els prototips amb els que vaig anar desenvolupant el codi font del tacòmetre. Com veureu, cadascuna de les plataformes de prototipatge té les seves avantatges i desavantatges.<br>

## <i>Protoboard</i>
Tot aspirant d'apendre electrònica ha de tenir com a mínim una <i>protoboard</i> al calaix per fer provatures de circuits ràpidament. En el meu cas, va ser així com va començar aquest projecte, encenent un <i>LED</i> amb un <i>PIC</i>, multiplexant una matriu de <i>LED</i>s, creant un bus de dades, interrupcions, etc etc etc. <br>
<b>Avantatges</b>: Disponibilitat immediata per a provar nous circuits.<br>
<b>Desavantatges</b>: Problemes de connexionat (intermitències, desconnexions involuntàries, curtcircuits,..) que et poden fer perdre dies fins entendre si hi ha un cable que fa mal contacte o és que hi ha una errada al codi. No recomanat per a circuits complexes.<br>

<u><b>Imatges</b></u>
<center><img style="display:inline" src="/images/Part10/PB1.jpg" width="18%" alt="Contingut: Protoboard inicial. Source: Xavier Morales">
<img style="display:inline" src="/images/Part10/PB2.jpg" width="39%" alt="Contingut: Protoboard amb font d'alimentació i oscil·loscopi. Source: Xavier Morales">
<img style="display:inline" src="/images/Part10/PB3.jpg" width="40%" alt="Contingut: Embolic de cables a la protoboard. Source: Xavier Morales">
</center>

<!--more-->
## Placa Foradada
No havent aprés la lliçó vaig passar a les plaques foradades. El circuit era bastant complex, així que farien falta un parell de plaques com a mínim per incloure tots els components. Aquestes plaques també val la pena tenir-les pel calaix, però només per a projectes petits. Val a dir que no s'ha d'utilitzar un cable molt gruixut o es pot correr el risc d'acabar tenint un conjunt placa + cablejat massa gruixut. El cable perfecte és l'anomenat <i>wrap wire</i>, un cable molt finet que permetrà treballar amb molta més facilitat. <br>
<b>Avantatges</b>: Et permeten tenir plaques d'electrònica funcionals en poc temps.<br>
<b>Desavantatges</b>: Com abans, si el sistema és complex, pots tenir problemes de connexionat que et poden fer perdre dies fins entendre l'origen. No recomanat per a circuits complexes.<br>

<u><b>Imatges</b></u>
<center><img style="display:inline" src="/images/Part10/PF2.jpg" width="18%" alt="Contingut: Visió frontal. Source: Xavier Morales">
<img style="display:inline" src="/images/Part10/PF3.jpg" width="39%" alt="Contingut: Visió posterior amb cables massa gruixuts. Source: Xavier Morales">
<img style="display:inline" src="/images/Part10/PF4.jpg" width="40%" alt="Contingut: Funcionament. Source: Xavier Morales">
</center>

## PCB
Aquest és l'últim pas per a tot aficionat a l'electrònica que vol portar els seus projectes a un <i>next step</i>. Sens dubte, aquesta és l'opció que ens portarà més temps d'aconseguir i el que suposarà una mica més de dedicació a l'hora de fer tot el disseny en CAD. A canvi, ens donarà uns resultats increïbles i si no és que hi ha alguna errada al <i>layout</i> o a l'hora de soldar components, serà molt fàcil treballar-hi i fer actualitzacions de software al projecte. <br>
<b>Avantatges</b>: Qualitat infinita. Facilitat per treballar i fer modificacions de software. Espai ocupat més reduït.<br>
<b>Desavantatges</b>: la quantitat de temps per tenir la placa acabada serà més llarg, encara que hi haurà alguna persona capaç de fer <i>PCB</i>s com xurros que estarà en contra d'aquesta afirmació.<br>

<u><b>Imatges</b></u>
<center><img style="display:inline" src="/images/Part10/PCB1.jpg" width="13%" alt="Contingut: PCB abans de soldar. Source: Xavier Morales">
<img style="display:inline" src="/images/Part10/PCB2.jpg" width="27%" alt="Contingut: PCB amb tots els elements soldats. Source: Xavier Morales">
<img style="display:inline" src="/images/Part10/PCB3.jpg" width="27%" alt="Contingut: Part posterior de la PCB. Source: Xavier Morales">
<img style="display:inline" src="/images/Part10/PCB4.jpg" width="30%" alt="Contingut: Tacòmetre funcionant. Source: Xavier Morales">
</center>

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
 Part11 /
 Part12 /
 Part13 /
 Part14 /
 Part15
 </font>
</p>
