---
type: posts
layout: post
lang: ca
comments: true
title: Com utilitzar un domini propi a Github pages quan el teu proveïdor deshabilita la Gestió de DNS?
name: GestioDNS
permalink: gestio-DNS-alternativa
category: jekyll
keywords: Jekyll, github, github-pages, web, estàtic, Gestió de DNS, proveïdor, deshabilitat, cdmon, swhosting
---

L'altre dia em vaig emportar una desagradable sorpresa quan estava creant un nou lloc web. Resulta que el meu proveïdor de domini (swhosting) va decidir canviar les condicions dels serveis contractats i l'apartat "Gestió de DNS" deixava d'estar inclòs en el servei bàsic <i>Hosting Micro</i> i si el volia incloure havia de pagar adicionalment 9,5€/any. Sembla ser que van enviar una circular que jo no vaig llegir/trobar (per descomptat, els hi concediré el benefici del dubte). La part interessant és que la publicitat al seu web no l'han canviat com tocaria i em van generar confusió amb la frase "Serveis gratuïts inclosos - Gestió de DNS" que es segueix anunciant com es feia fa 1, 2 i 3 anys. Sembla ser que la combinació de paraules "Gestió de DNS" de <a href="https://www.swhosting.com/blog/ca/el-cat-per-648e-el-domini-cat-mes-barat/" target="_blank">Desembre de 2013</a> i la d'<a href="https://www.swhosting.com/ca/dominios" target="_blank">avui, Juny 2017</a>, no volen dir el mateix i per tant, no inclouen el mateix... 3 tipus de queixes enviades a atenció al client (mur, tiquet administratiu i telf) i tres respostes que no m'ajuden en res. La sol·lució és molt fàcil, només han d'especificar que la modificació de registres s'ha de contractar per separat. Total, aquí deixo reflexada la meva total insatisfacció com a client que s'ha sentit enganyat i han passat olímpicament d'ell. <sup>(1)</sup><br>

En definitiva, un cop ja tenim el domini fet i no podem canviar els registres de les DNS (A, MX, CNAME...), com podem enllaçar el nostre domini a <i>Github</i>? Si mirem la llista que ofereix <a href="http://fundacio.cat/ca/domini/comparativa-de-preus" target="_blank">la fundació.cat</a> veiem que un 80% de les empreses que ofereixen el domini .cat també ofereixen la Gestió de DNS. Una per una anem mirant fins que topem amb una empresa anomenada <a href="https://www.cdmon.com/ca/" target="_blank">CDMON</a> que només registrant-se com a usuari ens ofereixen el servei de Gestió de DNS gratuït. Per cert, al web de la fundació ho tenen més clar que els mateixos de swhosting..<br>

<center>
<img src="/images/170611-DNS/01.jpg" width="80%" alt="Contingut: Llista de la fundació.cat. Source: Fundació.cat">
</center>

## Passos

## 1- Mudar les nostres DNS / <i>Domain Name System</i>

Una cosa que encara no han deshabilitat a swhosting és el poder canviar el que ells anomenen "Dades de DNS" o els noms dels servidors de DNS pel nostre domini (sí, això és el que ells anomenen Gestió de DNS a 2017). Així doncs, el primer que haurem de fer és canviar aquestes DNS per les de <i>CDMON</i>.
<!--more-->
<center>
<img style="display:inline" src="/images/170611-DNS/02.jpg" width="47%" alt="Contingut: DNS a swhosting. Source: Momex.cat">
<img style="display:inline" src="/images/170611-DNS/03.jpg" width="47%" alt="Contingut: Canvi DNS a CDMON. Source: Momex.cat">
</center>

## 2 - Generar els registres "A" apuntant cap a <i>Github</i>
Ara només toca anar al panell de control de cdmon i crear els registres "A" apuntant cap a <i>Github</i>, tal i com vam explicar <a href="/jekyll-install-part5">aquí</a>.


<center>
<img style="display:inline" src="/images/170611-DNS/04.jpg" width="98%" alt="Contingut: Registres A creats al panell de control de CDMON apuntant a Github. Source: Momex.cat">
</center>

## 3 - Crear el registre "MX" per al correu
Si no el creem, podrem enviar emails des del nostre correu però no en podrem rebre. Per tant, com abans, procedirem a crear-lo amb el nom del servidor que trobarem al nostre panell de control de swhosting, secció detalls del servei de correu.

<center>
<img style="display:inline" src="/images/170611-DNS/05.jpg" width="98%" alt="Contingut: Registre MX creat al panell de control de CDMON apuntant a Github. Source: Momex.cat">
</center>
<br>

<sup>(1)</sup><font size="3"> Només per aclarir-ho una mica més. Estic a favor de pagar pels serveis, com és lògic, però no estic a favor de fer publicitat "poc clara" i que una empresa permeti que els seus client es sentin enganyats.</font>

