---
type: posts
layout: post
lang: en
comments: true
title: Digital Tachometer for Harley Davidson Sportster (Part 15 - Issues during development and improvements)
name: HD-tacho-part15
permalink: en/HD-tacho-part15
category: ENtacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, SAE, improvements, project, errors, problems, issues
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
<a href="/en/HD-tacho-part13"> Part13 </a>/
<a href="/en/HD-tacho-part14"> Part14 </a>/
<b> Part15 </b>
 </font>
</p>

<b>Issues:</b><br>
- First and main issue was.. how the hell do I make this project?! It was my first electronic project and I had to think & plan basically all the steps (quite stressful).<br>
- The J1850 VPN trasnceivers were discontinued and not available in the main online electronic stores. Luckily, I was able to find 3 IC on eBay and I was able to build my first dummy control unit that was broadcasting messages all the time on the data bus. For the final design I manage to replace the IC by a couple of transistors and resistors.<br>
- The lack of experience when soldering electronic parts and in particular SMD components. I lost 2 PCB on the way but I learnt the lesson to start always by soldering the most difficult components first.<br>
- I suffered many times problems on the PCB, usually due to my poor soldering skills that created micro joint cracks. I spent sometimes weeks trying to find the rootcause and that caused many times to loose hope. <br>
- Poor test & lab equipment, for example a computer 12V fixed power supply to simulate the battery of the bike. Anyway, I have to say that even with some basic equipment if you want to do something you can do it. With time I manage to buy a decent soldering station, a decent multimeter, scope, ....<br>

<br>

<b>Improvements:</b><br>
- The software still has some minor glitches that I don't care to solve. For example, from time to time some number that should not be there appears on the gear indicator, but as fast as it comes, it goes away. <br>
- Need to implement the fuel consumption function on the tachometer. <br>
- Brightness can be increased or decreased by user request, except for the gear indicator that is fixed and it could disturb at night.<br>
- All the LEDs used on the RPM bar or on the mode indicator can not be seen when driving at daylight.<br>
- When the sun shines from the rear of the bike, it is not possible to read the 7 segments (even with full brightness).<br>
- Rear switch does not perform as expected sometimes. The connector should be improved.<br>
- 3D printed housing could be improved in many ways. It does not have a PCB fixing tab, only a position tab. Also it could be improved the hole on the back of the housing to avoid/reduce humidity entrance.<br>
- Design and print a vinyl for the tachometer cover. Currently, it has a printed paper that is now deteriorated due to the humidity and the sun.


<br>
Any other question or request, please leave a comment below or send me an email.
Salut

<center>
<img src="/images/Part14/04.png" width="80%" alt="Content: Homemade Digital Tahcometer for Sportster. Source: Momex.cat" title="Homemade Digital Tahcometer for Sportster">
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
<a href="/en/HD-tacho-part12"> Part12 </a>/
<a href="/en/HD-tacho-part13"> Part13 </a>/
<a href="/en/HD-tacho-part14"> Part14 </a>/
<b> Part15 </b>
 </font>
</p>
