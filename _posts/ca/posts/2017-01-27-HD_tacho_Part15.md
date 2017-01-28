---
type: posts
layout: post
lang: ca
comments: true
title: Tacòmetre Digital per a Harley Davidson Sportster (Part 15 - Problemes durant el projecte i millores)
name: HD-tacho-part15
permalink: HD-tacho-part15
category: tacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, SAE, millores, projecte, errors, problemes
---
<p>
<font size="2"> 
<a href="/HD-tacho-part1">Part1 </a>/
<a href="/HD-tacho-part2"> Part2 </a>/
<a href="/HD-tacho-part3"> Part3 </a>/
<a href="/HD-tacho-part4"> Part4 </a>/
<a href="/HD-tacho-part5"> Part5 </a>/
<a href="/HD-tacho-part6"> Part6 </a>/
<a href="/HD-tacho-part7"> Part7 </a>/
<a href="/HD-tacho-part8"> Part8 </a>/
<a href="/HD-tacho-part9"> Part9 </a>/
<a href="/HD-tacho-part10"> Part10 </a>/
<a href="/HD-tacho-part11"> Part11 </a>/
<a href="/HD-tacho-part12"> Part12 </a>/
<a href="/HD-tacho-part13"> Part13 </a>/
<a href="/HD-tacho-part14"> Part14 </a>/
<b> Part15 </b>
 </font>
</p>

<b>Problemes:</b><br>
- El primer i principal, com dimonis ho faig? aquest era el primer projecte d'aquesta magnitut amb el que m'enfrontava i havia de pensar com fer pràcticament tot.<br>
- Els transceptors (<i>trasnceiver</i> en anglès) per J1850 VPW estaven descontinuats des de feia anys. Per sort, en vaig trobar 3 a l'eBay i vaig poder fer una unitat de control <i>dummy</i> (de mentira) emisora de senyals pel bus de dades. Pel disseny final, però, vaig optar per utilitzar un parell de transistors i resistències.<br>
- La falta d'experiència a l'hora de soldar components <i>SMD</i> em va portar a perdre un parell de <i>PCB</i>s. Per sort, sempre començava a soldar aquells components més complicats, en aquest cas, el <i>driver</i> dels 7 segments i <i>LED</i>s.<br>
- Vaig patir bastants problemes a les <i>PCB</i>s, bàsciament degut a males soldadures, que em van fer perdre setmanes senceres i també la il·lusió per continuar el projecte. Per example, per culpa d'una resistència mal soldada (micro fractura i per tant falta de continuïtat) pensar que era un problema de software i després d'una setmana diagnosticant a estones, quan ja vas a tirar la tovallola, comences a tocar els components amb el dit i comença a funcionar com era d'esperar.<br>
- Equipaments de mesura bastant precaris o fonts d'alimentació provinents d'un ordinador amb sortida fixa a 12V. De totes maneres, com heu vist, aquestes eines les vaig anar comprant a mesura que les necessitava. He de dir que han sigut una de les millors inversions que he fet. També he de dir que amb equipament més senzill també hauria pogut acabar el projecte (un soldador galdós, un multimetre Vichy VC99, una font d'alimentació d'ordinador i un <i>logic analyzer</i> de 15€ en comptes d'un oscil·loscopi).<br>

<br>

<b>Millores:</b><br>
- El <i>software</i> encara té algunes errades. Per exemple: alugnes vegades apareixen números que no tocaria a l'indicador de marxa. <br>
- Implementar la funció del consum de benzina que actualment està en blanc. <br>
- La lluminositat es pot reduir o augmentar a gust de l'usuari, però la lluminositat de l'indicador de marxa és fixa i per la nit pot molestar una mica.<br>
- Els <i>LED</i>s utilitzats per la barra d'RPM o per l'indicador de mode no es veuen a plena llum del dia.<br>
- Amb el sol il·luminant per darrera no es veuen els 7 segments encara que estiguin a plena potència.<br>
- El botó posterior a vegades no respon bé. Podria ser <i>software</i>, però jo em decanto més per una mala fixació del botó a la carcassa que genera falsos contactes als terminals del botó.<br>
- La carcassa impresa en 3D la milloraria en molts sentits, per exemple, formes específiques per bloquejar la <i>PCB</i> internament. Un disseny intel·ligent és la clau per notar la qualitat d'un producte durant el seu funcionament. Una altra millora relacionada amb la carcassa seria la de millorar la impermeabilitat o la ventilació correcta per evitar humitats a l'interior.<br>
- Crear un vinil decent per posar a la caràtula. Actualment vaig amb una impresió en paper que va començar a arrugar-se durant el meu viatge als Alps Suïssos (tots els dies amb pluja).


<br>
I fins aquí aquest meravellós projecte. Qualsevol pregunta, deixeu-la als comentaris o envieu-me un correu.
Salut

<center>
<img src="/images/Part14/04.png" width="80%" alt="Contingut: vista del tacòmetre digital. Source: Momex.cat" title="Vista del tacòmetre digital">
</center>

<p>
<font size="2"> 
<a href="/HD-tacho-part1">Part1 </a>/
<a href="/HD-tacho-part2"> Part2 </a>/
<a href="/HD-tacho-part3"> Part3 </a>/
<a href="/HD-tacho-part4"> Part4 </a>/
<a href="/HD-tacho-part5"> Part5 </a>/
<a href="/HD-tacho-part6"> Part6 </a>/
<a href="/HD-tacho-part7"> Part7 </a>/
<a href="/HD-tacho-part8"> Part8 </a>/
<a href="/HD-tacho-part9"> Part9 </a>/
<a href="/HD-tacho-part10"> Part10 </a>/
<a href="/HD-tacho-part11"> Part11 </a>/
<a href="/HD-tacho-part12"> Part12 </a>/
<a href="/HD-tacho-part13"> Part13 </a>/
<a href="/HD-tacho-part14"> Part14 </a>/
<b> Part15 </b>
 </font>
</p>
