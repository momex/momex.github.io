---
type: posts
layout: post
lang: en
comments: true
title: Digital Tachometer for Harley Davidson Sportster (Part 3 - Harley Davidson and SAE J1850 VPW)
name: HD-tacho-part3
permalink: en/HD-tacho-part3
category: ENtacho
keywords: HD, harley, davidson, tachometer, tacho, rpm, J1850, SAE, VPW, specification
---

The best and shortest way to understand this protocol is to read<a href="http://download.intel.com/design/intarch/papers/j1850_wp.pdf" target="_blank"> this document</a>. The longest way is to read directly the SAE J1850 documentation. Nevertheless, in this post I will try to summarize the most relevant concepts of this protocol in order to be able to write the proper code to receive and interpret the ECM messages.<br>

According to the standard SAE J1850 VPW, in our bike we will have 1-wire data bus where the information will be broadcasted based on different voltage levels and tranmission timings. These levels are: <br>
- <u>Passive</u>: 0 - 3,5V (natural state of the data bus)<br>
- <u>Active</u>: 4,25V - 20V (control units can activate the bus through transistors)<br>
<br>
Main bus properties are:<br>
- <u>Serial bus</u>: information is sent bit by bit.<br>
- <u>Asynchronous</u>: broadcasted information between nodes is managed by the same emitter instead of beeing synchronized by another clock signal.<br>
- <u>Master-less</u>: there is no node with superiority over the others.<br>
- <u>Peer to peer</u>: All nodes have same capability to transmit.<br>
<br>
One important property of the nodes is that when one is transmitting to the data bus, it listens to itself to check if what it says is the same that is in the data bus. In following lines we will understand why.<br>
<!--more-->
<dl></dl>

### Arbitrariety:

In this kind of buses everybody will be able to transmit, for this reason it is necessary to set specific rules in order to not have chaos. It can be mainly summarized in 2 rules:<br>
<dl>
<b>1-</b> The node who wants to transmit first listens to the bus.
   <dd><b>a)</b> If bus is empty during a certain period of time (nobody is transmitting), then this node is allowed to start the transmission.<br></dd>
   <dd><b>b)</b> If someone is already transmitting, then it will wait for the transmission to finish and an additionally specified time before it is allowed to start its own transmission.<br></dd>
<b>2-</b> Once it is transmitting the message, in case the bit transmitted is not the same as the bit it reads from the bus, automatically it has to stop the transmission because it lost arbitrariety. This means that other node is also transmitting a message with higher priority.
</dl>

<img src="/images/Part3/02.PNG" alt="Source: Xavier Morales">

<dt>And how is this message priority defined?</dt>
Everything is managed by voltage levels. As said before, the bus is passive in natural status and therefore the nodes only have activate o deactivate the transistor in order to change the bus to active or passive mode. If one node is transmitting a passive bit but it reads an active bus, this means that some other node is transmitting at the same time.
<dt>And then?</dt> 
Everything lays in the 3 bytes in the message header. There, one of these bytes shows the message priority stablished by the engineer who decided which messages were more important (e.g. RPM message should be more important than a Temperature message because in one second, temperature will not change dramatically, but RPM can vary a lot).<br>
Messages with higher priority will be then those with more active bits at the beginning of the header.

### Message structure:
Structure of a Harley Davidson message:
<img src="/images/Part3/01.PNG" alt="Source: Xavier Morales">

With this format, the maximum number of bytes is set to 11.<br>

<dt>SOF (Start Of Frame)</dt>
The node starting to transmit has to start with an active bit during 200us. After this time, it will proceed with the header.

<dt>Header</dt>
It can be set from 1 to 3 bytes. In the case of Harley Davidson we will find 3 bytes:<br>
<dd><b>Byte #1:</b> It will show to the other nodes the Header configuration (e.g.: 1 o 3 bytes)<br>
<img src="/images/Part3/03.PNG" alt="Source: Xavier Morales"></dd>
<dd><b>Byte #2:</b> Target address or Primary ID. This value will be available in the SAE J2178-4 and it can be a Command ID or a Status ID.</dd>
<dd><b>Byte #3:</b> Source address</dd>

Header byte#1 meaning:<br>
<img src="/images/Part3/04.PNG" alt="Source: Xavier Morales">

<br>
Example (RPM: $28 $1B $10)<br>
<b>$28</b>
<img src="/images/Part3/05.PNG" alt="Source: Xavier Morales">

<dl>
<dd>001: Value close to high priority </dd>
<dd>0: 3 bytes header</dd>
<dd>1: IFR not necessary</dd>
<dd>0: Functional address</dd>
<dd>00:-</dd>
<b>$1B</b>
<dd> Target address / Primary ID: RPM - Status ID</dd>
<b>$10</b>
<dd> Source address (ECM: Engine Control Unit)</dd>
<dd> <b>Remark:</b> Other source addresses: 40 (Display), 61 (Body Control)</dd>
</dl>

<dt>Message body</dt>
Target address and message body are specified in the SAE 2178-4 (Message Definition for Three Byte Headers).<br>
Primary IDs use to have Secondary ID that allow to have more detailed information. In the RPM example, the Primary ID ($1B) has 3:<br>

<dd> Sec ID 01 - Low resolution - PRN 1022</dd>
<dd> Sec ID 02 - High resolution - PRN 000C</dd>
<dd> Sec ID 20 - Idle RPM - PRN 1023</dd>
<br>
The PRN (Paremeter Reference Number) is a reference that is specified in this SAE 2178-4 for all the Secondary ID. With this PRN we will be able to go to the SAE 2178-2 (Data Parameter Definitions) and know how many bytes we will receive, which formula use to have a decimal value and which units we should expect.<br>

For example, if we look for PRN 000C (RPM - High Resolution), it will tell us that the units are RPM and the resoution is 1/4 (1bit=0,25 rpm). Therefore, if we receive the bytes <b>28 1B 10 02 0A F0</b> we will have:<br>

<dd><b>28 1B 10</b>: RPM Header</dd>
<dd><b>02</b>: Secondary ID for High Resolution RPM</dd>
<dd><b>0A F0</b>: RPM value. To calculate it we will do the following:<br> 
<dd>(byte0 * 0x100+byte1)/4= (0x0A * 0x100+0xF0)/4<br></dd>
<dd>(10 * 256+240)/4= (2560+240)/4= 2800/4= 700rpm</dd>
<br>

<dt>CRC (Cyclical Redundant Check)</dt>
It is 1 byte that comes after the message body and it has been obtained by the emitter through a mathematical formula. This number (CRC) is unique for this byte combination (Header + message body). When the receptor node has received all bytes through the bus, it also does this calculation using same formula and will obtain also a CRC. If received CRC and calculated CRC are the same, it means that there was no error during the message transmission-reception. Otherwise, the information of this message should not be taken into consideration.<br>

<dt>End of Data (EOD)</dt>
After the CRC, the bus will be left in passive mode during 200us. After the EOD, receptor nodes can answer the message or to send a new one.

<h3>DATA BITS:</h3>

Broadcasted information through the bus is based in 0s and 1s. This protocol has the characteristic that the broadcasted 1s and 0s can be active and passive.<br>
<dt>What does this mean?</dt>
It means that as the bus can be in active or passive mode (as explained above), nodes can transmit for example a 1 in active mode or in passive mode by changing only the transmiting time. Following table summarizes it:<br>

<center>
<img style="display:inline" src="/images/Part3/06.PNG" alt="Source: Xavier Morales"> 
<img style="display:inline" src="/images/Part3/07.PNG" alt="Source: Xavier Morales">
</center>
<br>

Example using the same 1st byte of the previous header (<b>0x28</b>: <b>0b</b>00101000):

<img src="/images/Part3/08.PNG" alt="Source: Xavier Morales">

As you can see, the bits alterante every time between active and passive. As the SOF forces the first state (active), the first bit of the header will be passive and the rest will start alternating. All the bits within the bytes of the message will be transmitted starting by the most significant bit, this means bit7, bit6,..., bit0.<br>

<b>Remark:</b> As you can see, a Passive 0 will always win a Passive 1 (0 is temporary shorter and therefore it will change to the next bit (active) sooner and therefore the passive 1 will loose arbitrariety). The same occurs with the Active 0, this is temporary longer than the Active 1.<br>

<h3>Specification tables</h3>

<img src="/images/Part3/09.PNG" alt="Source: Xavier Morales">

<h3> Physical Layer:</h3>
- 1-wire bus used to transmit 1s and 0s at a specified speed of 10,4 Kb/s through VPW. <br>
- Cable maximum length: 40m <br>
- Maximum number of nodes (Control Units): 32 <br>
- A 0 bit will always rule over a 1 bit<br>
- Maximum number of bytes in the message body: 12 <br>
<br>

<img src="/images/Part3/10.PNG" alt="Source: Xavier Morales">


<p>
<font size="2"> 
Project Index:<br>
<a href="/en/HD-tacho-part1">Part1 </a>/
<a href="/en/HD-tacho-part2"> Part2 </a>/
<a href="/en/HD-tacho-part3"> Part3 </a>/
<a href="/en/HD-tacho-part4"> Part4 </a>/
 Part5 /
 Part6 /
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
