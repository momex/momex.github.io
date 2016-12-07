---
type: posts
layout: post
lang: ca
comments: true
title: Crear un Ubuntu USB Live amb persistència de fitxers
name: UbuntuUSBLive
permalink: Ubuntu-USB-Live-persistència
category: Ubuntu
keywords: crear, Ubuntu, USB, Live, persistència, fitxers, persistencia, ficheros
---

Avui m'he sorprès quan he descobert que l'aplicació nativa d'Ubuntu 16.04, l'<i>usb-creator-gtk</i>, el qual et permet crear un <i>USB Live</i> amb Ubuntu, ja no suporta l'opció de reservar un espai al disc per poder desar els teus fitxers i que no es perdin cada cop que s'apaga l'ordinador. 

<center>
<img style="display:inline" src="/images/161206-USBLive/livecreator02.jpg" width="40%" alt="Contingut: usb-creator-gtk amb slider. Source: Momex.cat" title="Abans, amb l'opció">
<img style="display:inline" src="/images/161206-USBLive/livecreator01.png" width="50%" alt="Contingut: usb-creator-gtk sense slider. Source: Momex.cat" title="Ara, sense l'opció">
</center>


Per sort, sempre hi ha altres opcions per acabar fent una mateixa feina i llegint aquest <a href="http://askubuntu.com/questions/841843/what-program-to-use-when-you-want-to-create-a-persistent-storage-live-usb-in-ubu" target="_blank">fil</a> del fòrum askubuntu.com he trobat el que buscava. Es tracta del programa <a href="https://help.ubuntu.com/community/mkusb" target="_blank">MKUSB</a>, amb una operativa similar a l'<i>usb-creator-gtk</i> i que permet fer exactament allò que necessitava. Per instal·lar-lo amb el terminal:<br>

{% highlight bash %}
sudo add-apt-repository ppa:mkusb/ppa
sudo apt-get update
sudo apt-get install mkusb usb-pack-efi
{% endhighlight %}

<!--more-->

Un cop instal·lat, el podrem buscar al menú d'aplicacions d'Ubuntu i un cop executat, el primer que farà serà demanar-nos el password de <i>superuser</i>. Un cop introduït, ens mostrarà una finestra de benvinguda i tot seguit el menú principal, que com veureu, és molt simple.<br> 

<center>
<img style="display:inline" src="/images/161206-USBLive/01.png" width="40%" alt="Contingut: Passes. Source: Momex.cat" title="Passes">
<img style="display:inline" src="/images/161206-USBLive/02.png" width="55%" alt="Contingut: Passes. Source: Momex.cat" title="Passes">
</center>

Per moure'ns en aquest menú simplement haurem de seleccionar l'opció que vulguem i tot seguit clicar l'OK. Per exemple, el primer pas serà escollir la imatge que volem gravar (<i>Select source -iso,img, ...</i>). Això ens portarà a una finestra que ens permetrà navegar pels directoris per seleccionar la nostra imatge. Tot seguit, podrem escollir si volem un USB Live amb (<i>persistent live</i>) o sense (<i>live only</i>) persistència. Cada vegada que cliquem l'OK l'opció de la persistència canviarà. Finalment, ja podrem cliclar a instal·lar i ens mostrarà una finestra amb un resum i unes advertències:
<center>
<img style="display:inline" src="/images/161206-USBLive/03.png" width="55%" alt="Contingut: Passes. Source: Momex.cat" title="Passes">
<img style="display:inline" src="/images/161206-USBLive/04.png" width="40%" alt="Contingut: Passes. Source: Momex.cat" title="Passes">
</center>

Cliquem <i>Select Target device in the next window</i> i ens permetrà escollir l'USB on gravar la imatge. Finalment, ens demanarà si estem segurs de tot ja que s'esborraran dades, clicarem la casella inferior i ja podrem donar al botó <i>Go</i>. Abans de començar el procés de gravació, ens demanarà quant d'espai de l'USB volem ocupar (0-100) ja que amb el que sobri crearà una partició per poder accedir-hi des d'altres sistemes operatius. Un cop definit, començarà a gravar i al cap d'uns minuts ja el tindrem llest.

<center>
<img style="display:inline" src="/images/161206-USBLive/05.png" width="40%" alt="Contingut: Passes. Source: Momex.cat" title="Passes">
<img style="display:inline" src="/images/161206-USBLive/06.png" width="40%" alt="Contingut: Passes. Source: Momex.cat" title="Passes">
</center>

