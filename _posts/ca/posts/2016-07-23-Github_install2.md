---
type: posts
layout: post
lang: ca
comments: true
title: Com crear un lloc web econòmicament per menys de 6€ amb Github i Jekyll - Part2
name: jekyll-install-Part2
permalink: jekyll-install-part2
category: jekyll
keywords: Jekyll, github, github-pages, web, estàtic, instal·lació, Part2
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
<font size="5"><b><u>Part2 - Creació o Clonació del web/blog</u></b></font>

Un cop tenim el gem <i>github-pages</i> instal·lat a l'ordinador (mirar el post <a href="/jekyll-install-part1">anterior</a>), ara ja podem crear el nostre lloc web/blog. Ho podem fer de dues maneres; l'elavorada i la copy/paste.<br>
<b>1) <u>Elavorada</u></b>: mitjançant el terminal, entrem a la carpeta on volem el web/blog i procedim a crear-lo amb el comandament <i>jekyll new "nom del web"</i>. <i>Jekyll</i> crearà un web en blanc predefinit que podrem modificar més tard.

{% highlight bash %}
jekyll new nomweb
{% endhighlight %}

Exemple si volguéssim crear un web/blog anomenat "test":

{% highlight bash %}
momex@cat:~$ jekyll new test
New jekyll site installed in /home/momex/test.
momex@cat:~$ cd test/
momex@cat:~/test$ ls 
about.md     css       _includes   _layouts  _sass
_config.yml  feed.xml  index.html  _posts    _site
{% endhighlight %}

<b>2) <u>Copy/Paste</u></b>: Sempre és més fàcil clonar un web/blog existent als repositoris de Github i anar modificant-lo poc a poc (és una bona manera d'apendre). Per fer-ho, necessitarem el programa <i>git</i> que el podem instal·lar mitjançant el següent comandament al terminal:
{% highlight bash %}
sudo apt-get install git

{% endhighlight %}

Un cop instal·lat, procedirem a localitzar el repositori i copiar l'URL. En el meu cas, l'URL és <a href="https://github.com/momex/momex.github.io.git" target="_blank">https://github.com/momex/momex.github.io.git</a>. Aquest link el trobarem al mateix web de Github.
{% highlight bash %}
git clone https://github.com/momex/momex.github.io.git
{% endhighlight %}

<font size="3"><b>Nota1</b>: Com passa a Wordpress, a github-pages / Jekyll també hi ha plantilles disponibles per a començar a escriure posts. Aquest blog està basat en una plantilla <a href="http://hyde.getpoole.com/" target="_blank">Hyde</a> i la pots clonar amb aquesta <a href="https://github.com/poole/hyde" target="_blank">URL</a>.
</font>
<br>
<!--more-->
Un cop tenim el blog al nostre ordinador, podem començar a modificar-lo. Per fer-ho, només hem d'entrar a la carpeta del web/blog i executar el nostre servidor web amb el següent comandament:
{% highlight bash %}
cd momex.github.io/
jekyll serve --watch
{% endhighlight %}

i ens dirà que podem entrar al web/blog mitjançant el nostre navegador i la URL indicada (http://127.0.0.1:4000). Us deixo una captura del terminal.

{% highlight bash %}
momex@cat:~$ cd momex.github.io/
momex@cat:~/momex.github.io$ jekyll serve --watch
Configuration file: /home/momex/momex.github.io/_config.yml
            Source: /home/momex/momex.github.io
       Destination: /home/momex/momex.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
                    done in 1.974 seconds.
 Auto-regeneration: enabled for '/home/momex/momex.github.io'
Configuration file: /home/momex/momex.github.io/_config.yml
    Server address: http://127.0.0.1:4000//
  Server running... press ctrl-c to stop.
{% endhighlight %}

<br>

<center><img src="/images/160723-jekyll2/screenshot.png"></center>

Ara que ja sabem utilitzar el sevidor web local per veure el nostre web, anem a veure l'estructura del web.<br>
<a href="/jekyll-install-part3">Seguir Part3</a>

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

