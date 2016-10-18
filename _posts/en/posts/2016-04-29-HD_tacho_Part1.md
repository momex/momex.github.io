---
type: posts
layout: post
lang: en
comments: true
title: Digital Tachometer for Harley Davidson Sportster (Part 1 - Introduction)
name: HD-tacho-part1
permalink: en/HD-tacho-part1
category: ENtacho
keywords: HD, harley, davidson, tachometer, tacho, rpm, J1850, SAE, introduction
---

While driving a vehicle we all have in mind at least a couple of basic indicators that will give us an idea of the speed and the engine RPMs. In trucks or passenger cars it is common to have more information but in a motorcycle, due to the available space, there is a limitation of info. We can find some models that have 2 gauges with the speedo and a tachometer and other models with one gauge and a LCD to show the speed.<br>
If we look at cheaper bikes or engines that don't rev up too much, everything gets much simpler. The indicators of a Harley Davidson Sportster are very basic, you can find a speedo gauge, some tell tales (fuel, engine check, ...) and a small LCD display to show the odometer, two partials and the current time. 
<p>


<center><img src="/images/Part1/meter.png" alt="Contingut: HD Sportster speedometer. Source: Momex.cat"></center>

For a person obsessed with control like me, this ammount of information was obviously not enough, so I decided to start a long term project (almost took me 4 years) in order to design some kind of display to give me some extra information like engine RPMs and gear engaged.<sub>(1)</sub>. <p>

Learning a bit of electronics and develope my own PCBs was a pending item in my checklist, so I decided to go for it. As everything I've learned comes from the <a href="https://en.wikipedia.org/wiki/Open-source_software" target="_blank">open source</a> / <a href="https://en.wikipedia.org/wiki/Free_software" target="_blank">free software</a> I decided to create this blog in order to return my learnings to the community.<br>

I will divide this project in 14 parts where I will explain the different steps I followed, schematics, designs, code, ... 
<p>

<a href="/en/HD-tacho-part1">Part 1 - Introduction </a> <br>
<a href="/en/HD-tacho-part2">Part 2 - Communication Bus and sensors </a><br>
<a href="/en/HD-tacho-part3">Part 3 - Harley Davidson and SAE J1850 VPW </a><br>
<a href="/en/HD-tacho-part4">Part 4 - Bus Messages </a><br>
<a href="/en/HD-tacho-part5">Part 5 - Tachometer Benchmarking </a><br>
<a href="/en/HD-tacho-part5">Part 6 - Design and functions </a><br>
Part 7 - Components<br>
Part 8 - Schematics <br>
Part 9 - PCB design <br>
Part 10 - Source code and libraries <br>
Part 11 - Housing design and brackets <br>
Part 12 - Wiring harness and tests <br>
Part 13 - Wiring Harness and installation <br>
Part 14 - Problems during the project <br>

<p>
<sub>(1) Have you ever been riding in 5th gear and tried to upshift when there is no 6th?</sub>

<!--more-->
