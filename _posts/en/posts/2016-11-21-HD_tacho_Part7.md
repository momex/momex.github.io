---
type: posts
layout: post
lang: en
comments: true
title: Digital Tachometer for Harley Davidson Sportster (Part 7 - Components) 
name: HD-tacho-part7
permalink: en/HD-tacho-part7
category: ENtacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, components
---
<p>
<font size="2"> 
<a href="/en/HD-tacho-part1">Part1 </a>/
<a href="/en/HD-tacho-part2"> Part2 </a>/
<a href="/en/HD-tacho-part3"> Part3 </a>/
<a href="/en/HD-tacho-part4"> Part4 </a>/
<a href="/en/HD-tacho-part5"> Part5 </a>/
<a href="/en/HD-tacho-part6"> Part6 </a>/
<b> Part7 </b>/
<a href="/en/HD-tacho-part8"> Part8 </a>/
<a href="/en/HD-tacho-part9"> Part9 </a>/
<a href="/en/HD-tacho-part10"> Part10 </a>/
 Part11 /
 Part12 /
 Part13 /
 Part14 /
 Part15
 </font>
</p>
In this part I will list the components and integrated circuits (IC) I have used. Below, there is a basic circuit diagram (full schematic will be detailed in the next part).<br>
<center><img src="/images/Part7/schematic1.PNG" width="80%" alt="Basic circuit diagram. Source: Momex.cat" title="Basic circuit diagram"></center>

<font size="3"><b>Remark</b>: Digit3 driver will be used alternatively with the RPM bar. In RPM mode we will see all 4 digits but in the rest of modes, Digit3 will remain OFF and the RPM bar will show the RPMs. This is done because the rest of modes can work perfectly with only 3 of the 4 digits.</font>

### Microchip PIC18F2553<br>

The <a href="http://www.microchip.com/wwwproducts/en/PIC18F2553" target="_blank">PIC18F2553</a> is the project brain. I would lie to you if I say that I chose this particular brand and model because it was the best of the best (best performance, best price, ...). Frankly speaking, I chose it because it was the MCU family I started to work with when I decided to learn electronics. That and because it had enough pins to carry out this project.<br>
<!--more-->
<center>
<img style="display:inline" src="/images/Part7/PIC18F2553.png" width="29%" alt="PIC18F2553. Source: Microchip Technology" title="PIC18F2553">
<img style="display:inline" src="/images/Part7/PIC18F2553_sch.jpg" width="70%" alt="PIC18F2553 pinout. Source: Microchip Technology" title="PIC18F2553 pinout">
</center>

Requirements and specifications:
<dl>
- <b>Processing speed</b>: According the datasheet, this PIC can run up to 48MHz. For this application, 20MHz will be enough.<br>
- <b>Interruptions</b>: we will need one in order to stop temporarily the infinite loop and read the incoming J1850 bus message.<br>
- <b>Timers</b>: there are 4 timers available and they will be used as following.<br>
<dd>TO: functions related to the messages emission and reception.</dd>
<dd>T1: main code timer.</dd>
<dd>T2: brightness intensity regulation by means of PWM.</dd>
<dd>T3: function used to broadcast the information to the 7-segment driver.</dd>
- <b>I/O</b>: needed for the switch button, transistors and signals to the 7-segment display. <br>
- <b>PWM</b>: adjustment of the 7-segment display brightness by means of PWM control.<br>
- <b>USART</b>: In case we need the capability of designing a datalogger.<br>
</dl>

Furthermore, we will need:<br>

- <b>In-Circuit Debugger/Programmer</b>: this means a specífic programmer for PICs. In this project I used the <a href="https://en.wikipedia.org/wiki/PICkit" target="_blank">PICkit 2 and PICkit 3</a>, from the same Microchip Technology company. These tools are connected between the computer (via USB) and your IC (via 3 pins; PGC, PGD i MCLR) and they allow you to program the PIC with the code you have compiled previously.<br>
<center><img style="display:inline" src="/images/Part7/pickit3.png" width="50%" alt="PICkit 3. Source: Microchip Technology" title="PICkit 3"></center>
- <a href="https://en.wikipedia.org/wiki/MPLAB" target="_blank"><b>MPLAB</b></a> it is an IDE (<i>Integrated Development Environtment</i>) for PICs. It allows us to edit and compile code that we will program on the PIC afterwards with the PICkit. <br>


### Micrel/Microchip MM5450YN<br>
If the PIC is the brain of the project, the <a href="http://ww1.microchip.com/downloads/en/DeviceDoc/mm5450.pdf" target="_blank">MM5450</a> is the heart. This IC will allow us to control lots of pins in a very easy way. As a quick fact, according its website, by 2015 Microchip bought Micrel.
<center>
<img style="display:inline" src="/images/Part7/MM5450.png" width="29%" alt="MM5450. Source: Micrel" title="MM5450">
<img style="display:inline" src="/images/Part7/Micrel_sch.jpg" width="50%" alt="MM5450 pinout. Source: Micrel" title="MM5450 pinout">
</center>

Main specifications:<br>
<dl>
- <b>Brightness Control</b>: This IC has 1 pin (#19) that allows us to regulate the brightness of all the pins. With a PWM signal from the PIC and a resistor, we will be able to regulate the brightness by changing the PWM DC (<a href="https://en.wikipedia.org/wiki/Duty_cycle" target="_blank">Duty cycle</a>).<br>

- <b>Serial Data input</b>: All the 34 input pins from this LED driver are controlled by 2 pins; a clock signal (CLK) and a Data signal (DATA). 
<center><img style="display:inline" src="/images/Part7/MM5450_CLK_DATA.PNG" width="60%" alt="DATA and CLK signals. Source: Momex.cat" title="DATA and CLK signals"></center>
The MM5450 always waits for 36 clock signals (rising edge). First, it will check that the value on pin DATA has high value. If it is like this, it will start saving the values read from DATA for the next 35 rising edges. Once it receives the last clock (last rising edge),  (for the MM5450 with only 34 operative pins, the read value on the 35th rising edge will not be considered, but it is mandatory to send something) the IC will apply the values to the output pins and it will wait again for the new 36 next values.<br>

- <b>34 pins</b>: Following diagram will show you how pins will be used on the MM5450. The alternative would be to multiplex the 7-Segments, this would allow me to use only 12 instead of 29, but for reasons I will explain on Part 15 (Issues during development) I decided to go for this configuration.<br>
<center><img style="display:inline" src="/images/Part7/MM5450_non_multi.PNG" width="80%" alt="Connection diagram. Source: Momex.cat" title="Connection Diagram"></center>
</dl>

### LM340T-5.0/NOPB<br>
No doubt, for me, this 5V <a href="http://www.ti.com/lit/ds/symlink/lm340-n.pdf" target="_blank">Fixed Voltage Regulator</a> from Texas Instruments (TI) offers the best solution in IC format in order to have a simple and reliable power supply.<br>
<center><img style="display:inline" src="/images/Part7/LM340T.png" width="20%" alt="LM340T Source: unknown" title="LM340T-5V"></center>
Brief Specifications:<br>
- It can supply up to 1A on the output. It has to be combined with a heat sink.<br>
- Overtemperature protection.<br>
- Shortcircuit protection.<br>

### Trasnceiver
In order to be able to read the J1850 bus messages, first we need to adapt the voltage levels between the bus and the PIC. There are some IC such as the<a href="http://www.nxp.com/files/analog/doc/data_sheet/MC33990.pdf" target="_blank">MC33990</a> (NXP Feescale Semiconductor) or the <a href="http://alt.ife.tugraz.at/datashts/Harris/hip7020.pdf" target="_blank">HIP7020</a> (HARRIS Semiconductor), but as it is a very old technology, these ICs are discontinued and finding them on second hand markets it is no easy task.
<center><img style="display:inline" src="/images/Part7/MC33990_chip.PNG" width="20%" alt="MC33990 Source: Momex.cat" title="LM340T-5V">
<img style="display:inline" src="/images/Part7/j1850_chip_comparison.PNG" width="70%" alt="MC33990 i HIP7020 Source: Momex.cat" title="MC33990 and HIP7020 pinout"></center>

Nevertheless, currently I am using the MC33990 in order to send some fake RPM and gear messages through a J1850 bus and receiving them by one of my working prototypes. Thanks to this, I am able to improve the software/code with no need to physically connect it to the motorcycle.<br>
<center>
<img style="display:inline" src="/images/Part7/MC33990_sch.PNG" width="49%" alt="MC33990 Diagram Source: Momex.cat" title="Diagram MC33990">
<img style="display:inline" src="/images/Part7/MC33990_osc.png" width="49%" alt="Signal shape on MC33990 Source: Momex.cat" title="Signal shape MC33990">
</center>

The alternative on these circuits is to use transistors and resistors in order to adapt the voltage levels between the bus and the PIC. As, for the moment, we will need only to read, the final circuit will be very simple as you can see in the image below. One intersting thing to see is how the voltage values are changing on the circuit and how they are finally inverted at the end. If you want to use the MC33990, you will need to change 2 things in the code; invert the input value on the PIC by means of a "!" and the most important, to change the kind of interruption selecting the rising edge interruption.
<center>
<img style="display:inline" src="/images/Part7/transceiver_levels.PNG" width="49%" alt="Diagram transceiver Source: Momex.cat" title="Diagram transceiver">
<img style="display:inline" src="/images/Part7/transceiver.png" width="49%" alt="Signals shape: unknown" title="Signals shape on the oscilloscope">
</center>
<br>


<p>
<font size="2"> 
Project Index:<br>
<a href="/en/HD-tacho-part1">Part1 </a>/
<a href="/en/HD-tacho-part2"> Part2 </a>/
<a href="/en/HD-tacho-part3"> Part3 </a>/
<a href="/en/HD-tacho-part4"> Part4 </a>/
<a href="/en/HD-tacho-part5"> Part5 </a>/
<a href="/en/HD-tacho-part6"> Part6 </a>/
<b> Part7 </b>/
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
