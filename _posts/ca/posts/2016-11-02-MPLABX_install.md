---
type: posts
layout: post
lang: ca
comments: true
title: Instal·lació MPLAB X IDE a Ubuntu i problemes amb PICKIT3
name: MPLABX-Ubuntu-Pickit3
permalink: MPLABX-Ubuntu-Pickit3
category: Microchip
keywords: MPLABX, MPLAB, Ubuntu 16.04, Windows, XP, Pickit3, firmware, actualització
---

Fins a dia d'avui he sigut usuari d'<i>MPLAB IDE</i> v8.43 sota <i>Windows XP</i> ja que des de que vaig començar amb això de la programació de <i>PIC</i>s mai m'havia molestat a actualitzar el <i>software</i>. Fins i tot quan va apareixer l'<i>MPLAB X IDE</i> em vaig resistir a canviar-lo ja que això dels canvis d'interfície em porten boig. Els anys han passat i mica en mica he aconseguit migrar totes les aplicacions a <i>Linux/Ubuntu</i>, excepte amb el <i>MS Excel</i> que encara m'hi resisteixo. Així doncs, ara li tocava el torn a l'<i>MPLAB</i> ja que no podia ser que haguès de reiniciar i canviar d'OS cada vegada que volia programar algun micro controlador.<br>

<center>
<img style="display:inline" src="/images/161102-MPLAB/mplablogo.jpeg" width="20%" alt="Contingut: MPLAB IDE Logo. Source: Microchip" title="MPLAB IDE Logo">
<img style="display:inline" src="/images/161102-MPLAB/mplabxlogo.png" width="20%" alt="Contingut: MPLAB X IDE Logo. Source: Microchip" title="MPLAB X IDE Logo">
</center>


La veritat és que la instal·lació va ser més fàcil del que m'esperava. A la part inferior del web d'<a href="http://www.microchip.com/mplab/mplab-x-ide" target="_blank">MPLAB X IDE</a> hi ha una pestanya de descàrregues i allà t'hi pots baixar el fitxer <i>MPLABX-v3.45-linux-installer.tar</i> (a data 2 de Novembre de 2016) que conté un fitxer *.sh de gairebé 550MB. Només fa falta descomprimir-lo i executar-lo com a super usuari:<br>

{% highlight bash %}
sudo ./MPLABX-v3.45-linux-installer.sh
{% endhighlight %}

<!--more-->

I ara a seguir les instruccions:<br> 

<center>
<img style="display:inline" src="/images/161102-MPLAB/01.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/02.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

<center>
<img style="display:inline" src="/images/161102-MPLAB/03.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/04.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

<center>
<img style="display:inline" src="/images/161102-MPLAB/05.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/06.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

<center>
<img style="display:inline" src="/images/161102-MPLAB/07.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/08.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

Com es veu a l'última imatge de la instal·lació, ens recomana uns <i>links</i> per anar a buscar i descarregar el compilador. La primera sorpresa que m'emporto és que a Linux no tindrem el compilador C18 com a Windows, sinó un anomenat XC8. No és que sigui un fanàtic del C18, però això de canviar de compilador, de ben segur, em portarà problemes amb la portabilitat dels codis que ja tinc escrits.<br>

Total, en <a href="http://www.microchip.com/mplab/compilers" target="_blank">aquest link</a>, a la part d'abaix, hi trobareu una altra pestanya on baixar-vos el compilador i un parell més de fitxer que poder ser interessants.<br>

- MPLAB® XC8 Compiler v1.38<br>
- Latest Part Support Patch Files: MPLAB® XC8 Compiler Part-Support Patch v1.38 (segons el web, afegeix nova informació específica sense canviar la base del compilador)<br>
- 8-bit MCUs: MPLAB Code Configurator: ens portarà a una altra pàgina web (dins del web de Microchip) on ens explicarà les característiques meravelloses de l'MCC. Hi ha l'opció de no baixar el fitxer des del web i fer-ho directament des del programa a la part de <i>Plugins</i>.<br>
- Al mateix web d'MCC, també ens podem descarregar la llibreria de dispositius (fitxer PIC10/PIC12/PIC16/PIC18_v1.16.jar).

Per continuar amb la instal·lació, simplement hem de canviar l'opció que permet als 2 fitxers *.run ser executables (botó dret, propietats i a la pestanya Permisos, clickar l'opció que diu "Permet executar aquest fitxer com a un programa"). A continuació amb un:

{% highlight bash %}
sudo ./xc8-v1.38-full-install-linux-installer.run
{% endhighlight %}

I ara a seguir les instruccions:<br> 

<center>
<img style="display:inline" src="/images/161102-MPLAB/XC01.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/XC02.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

<center>
<img style="display:inline" src="/images/161102-MPLAB/XC03.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/XC04.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

<center>
<img style="display:inline" src="/images/161102-MPLAB/XC05.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/XC06.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

<center>
<img style="display:inline" src="/images/161102-MPLAB/XC07.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/XC08.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

<center>
<img style="display:inline" src="/images/161102-MPLAB/XC09.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/XC10.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

I passem al fitxer de suport que l'instal·larem igual:

{% highlight bash %}
sudo ./xc8-v1.38-part-support-linux-installer.run
{% endhighlight %}

I ara a seguir les instruccions:<br> 

<center>
<img style="display:inline" src="/images/161102-MPLAB/XCS01.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/XCS02.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

<center>
<img style="display:inline" src="/images/161102-MPLAB/XCS03.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/XCS04.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

<center>
<img style="display:inline" src="/images/161102-MPLAB/XCS05.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/XCS06.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

Per instal·lar el <i>MCC</i>, nosaltres ens hem baixat el fitxer *.nbm i per instal·lar-lo hem d'anar a <i>Tools/Plugins</i>, afegir el fitxer i instal·lar-lo clicant el botó <i>Install</i>. Per adjuntar la seva llibreria de dispositius, haurem d'anar a <i>Tools/Options</i> buscant la pestanya <i>Embeded</i>, buscarem la subpestanya <i>MPLAB Code Configurator 3.0</i> i allà hi trobarem un botó anomenat <i>"Add Library"</i>.

<center>
<img style="display:inline" src="/images/161102-MPLAB/MCC01.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/MCC02.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

<center>
<img style="display:inline" src="/images/161102-MPLAB/MCC03.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/MCC04.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

<center>
<img style="display:inline" src="/images/161102-MPLAB/MCC05.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/MCC06.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

<center>
<img style="display:inline" src="/images/161102-MPLAB/MCC07.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/MCC08.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

<center>
<img style="display:inline" src="/images/161102-MPLAB/MCC09.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/MCC10.png" width="49%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

I fins aquí, en principi, tot el que necessitarem per començar a jugar amb l'<i>MPLAB X IDE</i> a <i>Linux/Ubuntu</i>. Per arrencar el programa només haurem de teclejar al terminal:<br>
{% highlight bash %}
sudo mplab_ide
{% endhighlight %}

Si l'únic que volem és reprogramar un <i>PIC</i> amb un *.hex ja existent, podem arrencar el substitut del <i>Pickit 3 Programmer Application</i>:
{% highlight bash %}
sudo mplab_ipe
{% endhighlight %}


## Problemes després de la instal·lació

Per seguir una mica amb el tema, em vaig trobar alguns "problemes" que vaig sol·lucionar així:<br>

- <u>Errors al compilar per falta d'includes</u>: D'alguna manera semblava que havia d'indicar manualment el <i>path</i> dels directoris que contenien els fitxers *.h. A la icona "Project Properties", podrem introduir manualment aquests <i>paths</i>.
<center>
<img style="display:inline" src="/images/161102-MPLAB/Project Properties icon.png" width="20%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/Comp_includes01.png" width="40%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/Comp_includes02.png" width="35%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

- <u><i>MPLAB X IDE</i> omple la carpeta de logs</u>: tot i que es pot configurar per desactivar-ho a <i>Tools/Options</i>, pestanya <i>Embeded</i> i subpestanya <i>Diagnostics (Logging Level OFF)</i>, el programa segueix fent de les seves. Buscant per internet vaig trobar una sol·lució bastant intel·ligent, només fa falta canviar el directori a <i>/dev/null</i>. Copy/paste del viquipedia:<br>
<i>En sistemes operatius tipus Unix, /dev/null o perifèric nul (null device) és un fitxer especial que descarta tota la informació que s'escriu o redirecciona en ell. Al seu torn, no proporciona cap dada a qualsevol procés que intenti llegir d'ell, tornant simplement un EOF o fi de fitxer.</i><br>

- <u>Versió del <i>firmware</i> del <i>Pickit 3</i> massa antiga</u>: aquí si no hi he perdut 3 hores, no n'hi he perdut cap. L'<i>MPLAB X IDE</i> em llençava un codi com aquest:<br>
<i>Your PICkit 3 firmware version is too old. You must have firmware version 01.26.00 or higher to use MPLAB X. Connection Failed.</i><br>
Total, no hi havia manera de que el sistema baixés un <i>firmware</i> automàticament..ni amb l'<i>IDE</i> ni amb l'<i>IPE</i>. Així que he reculat i he tornat al <i>MPLAB</i> antic, l'he actualitzat a l'última versió disponible (v8.92) i allà he aconseguit poder instal·lar una versió posterior...fiuuu <br>
<center>
<img style="display:inline" src="/images/161102-MPLAB/MPLAB01.png" width="35%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/MPLAB02.JPG" width="30%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>

<center>
<img style="display:inline" src="/images/161102-MPLAB/MPLAB03.JPG" width="35%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/MPLAB04.JPG" width="30%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
<img style="display:inline" src="/images/161102-MPLAB/MPLAB05.JPG" width="30%" alt="Contingut: Passos. Source: Momex.cat" title="Passos">
</center>


