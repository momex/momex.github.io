---
type: posts
layout: post
lang: ca
comments: true
title: Tacòmetre Digital per a Harley Davidson Sportster (Part 6 - Disseny i funcions)
name: HD-tacho-part6
permalink: HD-tacho-part6
category: tacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, disseny, funcions
---

Aquesta part la dividiré en 2 seccions i en cadascuna resumiré les parts més importants.

### Disseny conceptual

Després de veure què és el que més m'ha agradat de l'estudi de mercat, què és el que puc arribar a fer i coneixent les meves limitacions tant teòriques com de fabricació, ve't aquí les conclusions i decisions:<br>
- <b>2 rellotges</b>: Això em permetrà seguir mantenint el rellotge de sèrie amb les seves funcions corresponents i la informació important com els kilòmetres totals.<br>
- <b>Simplificació</b>: utilitzaré el suport 67338-97 per a 2 rellotges que ve amb el Kit de tacòmetre 67182-07. Per ebay de tant en quan en venen de 2ona mà. Amb això, la forma i els tamanys de la PCB (&#8709;85mm) i carcassa (&#8709;90mm) ja venen delimitats.<br>
- El <b>cablejat</b> també el podria comprar per ebay (68811-07), però resultaria més econòmic si me'l fes jo mateix. Al cap i a la fi, necessito mínim 3 cables (+12V, Massa i bus J1850) i cap connector específic.<br>
- <b>Elements indicatius</b>: 7-segments i LEDs.<br>
- <b>Caràtula</b>: impresió en vinil o similar.

La idea vindria a ser quelcom similar a la unió d'aquests dos models:<br><center>
<img style="display:inline" src="/images/Part6/proto-disseny1.png" width="30%" alt="HD Sportster Tacòmetre. Source: Harley Davidson" title="HD Sportster amb doble rellotge">
<img style="display:inline" src="/images/Part6/proto-disseny.jpg" width="40%" alt="Esbós. Source: Xavier Morales" title="Esbós">
</center>
<!--more-->

### Funcions principals

- <b>RPM:</b> Valor llegit del bus de dades i mostrat als 4x7-segments. Aquest senyal té una resolució d'1 RPM i s'actualitza unes quantes vegades per segon, per tant, s'ha de programar el codi per tal de que no molesti a la vista. <br>
- <b>Indicador de marxa:</b> Valor llegit del bus de dades i mostrat al 7-segments situat a la part inferior. Aquest 7-segments sempre mostrarà aquest valor. <br>
- <b>Consum:</b> Valor llegit del bus de dades i mostrat als 4x7-segments.<br>
- <b>Temperatura de motor:</b> Valor llegit del bus de dades. <br>
- <b>Barra d'RPM:</b> Quan les funcions de mostrar el consum o temperatura del motor estiguin activades, les RPM es mostraran en aquesta barra de LEDs. Es pot programar codi per incloure efectes lluminosos. <br>
- <b>Botó posterior:</b> Per canviar de mode, el sistema incorporarà un botó a la part posterior.
- <b>Lluminositat:</b> Al ésser 7-segments i LEDs, la visibilitat dependrà totalment de la lluminositat exterior. Si la intensitat lluminosa dels LEDs fos constant, de nit podríem tenir problemes ja que ens il·luminaria massa. Per tant s'incorporarà una funció per poder variar la lluminositat utilitzant el botó posterior.

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
 Part10 /
 Part11 /
 Part12 /
 Part13 /
 Part14
 </font>
</p>
