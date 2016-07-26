---
type: posts
layout: post
lang: ca
comments: true
title: Com crear un lloc web econòmicament per menys de 6€ amb Github i Jekyll - Part4
name: jekyll-install-Part4
permalink: jekyll-install-part4
category: jekyll
keywords: Jekyll, github, github-pages, web, estàtic, instal·lació, Part4
---
<p>
<font size="2"> 
Índex:
<a href="/jekyll-install-part1"> Part1 </a>/
<a href="/jekyll-install-part2"> Part2 </a>/
<a href="/jekyll-install-part3"> Part3 </a>/
<a href="/jekyll-install-part4"> Part4 </a>/
<a href="/jekyll-install-part5"> Part5 </a>/
<a href="/jekyll-install-part6"> Part6 </a>
</font>
</p>

<font size="5"><b><u>Part4 - Creació d'un repositori a Github i com pujar les actualitzacions</u></b></font>

<b>1-</b> El primer pas serà crear un usuari nou a Github.

<center><img src="/images/160725-jekyll4/screenshot.png" width="70%"></center>

<b>2-</b> Un cop tenim usuari, tenim dues opcions:<br>
<b>2.1-</b> Crear un repositori nou amb el nom xxxx.github.io (on xxxx és el teu user a Github).<br>
Github ho interpreta com un <i>User o Master repository</i>. Jo recomano aquesta opció ja que sembla ser la més senzilla.<br>
<b>2.2-</b> Crear un repositori nou i anomenar-lo sense <i>.github.io</i>. En aquest altre cas, això seria interpretat per Github com un <i>Project repository</i> i per poder tenir un web hauries de crear una branca (<i>branch</i>) anomenada gh-pages.<br><br>

<!--more-->

<b>3-</b> Un cop tenim l'usuari i el repositori creat, procedirem a configurar el programa <i>git</i> si és el primer cop que l'utilitzem a l'ordinador. També tenim dues opcions:<br>
<b>3.1-</b> Amb el terminal:<br>
->Configurar el nom d'usuari de Github en git:
{% highlight bash %}
git config --global user.name nom
{% endhighlight %}
"nom" el substituirem pel nostre nom de Github, en el meu cas, momex.<br>

->Configurar l'email d'usuari de Github en git:
{% highlight bash %}
git config --global user.email email
{% endhighlight %}
"email" el substituirem pel nostre email amb el que ens varem registrar a Github.<br><br>

<b>3.2-</b> Manualment amb gedit editant el fitxer de configuració:
{% highlight bash %}
gedit .git/config
{% endhighlight %}

i a la secció d'<i>user</i> afegir o modificar aquests camps:<br>
{% highlight txt %}
[user]
	name = momex
	email = email@example.com

{% endhighlight %}

<b>4-</b> Si ja tenim el web / blog preparat (o mig preparat) i el volem pujar al nostre repositori, podem instal·lar la interfície de git per indicar quins són els fitxers que hem modificat i que volem pujar al repositori, a més d'incloure una petita descripció sobre l'actualització.<br>
{% highlight bash %}
sudo apt-get install gitk giggle git-cola git-gui gitg
{% endhighlight %}

Un cop fet això, accedim a la carpeta del nostre repositori, executem l'eina git i seguim els passos següents:
{% highlight bash %}
cd momex.github.io/
git gui
{% endhighlight %}

i: doble click als fitxers que volem pujar. Amb el doble clic apareixeran abaix.<br>
ii: posem un comentari a la finestra de <i>commit</i><br>
iii: cliquem el botó commit.<br>

<center><img src="/images/160725-jekyll4/gitgui.png" width="70%"></center>

<b>5-</b> Per assegurar-nos que no existeixi cap canvi que nosaltres no tinguem, cosa rara si nosaltres som els únics que editarem el repositori.<br>
{% highlight bash %}
git pull origin master
{% endhighlight %}

En el cas que fos un <i>Project Repository</i> (veure punt 2), s'hauria de picar el següent <i>git pull origin gh-pages</i><br>

<b>6-</b> Finalment, procedim a pujar els canvis depenent de si es un repositori <i>master o gh-pages</i>.
{% highlight bash %}
git push origin master
{% endhighlight %}

Ens demanarà Github <i>user</i> (momex en el meu cas) i el <i>password</i> de Github.<br>
En el cas que fos un <i>Project Repository</i> (veure punt 2), s'hauria de picar el següent <i> git push origin gh-pages</i><br>

Un cop fet el pas 6, ja tindrem les actualitzacions al nostre repositori de Github. Si volem veure el web al nostre navegador ho podrem fer escrivint <i>http://username.github.io</i> (on <i>username</i> és el teu nom d'usuari de Github), en el meu cas, <a href="http://username.github.io" target="_blank">http://momex.github.io</a>.<br>
Al següent post explicarem com enllaçar un domini propi, com www.momex.cat, al repositori de Github.<br>
<a href="/jekyll-install-part5">Seguir Part5</a>
<p>
<font size="2"> 
Índex:
<a href="/jekyll-install-part1"> Part1 </a>/
<a href="/jekyll-install-part2"> Part2 </a>/
<a href="/jekyll-install-part3"> Part3 </a>/
<a href="/jekyll-install-part4"> Part4 </a>/
<a href="/jekyll-install-part5"> Part5 </a>/
<a href="/jekyll-install-part6"> Part6 </a>
</font>
</p>

<font color="white" size="1">Instal·lar jekyll. Instal·lar github-pages. Com vaig moure la meva pàgina web el meu web a github? Blogs amb github jekyll. Blog gratuït </font>

