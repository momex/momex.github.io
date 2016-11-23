---
type: posts
layout: post
lang: en
comments: true
title: Digital Tachometer for Harley Davidson Sportster (Part 5 - Tachometer Benchmarking)
name: HD-tacho-part5
permalink: en/HD-tacho-part5
category: ENtacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, benchmarking, mercat
---
<p>
<font size="2"> 
<a href="/en/HD-tacho-part1">Part1 </a>/
<a href="/en/HD-tacho-part2"> Part2 </a>/
<a href="/en/HD-tacho-part3"> Part3 </a>/
<a href="/en/HD-tacho-part4"> Part4 </a>/
<b> Part5 </b>/
<a href="/en/HD-tacho-part6"> Part6 </a>/
<a href="/en/HD-tacho-part7"> Part7 </a>/
<a href="/en/HD-tacho-part8"> Part8 </a>/
<a href="/en/HD-tacho-part9"> Part9 </a>/
 Part10 /
 Part11 /
 Part12 /
 Part13 /
 Part14 /
 Part15
 </font>
</p>
Easiest way to start a project is always doing a benchmarking or market analysis. Doing this, we will be able to know what do we want, how do we want it and if we can reduce the complexity of the project by using already existing components. <br>
<li><h4>Harley Davidson - Analog tachometer Kit 67182-07 (Price April'16: HD USA 337 USD / HD UE 524 €):</h4></li>
<font size="3">Installation Dificulty:</font><font style="display:inline" size="4"> &#9733;&#9733;&#9734;&#9734;&#9734;</font>
<center>
<img style="display:inline" src="/images/Part5/67182-07_OB.jpeg" width="30%" alt="HD Sportster Tachometer. Source: Harley Davidson" title="HD Sportster with double gauge">
<img style="display:inline" src="/images/Part5/taco_67182-07.jpeg" width="30%" alt="Speedometer and Tachometer bracket Ref#: 67182-07. Source: Harley Davidson" title="Suport Ref# 67182-07">
<img style="display:inline" src="/images/Part5/harness_68811-07.png" width="20%" alt="Harness Ref# 68811-07. Source: Harley Davidson" title="Harness Ref# 68811-07">
</center>

This is the solution that HD gives to all of you wanting to incorporate a second gauge with an analog tachometer into your Sportster. According the <a href="http://www.harley-davidson.com/app-content/service/isheets/-J02933.PDF" target="_blank">installation manual</a>, this kit has, as interesting part for our project, a double gauge bracket (ref#: 67338-97) and a specific harness (ref#: 68811-07).<br>
<!--more-->

<li><h4>Harley Davidson - Digital speedometer/ Analog tachometer 4" Kit 70900274 (Price April'16: HD USA 315 USD / HD UE 405 €):</h4></li>
<font size="3">Installation Dificulty:</font><font style="display:inline" size="4"> &#9733;&#9734;&#9734;&#9734;&#9734;</font>
<center>
<img style="display:inline" src="/images/Part5/70900274_OB.jpeg" width="25%" alt="HD Sportster 2 in 1. Source: Harley Davidson" title="HD Sportster with 2 in 1 gauge">
<img style="display:inline" src="/images/Part5/70900274_gauge.JPG" width="25%" alt="Tacho and speedometer gauge. Source: Harley Davidson" title="Kit 70900274">
</center>

Another solution offered by HD if you prefer having only 1 gauge on the bike to show all the information. According the <a href="http://www.harley-davidson.com/app-content/service/isheets/-J05551.PDF" target="_blank">installation manual</a>, this kit only includes this 2 in 1 gauge, so there is no other part that we can use. Nevertheless, we have a datasheet with some additional information that can come in handy. Three things: <br>
- You need to copy the information from the original speedometer/odometer to the new gauge.<br>
- Since 2008, Sportster ECM can inform about the current gear.<br>
- The gauge will also inform about the fuel level if you purchase separately the Fuel Sensor Kit (Ref# 61200008).<br>
 
<li><h4>Harley Davidson - Speedo and Tachometer from a Sportster XR1200R (Price April'16: 518.00 USD / HD UE - € ):</h4></li>
<font size="3">Installation Dificulty:</font><font style="display:inline" size="4"> &#9733;&#9733;&#9734;&#9734;&#9734;</font>
<center>
<img style="display:inline" src="/images/Part5/XR1200R_meter.jpg" width="25%" alt="HD XR1200R Gauges. Source: http://ridermagazine.com" title="XR1200R tachometer and speedometer">
<img style="display:inline" src="/images/Part5/xr1200r_67576-08.png" width="25%" alt="Tachometer 67576-08. Source: www.befr.ebay.be" title="Tachometer 67576-08">
<img style="display:inline" src="/images/Part5/xr1200r_67087-08.jpeg" width="25%" alt="Speedometer 67087-08. Source: m.ebay.ie" title="Speedometer 67087-08">
</center>

First option that is different from the ones that HD proposes. As expected, it is not sold as a kit and you have to buy the parts separately or try to find a good deal on the internet in the second hand market. <a href="http://www.stcharlesharleydavidson.com/oempartfinder.htm#/Harley-Davidson%C2%AE/XR1200_LA_SPORTSTER_1200_%282008%29/SPEEDOMETER_%26_TACHOMETER_-_XR1200/99451-08A\LA/99451-08A\SPEEDOMETER|~TACHOMETER|~XR1200\LA" target="_blank">Parts</a>: <br>
<font size="4">67087-08 SPEEDOMETER -<font style="display:inline" size="3"> <a href="http://www.boardtrackerharleyonline.com/harley-davidson/speedometer-67087-08" target="_blank"> 222.00 USD </a><br>
67576-08 TACHOMETER W/ODOMETE -<a href="http://www.boardtrackerharleyonline.com/harley-davidson/tachometer-with-odometer-67576-08" target="_blank"><font size="3"> 169.00 USD</font></a><br>
67157-08 BRACKET, INSTR -<a href="http://www.boardtrackerharleyonline.com/harley-davidson/bracket-instr-67157-08" target="_blank"><font size="3"> 38.00 USD</font></a><br>
67170-08 BACK COVER, INSTR 0604 -<a href="http://www.boardtrackerharleyonline.com/harley-davidson/back-cover-instr-0604-67170-08" target="_blank"><font size="3"> 25.00 USD</font></a><br>
67091-08 INSTR HARNESS 0604 -<a href="http://www.boardtrackerharleyonline.com/harley-davidson/instr-harness-0604-67091-08" target="_blank"><font size="3"> 64.00 USD</font></a><br>
67121-95A GASKET tachometer -<a href="http://www.boardtrackerharleyonline.com/harley-davidson/gasket-front-speedo-tach-shock-67121-95a" target="_blank"><font size="3">7.10 USD</font></a><br>
67174-08  GASKET speedometer -<a href="http://www.boardtrackerharleyonline.com/harley-davidson/gasket-shock-0704-67174-08" target="_blank"><font size="3"> 11.00 USD</font></a><br>
</font>

<li><h4>Dakota Digital Direct Plug-in Speedo & Tach - <a href="http://www.dakotadigital.com/index.cfm/page/ptype=product/product_id=684/prd684.htm">MCL-3204 </a> (Price April'16: 400 USD / UE - €):</h4></li>
<font size="3">Installation Dificulty:</font><font style="display:inline" size="4"> &#9733;&#9734;&#9734;&#9734;&#9734;</font>
<center>
<img style="display:inline" src="/images/Part5/MCL-3200.jpg" width="25%" alt="Dakota Digital MCL-3200 red. Source: Dakota Digital" title="MCL-3200">
<img style="display:inline" src="/images/Part5/MCL-3200_vermell.gif" width="25%" alt="MCL-3200 Plug in. Source: Dakota Digital" title="MCL-3200">
</center>

Yet another solution, this time not from HD. This is only 1 gauge with everything integrated and plug&play. According the <a href="http://www.dakotadigital.com/pdf/mcl-3204.pdf" target="_blank"> installation manual</a>, this unit has many interesting functions using the available information in the data bus as the current gear, rpm, engine temperature,... and it also has special functions as time from 0-100kph (0-60mph), adjustable shifting point,... This is a true sporty gague... very interesting indeed.


<li><h4>Speedway instruments - <a href="http://speedwayinstruments.com/products/microtach.html">microTach+ </a>Tachometer (Price April'16: 150 USD / UE - €):</h4></li>
<font size="3">Installation Dificulty:</font><font style="display:inline" size="4"> &#9733;&#9733;&#9734;&#9734;&#9734;</font>
<center>
<img style="display:inline" src="/images/Part5/microtach.jpeg" width="25%" alt="microTach+ installed. Source: Speedway instruments" title="microTach+">
<img style="display:inline" src="/images/Part5/microtach2.jpg" width="25%" alt="2 different surfaces for microTach+, chrome or black. Source: Speedway instruments" title="2  different surfaces for microTach+">
</center>

Super simple design offered by this brand with only the 2 most significant dígits to show the engine RPM. Remember that stock Sportster 883/1200 only get up to aprox 6000 RPM. This tachometer comes with two different finishes (chrome and black) and it uses only 3 wires (Ign, ground and spark plug ignition coil).

<li><h4>KOSO NORTH AMERICA- <a href="http://kosonorthamerica.com/product/tnt-01r-8000-harley-davidson/">TNT-01R</a> Tachometer – 8 000 RPM (Price April'16: 200 USD / UE - €):</h4></li>
<font size="3">Installation Dificulty:</font><font style="display:inline" size="4"> &#9733;&#9733;&#9733;&#9734;&#9734;</font>
<center>
<img style="display:inline" src="/images/Part5/KOSO.jpg" width="25%" alt="KOSO TNT-01R caràtula blanca i negra. Source: KOSO NORTH AMERICA" title="KOSO TNT-01R">
<img style="display:inline" src="/images/Part5/TNT-01R tacho.png" width="25%" alt="KOSO TNT-01R kit. Source: KOSO NORTH AMERICA" title="KOSO TNT-01R">
</center>

Another advanced solution to connect direclty to the spark plug coil. According the <a href=" http://kosonorthamerica.com/instructions/BA035102.pdf" target="_blank"> installation manual</a> of this programable analog tachometer, it can be installed in all motorcycles and there is a configuration menu to make the proper adjustments.<br>


<li><h4>Chinese solutions on eBay:</h4></li>
<font size="3">Installation Dificulty:</font><font style="display:inline" size="4"> &#9733;&#9733;&#9734;&#9734;&#9734;</font>
<center>
<img style="display:inline" src="/images/Part5/ebay_tacho.jpg" width="25%" alt="Digital Tachometer. Source: ebay" title="Digital Tachometer">
<img style="display:inline" src="/images/Part5/ebay_tacho2.jpg" width="25%" alt="Analog Tachometer. Source: ebay" title="Analog Tachometer">
</center>

Small gauges in 3-wire connection format (Ign, ground and spark plug coil).

<li><h4>Other:</h4></li>
<a href="http://www.baronscustom.com/catalog/display/1062/index.html" target="_blank"> 2" MINI-BULLET TACH Black Face 1" Clamp</a>
<br>

<p>
<font size="2"> 
Project Index:<br>
<a href="/en/HD-tacho-part1">Part1 </a>/
<a href="/en/HD-tacho-part2"> Part2 </a>/
<a href="/en/HD-tacho-part3"> Part3 </a>/
<a href="/en/HD-tacho-part4"> Part4 </a>/
<b> Part5 </b>/
<a href="/en/HD-tacho-part6"> Part6 </a>/
<a href="/en/HD-tacho-part7"> Part7 </a>/
<a href="/en/HD-tacho-part8"> Part8 </a>/
<a href="/en/HD-tacho-part9"> Part9 </a>/
 Part10 /
 Part11 /
 Part12 /
 Part13 /
 Part14 /
 Part15
 </font>
</p>
