---
type: posts
layout: post
lang: en
comments: true
title: Digital Tachometer for Harley Davidson Sportster (Part 9 - PCB Design)
name: HD-tacho-part9
permalink: en/HD-tacho-part9
category: ENtacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, SAE, PCB, design, Altium
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
<b> Part9 </b>/
 Part10 /
 Part11 /
 Part12 /
 Part13 /
 Part14 /
 Part15
 </font>
</p>
In this 9th part I will show you some of the steps I followed up to do this PCB design.<br>

<b>1)</b> To be able to do the schematic or the PCB layout, Altium Designer requires some libraries where it can find the components information we will use. It will be necessary to have 2 libraries, one for the schematic with, for example, the number of IC pins, and antoher library for the PCB with the footprins and the position of the terminals. Additionally, if you want to be able to see a 3D version of your PCB, it is in this second library where you have to include the 3D files (STEP format). Following figures show a couple of examples where we can see from left to right (schematic, terminal list, footprint and a 3D model using STEP files). <br>

<u><b>7 SEGMENTS</b></u>
<center><img style="display:inline" src="/images/Part9/7Seg_sch.PNG" width="24%" alt="Content: 7-segments schematic. Source: Momex.cat">
<img style="display:inline" src="/images/Part9/7Seg_sch_pins.PNG" width="22%" alt="Content: Pinout 7-segments. Source: Momex.cat">
<img style="display:inline" src="/images/Part9/7Seg_PCB.PNG" width="18%" alt="Content: footprint 7-segments. Source: Momex.cat">
<img style="display:inline" src="/images/Part9/7Seg_PCB_3d.PNG" width="22%" alt="Content: STEP vista 3D 7-Segments. Source: Momex.cat"></center>

<u><b>PIC18F2553</b></u>
<center><img style="display:inline" src="/images/Part9/PIC_sch.PNG" width="24%" alt="Content: PIC schematic. Source: Momex.cat">
<img style="display:inline" src="/images/Part9/PIC_sch_pins.PNG" width="11%" alt="Content: Pinout PIC. Source: Momex.cat">
<img style="display:inline" src="/images/Part9/PIC_PCB.PNG" width="19%" alt="Content: footprint PIC. Source: Momex.cat">
<img style="display:inline" src="/images/Part9/PIC_PCB_3d.PNG" width="30%" alt="Content: STEP veiw 3D PIC. Source: Momex.cat"></center>

<b>2)</b> Once the schematic is done (<a href="/en/HD-tacho-part8">part8</a>), we can proceed to build the PCB. To do so, we will need to transfer all the component footprints to the PCB shape we choose.<br>

<center><img style="display:inline" src="/images/Part9/volcatPCB.PNG" width="99%" alt="Content: Component footprints on the PCB layout, Altium Designer. Source: Momex.cat"></center>

<!--more-->

<b>3)</b> Before we start positioning all the components, we will need to decide and create the shape of the PCB. Here it is important to know who will be our PCB manufacturer in order to follow its manufacturing rules (for example, max PCB size, color, ...). <br>

<center><img style="display:inline" src="/images/Part9/pcbshape.PNG" width="30%" alt="Content: PCB, shape and size in Altium Designer. Source: Momex.cat"></center>


<b>4)</b> Position and, if necessary, rotate the components over the PCB defined area. As you can see in the image below, Altium shows which are the interconnections between the pins of the different components. At the beginning, it will look like a mess, but with time you will see how this will help you to connect everything.

<center><img style="display:inline" src="/images/Part9/pcb_routing2.PNG" width="70%" alt="Content: Component position within the PCB, Altium Designer. Source: Momex.cat"></center>

<b>5)</b> There are many ways to create the paths and vias on the PCB and it is worth to mention that, having 2 layers (upper and lower), it just makes this task easier.. Probably the most common way is to do all the traces vertical on the top layer and all the traces horizontal on the bottom layer, trying to minimize the number of vias used to connect one layer with the other. Another way, the one some designers try to avoid, is by using the auto router that comes by default in many software (following T-Shirt tries to show that using it is a bad idea)

<center><img src="/images/Part9/chrisgamm.jpg" width="40%" alt="Content: T-Shirt NEVER trust the autorouter. Source: teespring.com"></center>

<b>6)</b> Finally, here you have the final result after some hours trying to think and connecting all the pins.<br>

<b>FRONT SIDE</b>
<center><img style="display:inline" src="/images/Part9/3d front.PNG" width="49%" alt="Content: PCB Front side Harley tachometer. Source: Momex.cat">
<img style="display:inline" src="/images/Part9/3d lateral.PNG" width="49%" alt="Content: PCB Side view  Harley tachometer. Source: Momex.cat"></center>

<b>BACK SIDE</b>
<center><img style="display:inline" src="/images/Part9/3d back.PNG" width="49%" alt="Content: PCB Back side Harley tachometer. Source: Momex.cat">
<img style="display:inline" src="/images/Part9/3d back side.PNG" width="49%" alt="Content: PCB Side view Harley tachometer. Source: Momex.cat"></center>

<b>7)</b> As a last step, we will need the files in <a href="https://en.wikipedia.org/wiki/Gerber_format" target="_blank">Gerber</a> format to send them to our PCB manufacturer. Again, it is very important to know the rules our PCB manufaturer is requesting to all the PCBs sent to them.

<center><img src="/images/Part9/gerberrules.png" width="70%" alt="Content: PCB manufacturing Rules. Source: seeedstudio.com"></center>

Gerber files content (Front and Back view)

<center><img style="display:inline" src="/images/Part9/gerber top.PNG" width="49%" alt="Content: Gerber files, PCB Front side Harley tachometer. Source: Momex.cat">
<img style="display:inline" src="/images/Part9/gerber bottom.PNG" width="45%" alt="Content: Gerber files, PCB back side Harley tachometer. Source: Momex.cat"></center>


You can download all the files created for this project:<br>

<table>
<thead>
<tr bgcolor="#F8E0E0">
<th><a href="/images/Part9/J1850_Tacho.SchDoc"> Schematic </a><br>
<a href="/images/Part9/J1850_Tacho.PcbDoc"> PCB </a> <br>
<a href="/images/Part9/J1850_Harley_tacho_gerber files.zip"> Gerber Files</a> <br>
</th>
</tr>
</thead>
</table>

<p>
<font size="2"> 
Project Index:<br>
<a href="/en/HD-tacho-part1">Part1 </a>/
<a href="/en/HD-tacho-part2"> Part2 </a>/
<a href="/en/HD-tacho-part3"> Part3 </a>/
<a href="/en/HD-tacho-part4"> Part4 </a>/
<a href="/en/HD-tacho-part5"> Part5 </a>/
<a href="/en/HD-tacho-part6"> Part6 </a>/
<a href="/en/HD-tacho-part7"> Part7 </a>/
<a href="/en/HD-tacho-part8"> Part8 </a>/
<b> Part9 </b>/
 Part10 /
 Part11 /
 Part12 /
 Part13 /
 Part14 /
 Part15
 </font>
</p>
