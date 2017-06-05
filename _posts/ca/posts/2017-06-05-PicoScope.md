---
type: posts
layout: post
lang: ca
comments: true
title: Reparació d'un oscil·loscopi USB - PicoScope 4227
name: PicoScope4227
permalink: reparació-PicoScope-4227
category: reparació
keywords: reparació, repair, Scope, Oscil·loscopi, Osciloscopio, PicoScope, 4227, 100MHz
---

L'altre dia va arribar a les meves mans un oscil·loscopi <i>USB</i> que no funcionava prou interessant com per intentar esbrinar què li passava. Era un <a href="https://www.picotech.com/download/datasheets/PicoScope4226_7Datasheet.pdf" target="_blank">PicoScope 4227</a> (100MHz, 2ch, 250MS/S) i el problema era desconegut.<br>

<center>
<img style="display:inline" src="http://www.picoscope.nl/oscilloscopen/4226-4227.jpg" width="50%" alt="Contingut: PicoScope 4227. Source: PicoScope.nl">
<img style="display:inline" src="/images/170605-Picoscope/Spec.jpg" width="40%" alt="Contingut: Especificació PicoScope4227. Source: Momex.cat">
</center>

Molts cops, per saber per on començar la reparació, el millor és engegar l'aparell per veure si el seu comportament ens pot donar algunes pistes. Altres vegades, és millor no fer-ho si l'aparell fa olor a cremat o el fusible ha fallat. En aquests casos, el millor és obrir l'aparell i començar per donar una ullada per trobar parts defectuoses. En el nostre cas, com no fa olor i l'alimentació ve donada per l'USB de l'ordinador (protecció contra curts), el millor és connectar-ho i veure que passa.<br>

<!--more-->
<center>
<img style="display:inline" src="/images/170605-Picoscope/02.jpg" width="45%" alt="Contingut: Canal B al programa PicoSocpe. Source: Momex.cat">
<img style="display:inline" src="/images/170605-Picoscope/01.jpg" width="45%" alt="Contingut: Font d'alimentació Agilent E3644A. Source: Momex.cat">
</center>

Potser la imatge és massa petita, però el problema està bastant clar. Al connectar l'oscil·loscopi a l'ordinador per l'<i>USB</i>, el sistema operatiu el reconeix a la primera i això són molt bones noticies perquè podrem descartar una bona part de l'esquemàtic. Després d'executar el programa <i>PicoScope</i> veig que la comunicació és igual de bona. Un altre punt interessant i definitiu que ens ajudarà a fer les primeres comprovacions és que tots dos canals sempre donen 0V encara que s'estigui subministrant 5V amb la font d'alimentació programable. Res més a dir, tocarà obrir l'aparell i fer una inspecció visual, però fa pudor a fusible.<br>

<center>
<img style="display:inline" src="/images/170605-Picoscope/03.jpg" width="49%" alt="Contingut: PicoScope 4227 PCB. Source: Momex.cat">
<img style="display:inline" src="/images/170605-Picoscope/04.jpg" width="49%" alt="Contingut: Connectors BNC cremats. Source: Momex.cat">
</center>

Ja ho tenim!. A la imatge de la dreta es pot veure com la carcassa blanca dels connectors dels dos canals tenen un color cremat poc normal. Si ens hi fixem més veurem que el pin corresponent a la massa està cremat..en tots 2 canals!. Anem a fer la prova per veure si hi ha algun problema més com passa de vegades. Soldem un cable al pin cremat i fem el connexionat amb la font d'alimentació proporcionant diferents voltatges (a la foto 7V).<br>

<center>
<img style="display:inline" src="/images/170605-Picoscope/05.jpg" width="31%" alt="Contingut: Conexionat per comprovar que funciona. Source: Momex.cat">
<img style="display:inline" src="/images/170605-Picoscope/06.jpg" width="67%" alt="Contingut: PicoScope mostrant 7V com a la PSU. Source: Momex.cat">
</center>

Perfecte! Ara ja podem procedir a comprar un parell de connectors nous (aprox 5€ cadascun) per cambiar-los i ja ho tindrem com nou. <br>
<center>
<img style="display:inline" src="/images/170605-Picoscope/07.jpg" width="45%" alt="Contingut: Connector BCN 90º per PCB. Source: Momex.cat">
</center>

La causa arrel d'aquest problema és bastant clara i molt comú en oscil·loscopis. Molts cops, els que utilitzen aquest aparells no saben que les masses dels canals estan comunicades i que cada canal ens donarà el nivell de voltatge relatiu a la mateixa referencia de massa. Això vol dir que qui va utilitzar l'aparell per últim cop va connectar les masses dels dos canals a dos punts amb voltatges diferents creant un curtcircuit. Per sort, només els pins es van cremar i té fàcil reparació.
