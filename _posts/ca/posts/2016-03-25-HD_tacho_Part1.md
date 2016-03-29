---
type: posts
layout: post
lang: ca
title: Tacómetre Digital per a Harley Davidson Sportster (Part 1 - Introducció)
name: HD-tacho-part1
permalink: HD-tacho-part1
category: tacho
keywords: HD, harley, davidson, tachometer, tacho, rpm, J1850, SAE
---

A l'hora de conduir un vehicle a tots ens venen al cap com a mínim un parell d'indicadors bàsics que ens donen una idea de la velocitat i de les revolucions (rpm) del motor. En camions o cotxes és habitual trobar molta més informació al quadre d'instruments però en una moto, generalment per motius d'espai, això va una mica més comprimit. Si bé hi ha models que incorporen els dos rellotges de velocitat i rpm, alguns els fusionen i passen a tenir un rellotge de rpm i un LCD on es mostra la velocitat.<br>
Quan passem a motos més econòmiques o a motors que no es revolucionen molt, la cosa es simplifica bastant. Els indicadors d'una Harley Davidson Sportster són molt bàsics. Consten d'un rellotge on s'indica la velocitat, uns quants testimonis lluminosos (benzina, avís d'error de motor,...) i un petit display LCD per mostrar els km totals, dos parcials i l'hora. 
<p>

<center><img src="/images/meter.png" alt="Contingut: HD Sportster Comptekilómetres. Source: Xavier Morales"></center>

Per a una persona obsessiva del control com jo, això obviament no era suficient, així que vaig proposar-me a llarg termini (gairebé 4 anys) dissenyar algun giny que em proporcionés un mínim d'informació extra; revolucions motor i quina marxa portava engranada <sub>(1)</sub>. <p>

L'electrònica era una cosa pendent a la meva <em>checklist</em> així que vaig proposar-me anar per feina. Com bàsicament tot el que he aprés prové del <a href="https://ca.wikipedia.org/wiki/Codi_obert" target="_blank">codi obert</a> / <a href="https://ca.wikipedia.org/wiki/Programari_lliure" target="_blank">programari lliure</a> (open source en anglés) i gràcies al moviment cultural del <a href="https://ca.wikipedia.org/wiki/Coneixement_lliure" target="_blank">coneixement lliure</a> vaig decidir fer aquest blog per retornar a la comunitat tot allò que he aprés. <br>

Dividiré aquest projecte en 12 parts, on aniré introduint els passos que he seguit, els circuits i esquemàtics, els codis, els dissenys, etc. 
<p>

<a href="/HD-tacho-part1/">Part 1 - Introducció </a> <br>
Part 2 - Bus de dades i sensors <br>
Part 3 - Harley Davidson i SAE J1850 VPW <br>
Part 4 - Disseny en paper i funcions <br>
Part 5 - Components principals <br>
Part 6 - Esquemàtic <br>
Part 7 - Disseny de la PCB <br>
Part 8 - Codi font i llibreries <br>
Part 9 - Disseny de la carcassa i suports <br>
Part 10 - Cablatge i Tests <br>
Part 11 - Cablatge i instal·lació a la moto <br>
Part 12 - Problemes durant el projecte <br>

<p>
<sub>(1) No us ha passat mai d'anar en 5ena i voler pujar una marxa més?</sub>
