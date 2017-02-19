---
type: posts
layout: post
lang: ca
comments: true
title: Alimentar l'emisor del Wattson amb una bateria de 12V
name: EmisorWattson
permalink: Alimentar-wattson-emisor
category: wattson
keywords: kyoto, DIY, Wattson, emisor, alimentar, bateria, emisor, power, supply, emitter, batery, pcb
---

Un dels gadgets més interessants que hi ha a casa és el Wattson, un monitor i comptador de potència que permet saber quina potència instantània s'està consumint i cada 5 minuts fa una mitjana que enmagatzema a la memòria interna. Aquestes dades (pot enmagatzemar fins a un màxim de 28 dies i després comença a sobre escriure'ls) es poden descarregar en format *.csv i això facilita la visualització posterior amb qualsevol full de càlcul. El conjunt consta d'un emisor que s'ha de col·locar al quadre de comptadors on hi tenim els magneto-tèrmics i un receptor que mostra les lectures cada x segons. Però bé, tot això ja ho explicaré en una altra entrada més endavant.<br>

<center>
<img style="display:inline" src="/images/161208-wattson-emitter/00.jpg" width="49%" alt="Contingut: DIY Kyoto Wattson. Source: Momex.cat" title="DIY Kyoto Wattson">
<img style="display:inline" src="/images/161208-wattson-emitter/01.jpg" width="49%" alt="Contingut: Emisor del Wattson. Source: Momex.cat" title="Emisor del Wattson">
</center>

Aquesta entrada la vull centrar en com alimentar l'emisor si no volem utilitzar les dues opcions disponibles que tenim, les 4 piles LR6 AA d'1,5V o una font d'alimentació 9V DC.<br>

Fa poc vaig canviar la bateria de la moto ja que tenia 5 anys, dels quals els últims 2 he utilitzat la moto molt poc i la bateria s'ha passat molt de temps a voltatges baixos. Després de jugar amb ella i amb les fonts d'alimentació que vam arreglar en aquesta <a href="http://momex.cat/reparaci%C3%B3-agilent-E3644A" target="_blank">entrada</a>, vaig veure que la bateria un cop carregada no em donaria la suficient seguretat com per a reinstal·lar-la a la moto, però si que em permetria alimentar alguns aparells temporalment.<br>
Total, després de 3 mesos amb la bateria pel mig sense cap idea al cap de què fer amb ella, el Wattson va començar a donar senyals per canviar les piles de l'emisor i se'm va ocórrer d'utilitzar la bateria de la moto per alimentar l'emisor (si, a això se li diu <a href="http://aplicacions.llengua.gencat.cat/llc/AppJava/index.html;jsessionid=0540C7002C73B888E2832F079B0FCE3E?action=Principal&method=detall&input_cercar=matar+mosques+a+canonades+&numPagina=1&database=FITXES_PUB&idFont=11434&idHit=11434&tipusFont=Fitxes+de+l%27Optimot&numeroResultat=1&databases_avansada=&categories_avansada=&clickLink=detall&titol=Com+es+diu+matar+moscas+a+ca%F1onazos+en+catal%E0%3F+%2F+%C9s+correcte+matar+mosques+a+canonades+en+catal%E0%3F&tematica=&tipusCerca=cerca.normes" target="_blank">matar mosques a canonades</a>).
<!--more-->
<br>
Però un moment, 4 x 1,5V són 6V i el connector per la font d'alimentació diu 9V DC... connectar una bateria de 12V no pot fregir algun component? L'experiència em diu que val més no provar aquestes coses perquè sempre acaben malament, així que tocarà obrir l'emisor i veure quins components duu a la PCB i quina és l'especificació del regulador de voltage.<br> 

<center>
<img style="display:inline" src="/images/161208-wattson-emitter/02.jpg" width="49%" alt="Contingut: Interior emisor wattson. Source: Momex.cat" title="Interior emisor wattson">
<img style="display:inline" src="/images/161208-wattson-emitter/03.jpg" width="49%"  alt="Contingut: Interior emisor wattson. Source: Momex.cat" title="Interior emisor wattson">
</center>

Només desmuntar l'aparell ja veiem dues coses:<br>
- Els pols + i - de l'opció alimentació amb piles o alimentació amb font 9V DC estan connectats. Bona noticia ja que implica un disseny més senzill i menys feina per a nosaltres.<br>
- Com a curiositat, hi ha una etiqueta on podem intuir una data: 130828 (28 d'Agost del 2013?). Mirant els altres 2 <a href="https://ca.wikipedia.org/wiki/Circuit_integrat" target="_blank">CI</a> que hi ha a la PCB, les dates de fabricació són 1328 (Juliol 2013) i 1226 (Juny 2012). Fent una mica d'arqueologia a google, DIY Kyoto va començar al voltant del 2006 (&#xB1; 1 any) i al voltant del 2015 va tancar de cop.
<center>
<img src="/images/161208-wattson-emitter/04.jpg" width="70%"  alt="Contingut: Interior emisor wattson. Source: Momex.cat" title="Interior emisor wattson">
</center>

Donant la volta a la PCB veiem que hi ha un microcontrolador central (SIL C8051F330) de Silicon Labs, les 4 entrades de les pinces amb els seus acondicionadors, una PCB petita amb el mòdul de l'antena, el botó central per canviar de modes i un regulador de voltatge en format <a href="https://en.wikipedia.org/wiki/TO-92" target="_blank">TO-92</a>.

<center>
<img style="display:inline" src="/images/161208-wattson-emitter/05.jpg" width="49%" alt="Contingut: Interior emisor wattson. Source: Momex.cat" title="Interior emisor wattson">
<img style="display:inline" src="/images/161208-wattson-emitter/06.jpg" width="49%" alt="Contingut: Interior emisor wattson. Source: Momex.cat" title="Interior emisor wattson">
</center>

El regulador és de la casa Microchip (<a href="http://ww1.microchip.com/downloads/en/DeviceDoc/22008E.pdf" target="_blank">MCP1702T-3302E</a>) i en concret és un <i>Lineal LDO (<a href="https://en.wikipedia.org/wiki/Low-dropout_regulator" target="_blank">Low DropOut</a>)</i>, és a dir, proporciona un voltatge fix encara que el voltatge d'entrada sigui molt pròxim al de sortida. Algunes especificacions d'aquest model en concret:<br>
• 2.0 μA Quiescent Current (typical)<br>
• Input Operating Voltage Range: 2.7V to 13.2V <br>
• Low Dropout (LDO) Voltage (625 mV typical @ 250 mA (VOUT = 2.8V))<br>
• Output Voltage 3.3V<br>
• Short-Circuit Protection<br>
• Overtemperature Protection<br>

A més a més, hi ha un doble diode (WV3) en format SOT23 que serveix com a protecció en cas de polaritat inversa. Aquest diode té una caiguda de voltatge d'aproximadament 0,231V.<br>
En resum, el màxim voltatge teòric amb el que podríem alimentar aquest emisor seria amb 13,4V (13,2V+0,23V), així que una bateria de moto seria una candidata perfecta per alimentar l'emisor i, tenint en compte el baix consum que té aquest emisor, trigarà molt de temps en descarregar-se.


