---
type: posts
layout: post
lang: ca
comments: true
title: Com carregar una bateria de 12V de plom i àcid sense un carregador de bateries
name: carregarbateria
permalink: carregar-bat-plom-acid
category: plom-acid
keywords: carregar, cargar, bateria, batería, plom, plomo, àcid, ácido, cc, cv, corrent constant, voltatge constant, font d'alimentació, fuente de alimentación
---

A l'hivern és normal que les bateries sotmeses a baixes temperatures perdin prestacions (amb el fred les reaccions químiques són més lentes) i per això és important que, si la bateria no està ben aillada de l'exterior, ens assegurem que la tenim ben carregada. En aquest cas tenim la bateria d'un scúter que en circuit obert el multímetre llegeix 12.05V i per anar bé, hauríem de llegir uns 12.6V. Així que, anem a carregar-la.<br>

La manera més normal de carregar una bateria seria amb un carregador comercial però aquí a casa no en tenim. El que si que tenim és una font d'alimentació programable i amb això ara per ara en tindrem prou. Per poder procedir amb l'activitat, el més important és saber quin tipus de bateria disposem i en el nostre cas, és una bateria de plom i àcid. La manera de carregar aquest tipus de bateries és amb CC - CV (Constant Current - Constant Voltage), és a dir, Corrent Constant i després Voltatge Constant. En aquesta entrada no tocaré els temes de càrrega d'equalització o <i>floating</i> de les bateries.

<center>
<img style="display:inline" src="/images/161230-carregar-bat/graph1.jpg" width="49%" alt="Contingut: Diagrama de Corrent Constant - Voltatge Constant. Source: Momex.cat" title="CC-CV Diagram">
<img style="display:inline" src="/images/161230-carregar-bat/yuasa.jpg" width="29%" alt="Contingut: Yuasa YB4L-B. Source: Momex.cat" title="Bateria">
</center>

El gràfic superior bàsicament diu:<br>
1- Hi ha una primera fase on mantindrem el corrent constant (<b>Ia</b>) i això provocarà que el voltatge vagi incrementant.<br>
2- Quan el voltatge arribi a un valor determinat (<b>Va</b>) passarem a la segona fase, on mantindrem aquest voltatge constant (Va) i serà el corrent el que començarà a disminuir poc a poc fins a un valor (<b>Ib</b>) on ja podrem desconnectar la bateria.<br>
<!--more-->
<br>
Per no fer mal bé la bateria, quins són els valors que hauríem d'agafar? Doncs, primer, el millor és anar a veure què és el que diu el fabricant.<br>

<center>
<img style="display:inline" src="/images/161230-carregar-bat/spec1.jpg" width="39%" alt="Contingut: Especificació de Yuasa. Source: Momex.cat" title="Especificació de la bateria">
</center>

Veiem que ens hi indica <b>Ia</b> (0,4A o 400mA). Això coincideix amb el que he anat trobant a altres llocs web on fan referència a que un <i>slow charge</i> representa un 10% de la càrrega elèctrica (0.1C). Com la nostra bateria es de 4Ah, un 10% serien aquests 400mA.<br>
Respecte a <b>Va</b>, l'especificació del fabricant no en diu res. Segons aquest <a href="http://batteryuniversity.com/learn/article/charging_the_lead_acid_battery" target="_blank">web</a>, situen un valor genèric entre 13,8 i 14,7V i expliquen les conseqüències de cadascun. Un valor massa baix porta a una càrrega molt llarga i podria generar la sulfatació de la bateria. Un valor massa alt porta a la corrosió i emissió de gasos nocius.  Un valor entre 14,2 i 14,4V seria l'ideal.<br>
Per últim, <b>Ib</b>, veiem en el mateix web d'abans que situen el corrent a un 3% de la capacitat de càrrega (en el nostre cas seria al voltant de 120mA).<br>

Un cop amb totes aquestes dades ja podem procedir a configurar els límits Ia i Va a la nostra font d'alimentació. Degut a les limitacions d'aquesta, el valor Ib no es pot introduir, així que seré jo manualment qui apagarà la font i finalitzarà la càrrega. A continuació us deixo un <i>time-lapse</i> del procés:<br>

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/-KbkFs0-TaY" frameborder="0" allowfullscreen></iframe>
</center>

En total, unes 8 hores i mitja. Un cop recopilades les dades es poden mostrar en una gràfica com la següent:
<center>
<img style="display:inline" src="/images/161230-carregar-bat/realgraph.jpg" width="69%" alt="Contingut: Especificació de Yuasa. Source: Momex.cat" title="Especificació de la bateria">
</center>

Us deixo a continuació uns consells pràctics que he trobat interessants al web de Yuasa, <a href="http://www.yuasa.co.uk/info/technical/need-know-batteries/" target="_blank">Informació sobre bateries</a>.<br>
-Les bateries necessiten una recàrrega quan el voltatge en circuit obert és inferior a 12.4V<br>
-No carregar una bateria si la temperatura és inferior a 3ºC ja que l'electròlit podria estar congelat.<br>
-Qualsevol bateria per sota dels 11V hauria de ser descartada/reciclada ja que podria haver desenvolupat sulfatació que no es pot arreglar mitjançant posteriors càrregues.<br>
-No omplir d'aigua destilada fins al límit superior les bateries que hagin de ser carregades ja que els nivells pujen quan es carreguen.<br>
-Ajustar fins als nivells màxims només un cop la bateria hagi reposat un mínim d'1 hora després de la càrrega.<br>
-Utilitzeu només aigua destilada o desionitzada per omplenar la bateria. No utilitzar àcid sulfúric exepte si s'omplena la bateria per primer cop. L'ús d'aigua mineral podria generar que la bateria es descarregués degut a les impureses de l'aigua.<br>
-Ciclat sever: cada vegada que una bateria es carrega i es descarrega una petita part de material es perd. Si la bateria es sotmet a una descàrrega severa (35%) i posteriorment a una càrrega ràpida, el procés s'accelera.<br>
-Carregar a voltatges baixos (13,6-13,8V) pot generar sulfatació. Això pot passar quan el vehicle s'utilitza ocasionalment per a trajectes curts o l'activació del mateix <i>Start/Stop System</i> quan es circula per la ciutat.





