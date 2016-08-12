---
type: posts
layout: post
lang: ca
comments: true
title: Tacòmetre Digital per a Harley Davidson Sportster (Part 12 - Disseny de la carcassa i suports)
name: HD-tacho-part12
permalink: HD-tacho-part12
category: tacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, SAE, FreeCAD, carcassa, suports
---

Llistat d'elements que formaran la carcassa i suport del tacòmetre i velocímetre:

<b>1-Suport pels dos rellotges</b> (ref#: 67338-97) (vist a la <a href="/HD-tacho-part5">Part5</a>)
<center>
<img style="display:inline" src="/images/Part12/bracket.jpg" width="30%" alt="Contingut: HD bracket 67338-97. Source: eBay" title="HD bracket 67338-97">
<img style="display:inline" src="/images/Part12/bracket2.jpg" width="30%" alt="Contingut: HD bracket 67338-97. Source: eBay" title="HD bracket 67338-97">
<img style="display:inline" src="/images/Part12/bracket3.jpg" width="35%" alt="Contingut: HD bracket 67338-97. Source: Momex.cat" title="HD bracket 67338-97">
</center>

<font size="3"><b>Nota:</b> És important considerar el centrador (les dues banyes) que el suport té a la part inferior i que serveixen per evitar que la carcassa roti un cop instal·lada. La carcassa que escollim haurà de ser compatible amb aquests centradors.</font><br>

<b>2-Tapa i vidre d'un velocímetre analògic</b>: 
Per evitar problemes d'entrada d'aigua, aprofitaré la tapa de vidre d'un velocímetre analògic antic que vaig comprar de 2ona mà per inspirar-me.
<center>
<img style="display:inline" src="/images/Part12/tapa.jpg" width="35%" alt="Contingut: Tapa d'un velocímetre analògic. Source: Momex.cat" title="Tapa d'un velocímetre analògic">
</center>

<b>3-Carcassa impresa en 3D</b>:<br>
El següent disseny ha estat fet mitjançant el programa FreeCAD v0.15. Segons la wiquipedia, FreeCAD és un modelador de CAD 3D paramètric. És programari lliure (llicència GPL i LGPL) i orientat a l'enginyeria mecànica, el disseny industrial i l'arquitectura. Està disponible per a Ubuntu amb la comanda:
{% highlight bash %}
sudo apt-get install freecad
{% endhighlight %}

Tot i no poder comparar-lo amb altres programes de CAD professional, FreeCAD ofereix els recursos suficients per poder dissenyar figures complexes. La carcassa, com veureu, és bastant simple i per ser el meu primer disseny per ser imprès en 3D, va donar molt bon resultat. He dividit el disseny en 5 pasos:<br>

<b>3.1- Part exterior</b>: Al <i>workbench "Part Design"</i> crearem un <i>sketch</i> al pla X-Z i dibuixarem la forma de la figura inferior amb les cotes respectives. Posteriorment, amb l'opció <i>revolve</i>podrem fer una revolució i ja tindrem la base de la carcassa.
<center>
<img style="display:inline" src="/images/Part12/step1.png" width="45%" alt="Contingut: Creació del model 3D d'una carcassa per un tacòmetre. Source: Momex.cat" title="Step1">
<img style="display:inline" src="/images/Part12/step2.png" width="45%" alt="Contingut: Creació del model 3D d'una carcassa per un tacòmetre. Source: Momex.cat" title="Step2">
</center>
<!--more-->

<b>3.2- Base pels cargols</b>: Per subjectar la carcassa al suport l'haurem de collar a una tapa posterior. Per això a la base de la carcassa farem uns reforços. Fem un <i>sketch</i> a la cara superior de la base amb 4 circumferències i realitzem una extrusió de 6mm en l'eix +Z.
<center>
<img style="display:inline" src="/images/Part12/step3.png" width="45%" alt="Contingut: Creació del model 3D d'una carcassa per un tacòmetre. Source: Momex.cat" title="Step3">
<img style="display:inline" src="/images/Part12/step4.png" width="45%" alt="Contingut: Creació del model 3D d'una carcassa per un tacòmetre. Source: Momex.cat" title="Step4">
</center>

<b>3.3- Orifici del botó</b>: Igual que abans, fem un <i>sketch</i> a la cara superior de la base amb una circumferènia i després realitzem la operació <i>pocket</i> per crear el forat (-Z).
<center>
<img style="display:inline" src="/images/Part12/step5.png" width="45%" alt="Contingut: Creació del model 3D d'una carcassa per un tacòmetre. Source: Momex.cat" title="Step5">
<img style="display:inline" src="/images/Part12/step6.png" width="45%" alt="Contingut: Creació del model 3D d'una carcassa per un tacòmetre. Source: Momex.cat" title="Step6">
</center>

<b>3.4- Orificis dels cables i el centrador</b>: Tal i com deiem al principi, el suport té un centrador a la part inferior que serveix per posicionar la carcassa al suport. Haurem de fer un orifici perque la carcassa que dissenyem s'assenti bé i aprofitarem l'orifici per extreure els cables de la <i>PCB</i> cap a l'exterior. Aquest cop, fem un <i>sketch</i> a la cara inferior de la base de la carcassa i després fem un pocket cap a dalt (+Z).
<center>
<img style="display:inline" src="/images/Part12/step7.png" width="45%" alt="Contingut: Creació del model 3D d'una carcassa per un tacòmetre. Source: Momex.cat" title="Step7">
<img style="display:inline" src="/images/Part12/step8.png" width="45%" alt="Contingut: Creació del model 3D d'una carcassa per un tacòmetre. Source: Momex.cat" title="Step8">
</center>

<b>3.5- Base de la <i>PCB</i></b>: Per posicionar la <i>PCB</i> dins de la carcassa crearem unes pestanyes als laterals. Per fer això farem un <i>sketch</i> a un pla a una distancia del pla X-Y de 15 i 27 mm. Després extrudirem 3mm en direcció +Z als dos <i>sketchs</i>.
<center>
<img style="display:inline" src="/images/Part12/step9.png" width="45%" alt="Contingut: Creació del model 3D d'una carcassa per un tacòmetre. Source: Momex.cat" title="Step9">
<img style="display:inline" src="/images/Part12/step10.png" width="45%" alt="Contingut: Creació del model 3D d'una carcassa per un tacòmetre. Source: Momex.cat" title="Step10">
</center>

<b>3.6- Fitxer <i>STL</i></b>: Aquest és el fitxer que haurem d'aportar al programa d'impressió 3D per procedir amb la impressió. Així doncs, un cop tenim la figura desitjada, ara hem d'unir totes les parts extrudides. Anirem al <i>workbench "Part"</i>, a la barra d'eines altre cop anem a <i>Part > Boolean > Union</i>. Amb això ja tindrem la peça feta. Finalment, només farà falta exportar-la com a .STL clicant <i>File > Export</i> i sel·leccionar l'extensió <i>Mesh Formats (.stl)</i>.
<center>
<img style="display:inline" src="/images/Part12/step11.png" width="45%" alt="Contingut: Creació del model 3D d'una carcassa per un tacòmetre. Source: Momex.cat" title="Step11">
<img style="display:inline" src="/images/Part12/step12.png" width="45%" alt="Contingut: Creació del model 3D d'una carcassa per un tacòmetre. Source: Momex.cat" title="Step12">
</center>

<table>
<thead>
<tr bgcolor="#F8E0E0">
<th><a href="/images/Part12/housing_FreeCAD.fcstd"> Fitxer FreeCAD v0.15</a><br>
<a href="/images/Part12/vN.stl"> Fitxer STL per 3D print </a> <br>
</th>
</tr>
</thead>
</table>


<b>I per què no utilitzar una carcassa d'un velocímetre ja existent?</b><br>
Per 2 motius:<br>
1- Dimensions generals de la carcassa i dificultat per fixar la PCB i altres components.<br>
2- Perquè volia probar això de la impressió 3D :D<br>

<center>
<img style="display:inline" src="/images/Part12/hous1.jpg" width="25%" alt="Contingut: carcassa d'un velocímetre analògic. Source: Momex.cat" title="carcassa d'un velocímetre analògic">
<img style="display:inline" src="/images/Part12/hous2.jpg" width="30%" alt="Contingut: carcassa d'un velocímetre analògic. Source: Momex.cat" title="carcassa d'un velocímetre analògic">
</center>

## Resultat
I finalment, aquí teniu unes imatges amb els resultats. 

<center>
<img style="display:inline" src="/images/Part12/3dprint1.jpg" width="25%" alt="Contingut: Impressió 3D. Source: Momex.cat" title="Impressió 3D">
<img style="display:inline" src="/images/Part12/3dprint2.jpg" width="31%" alt="Contingut: Cargols instal·lats a la carcassa. Source: Momex.cat" title="Cargols instal·lats a la carcassa">
<img style="display:inline" src="/images/Part12/3dprint3.jpg" width="32%" alt="Contingut: Cargols instal·lats a la carcassa. Source: Momex.cat" title="Cargols instal·lats a la carcassa">
</center>

<center>
<img style="display:inline" src="/images/Part12/3dprint4.jpg" width="33%" alt="Cablatge instal·lat. Source: Momex.cat" title="Cablatge instal·lat">
<img style="display:inline" src="/images/Part12/3dprint5.jpg" width="28%" alt="Carcassa i PCB. Source: Momex.cat" title="Carcassa i PCB">
<img style="display:inline" src="/images/Part12/3dprint6.jpg" width="24%" alt="Carcassa, PCB i tapa. Source: Momex.cat" title="Carcassa, PCB i tapa">
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
<a href="/HD-tacho-part11"> Part11 </a>/
<b> Part12 </b>/
 Part13 /
 Part14 /
 Part15
 </font>
</p>
