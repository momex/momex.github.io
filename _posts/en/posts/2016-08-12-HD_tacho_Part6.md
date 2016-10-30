---
type: posts
layout: post
lang: en
comments: true
title: Digital Tachometer for Harley Davidson Sportster (Part 6 - Design and functions)
name: HD-tacho-part6
permalink: en/HD-tacho-part6
category: ENtacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, design, functions
---
<p>
<font size="2"> 
<a href="/en/HD-tacho-part1">Part1 </a>/
<a href="/en/HD-tacho-part2"> Part2 </a>/
<a href="/en/HD-tacho-part3"> Part3 </a>/
<a href="/en/HD-tacho-part4"> Part4 </a>/
<a href="/en/HD-tacho-part5"> Part5 </a>/
<b> Part6 </b>/
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
This part will be divided into two sections and for each one I will summarize the most important ideas I have come up with.

### Conceptual design

After doing a little bit of research and benchmarking, knowing the ideas that I liked the most, understanding what ideas are available and knowing which are my theoretical & manufacturing limitations, these are my conclusions:<br>
- <b>2 gauges</b>: This will allow me to keep the stock speedometer with its information (odometer).<br>
- <b>Simplification</b>: I will use the bracket 67338-97 for the 2 gauges that comes with the Tachometer kit 67182-07. On ebay you can find them from time to time. With this, PCB shape and size (&#8709;85mm) and housing (&#8709;90mm) are already set.<br>
- The <b>Harness</b> could also be purchased on ebay (68811-07) but, it will be cheaper if I make it by myself. It is only needed 3 wires (+12V, GND and bus J1850) and no specific connector.<br>
- <b>Tell-tales and displays:</b>: 7-Segments and LEDs.<br>
- <b>Gauge face</b>: vinyl, stiker or similar.

A draft idea would be something similar like the following images:<br><center>
<img style="display:inline" src="/images/Part6/proto-disseny1.png" width="30%" alt="HD Sportster Tachometer. Source: Momex.cat" title="HD Sportster with double gauge">
<img style="display:inline" src="/images/Part6/proto-disseny.jpg" width="40%" alt="Draft. Source: Momex.cat" title="Draft">
</center>
<!--more-->

### Main Functions

- <b>RPM:</b> Value read from the data bus and shown on the 4x7-Segments. This signal has 1 RPM resolution and it is updated several times per second, so it is important to program the code in order to get a proper update ratio to be able to read it. <br>
- <b>Current Gear:</b> Value read from the data bus and shown on the 7-segments located in the bottom left part. <br>
- <b>Fuel consumption:</b> Value read from the data bus and shown on the 4x7-segments. (Currently not implemented)<br>
- <b>Engine Temperature:</b> Value read form the data bus and shown on the 4x7-segments. <br>
- <b>RPM LED bar:</b> When Fuel Consumption or Engine Temperature functions are active, the engine RPM will be shown through this LED bar. Some code can be implemented to have special light effects, for example, blinking if reaching max RPM.<br>
- <b>Rear switch:</b> It will be used to switch between modes and also to change light intensity on the tachometer.<br>
- <b>Light intensity:</b> Due to 7-segments and LEDs visibility depend on the direct sun light, if the LED intensity was constant there would be some scenarios with problems (for example too much intensity during night or not enough intensity during daylight). Due to this, I decided to create a function in order to be able to manually switch between 2 modes of light intensity (day / night) using rear switch.


<p>
<font size="2"> 
Project Index:<br>
<a href="/en/HD-tacho-part1">Part1 </a>/
<a href="/en/HD-tacho-part2"> Part2 </a>/
<a href="/en/HD-tacho-part3"> Part3 </a>/
<a href="/en/HD-tacho-part4"> Part4 </a>/
<a href="/en/HD-tacho-part5"> Part5 </a>/
<b> Part6 </b>/
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
