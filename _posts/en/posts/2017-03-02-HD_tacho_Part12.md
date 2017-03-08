---
type: posts
layout: post
lang: en
comments: true
title: Digital Tachometer for Harley Davidson Sportster (Part 12 - Housing design and brackets)
name: HD-tacho-part12
permalink: en/HD-tacho-part12
category: ENtacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, SAE, FreeCAD, housing, brackets
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
<b> Part12 </b>/
<a href="/en/HD-tacho-part13"> Part13 </a>/
<a href="/en/HD-tacho-part14"> Part14 </a>/
<a href="/en/HD-tacho-part15"> Part15 </a>
 </font>
</p>
Following list will summarize the parts included on the housing and bracket assembly for the speedometer and tachometer:

<b>1-Dual gauge bracket</b> (ref#: 67338-97) (seen on <a href="/en/HD-tacho-part5">Part5</a>)
<center>
<img style="display:inline" src="/images/Part12/bracket.jpg" width="30%" alt="Content: HD bracket 67338-97. Source: eBay" title="HD bracket 67338-97">
<img style="display:inline" src="/images/Part12/bracket2.jpg" width="30%" alt="Content: HD bracket 67338-97. Source: eBay" title="HD bracket 67338-97">
<img style="display:inline" src="/images/Part12/bracket3.jpg" width="35%" alt="Content: HD bracket 67338-97. Source: Momex.cat" title="HD bracket 67338-97">
</center>

<font size="3"><b>Note:</b> It is important to take care of the gauge "rear horns" that are used to center and fix the position of the speedo and tachometer. The housing used for the tachometer will need to have a specific space to fit correctly.</font><br>

<b>2-Gauge cover and glass from an old analog speedometer</b>: 
In order to avoid humidity issues I will reuse the gauge cover from an old analog speedometer bought some time ago to get some ideas for this project.
<center>
<img style="display:inline" src="/images/Part12/tapa.jpg" width="35%" alt="Content: Gauge cover from an old analog speedo. Source: Momex.cat" title="Tapa d'un velocímetre analògic">
</center>

<b>3-3D printed housing</b>:<br>
Following design has been done with FreeCAD v0.15. According wiquipedia, FreeCAD is a parametric CAD 3D design tool. It is opensource (GPL and LGPL license) and focused in mechanical engineering, industrial engineering and architecture. It is available for Ubuntu by typing the following command:
{% highlight bash %}
sudo apt-get install freecad
{% endhighlight %}

It can not be compared with other professional CAD tools, but FreeCAD offers enough resources to allow the design of complex models. The housing, as you will see, is quite simple and as beeing my first 3D printed design I feel quite satisfied. The design can be summarized in 5 steps:<br>

<b>3.1- Exterior part</b>: In <i>workbench "Part Design"</i>, we will create a <i>sketch</i> on the X-Z and will draw the shape of the housing. Afterwards, with the option <i>revolve</i>, we will be able to revolve 360º in order to have the basic housing shape.
<center>
<img style="display:inline" src="/images/Part12/step1.png" width="45%" alt="Content: Creation of the 3D model tachometer housing. Source: Momex.cat" title="Step1">
<img style="display:inline" src="/images/Part12/step2.png" width="45%" alt="Content: Creation of the 3D model tachometer housing. Source: Momex.cat" title="Step2">
</center>
<!--more-->

<b>3.2- Base for the screws</b>: In order to hold the housing to the bracket, a rear cover will be needed. In order to do this, 4 cilyndrical shapes will be added to the base as material reinforcement. Creating a new <i>sketch</i> in the top base face, we will draw 4 circumferences and afterwards we will extrude them 6mm in the +Z direction.
<center>
<img style="display:inline" src="/images/Part12/step3.png" width="45%" alt="Content: Creation of the 3D model tachometer housing. Source: Momex.cat" title="Step3">
<img style="display:inline" src="/images/Part12/step4.png" width="45%" alt="Content: Creation of the 3D model tachometer housing. Source: Momex.cat" title="Step4">
</center>

<b>3.3- Switch hole</b>: Same as before, we create a new <i>sketch</i> in the top base face and draw a circumference and afterwards we execute the <i>pocket</i> operation in order to create the hole (-Z).
<center>
<img style="display:inline" src="/images/Part12/step5.png" width="45%" alt="Content: Creation of the 3D model tachometer housing. Source: Momex.cat" title="Step5">
<img style="display:inline" src="/images/Part12/step6.png" width="45%" alt="Content: Creation of the 3D model tachometer housing. Source: Momex.cat" title="Step6">
</center>

<b>3.4- Bracket "horns" and wire holes</b>: As we said at the beginning, this bracket has a special "horns" used to center and fix the speedo and tachometer units. We will need to create an orifice in the housing to allow these shapes to fix the unit and at the same time to allow the harness to go inside and connect with the PCB. This time, we create a new <i>sketch</i> on the bottom base face and then we perform a pocket upwards (+Z).
<center>
<img style="display:inline" src="/images/Part12/step7.png" width="45%" alt="Content: Creation of the 3D model tachometer housing. Source: Momex.cat" title="Step7">
<img style="display:inline" src="/images/Part12/step8.png" width="45%" alt="Content: Creation of the 3D model tachometer housing. Source: Momex.cat" title="Step8">
</center>

<b>3.5- PCB placing stands</b>: In order to place the PCB inside the housing we will create interior side stands. To do so, first we will create a new <i>sketch</i> in a parallel X-Y plane 15 and 27 mm over the top base face. Afterwards, we can extrude 3mm in +Z direction in both <i>sketches</i>.
<center>
<img style="display:inline" src="/images/Part12/step9.png" width="45%" alt="Content: Creation of the 3D model tachometer housing. Source: Momex.cat" title="Step9">
<img style="display:inline" src="/images/Part12/step10.png" width="45%" alt="Content: Creation of the 3D model tachometer housing. Source: Momex.cat" title="Step10">
</center>

<b>3.6- <i>STL</i> File</b>: This is the file we will have to send to the 3D printing company of your choosing. Basically, once the design is finsihed, it is needed to glue all the extruded parts. To do so, go to <i>workbench "Part"</i> and in the toolbar go to <i>Part > Boolean > Union</i>. Once this is done, we have finished our part. Now we have to export it as .STL by going to <i>File > Export</i> and then selecting the <i>Mesh Formats (.stl)</i> format.
<center>
<img style="display:inline" src="/images/Part12/step11.png" width="45%" alt="Content: Creation of the 3D model tachometer housing. Source: Momex.cat" title="Step11">
<img style="display:inline" src="/images/Part12/step12.png" width="45%" alt="Content: Creation of the 3D model tachometer housing. Source: Momex.cat" title="Step12">
</center>

<table>
<thead>
<tr bgcolor="#F8E0E0">
<th><a href="/images/Part12/housing_FreeCAD.fcstd"> FreeCAD v0.15 File</a><br>
<a href="/images/Part12/vN.stl"> STL for 3D file </a> <br>
</th>
</tr>
</thead>
</table>


<b>Why did I not use the old analog speedometer housing?</b><br>
2 main reasons:<br>
1- General dimensions were not appropriate for fixing the housing to the bracket or the PCB to the housing.<br>
2- I wanted to try 3D printing :D<br>

<center>
<img style="display:inline" src="/images/Part12/hous1.jpg" width="25%" alt="Content: Old analog speedometer housing. Source: Momex.cat" title="carcassa d'un velocímetre analògic">
<img style="display:inline" src="/images/Part12/hous2.jpg" width="30%" alt="Content: Old analog speedometer housing. Source: Momex.cat" title="carcassa d'un velocímetre analògic">
</center>

## Result
Finally, here you have the 3D printed housing.

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
<b> Part12 </b>/
<a href="/en/HD-tacho-part13"> Part13 </a>/
<a href="/en/HD-tacho-part14"> Part14 </a>/
<a href="/en/HD-tacho-part15"> Part15 </a>
 </font>
</p>
