---
type: posts
layout: post
lang: ca
comments: true
title: Com crear un lloc web econòmicament per menys de 6€ amb Github i Jekyll - Part5
name: jekyll-install-Part5
permalink: jekyll-install-part5
category: jekyll
keywords: Jekyll, github, github-pages, web, estàtic, instal·lació, Part5
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

<font size="5"><b><u>Part5 - Com enllaçar el teu domini propi amb Github </u></b></font>


<b>i-</b> Crear el fitxer <i>CNAME</i> dins del repositori de Github. Hem d'editar-lo i escriure-hi el nostre domini sense http i amb o sense www. Per exemple: momex.cat<br>

<b>ii-</b> Entrar al repositori i clicar la pestanya settings. <i>Scroll down</i> fins que trobis un text que digui:<br> <i>Your site is published at http://momex.cat</i><br>
<center><img src="/images/160726-jekyll5/screenshot.png" width="80%" alt="Github repository settings">
<img src="/images/160726-jekyll5/screenshot2.png" width="80%" alt="Github repository settings"></center>
<!--more-->
<b>iii-</b> El següent pas és anar al panell de configuració del teu domini i editar els registres d'IP. Amb això aconseguirem que quan algú vulgui accedir al web sigui redirigit a Github i no al petit hosting que em proporcionava el meu agent de dominis. En el meu cas, al panell haurem d'eliminar el registre A i afegir-ne 2 de nous (especificats al web de Github):<br>
192.30.252.153<br>
192.30.252.154<br>

<center><img src="/images/160726-jekyll5/panellcontrol.png" width="80%" alt="Github repository settings"></center>

Si es vol tenir total seguretat de que s'ha fet bé, sempre podem utilitzar l'eina <i>dig (domain information groper)</i> via el terminal per obtenir les DNS de qualsevol lloc web. Per exemple, per momex.cat abans de fer el canvi (només n'hi havia 1):<br>

{% highlight bash %}
momex@cat:~$ dig momex.cat +nostats +nocomments +nocmd
; <<>> DiG 9.9.5-9ubuntu0.3-Ubuntu <<>> momex.cat +nostats +nocomments +nocmd
;; global options: +cmd
;momex.cat.			IN	A
momex.cat.		300	IN	A	81.25.112.62
{% endhighlight %}

Si ho féssim ara, el resultat seria aquest:<br>
{% highlight bash %}
hummer@Legoland:~$ dig momex.cat +nostats +nocomments +nocmd
; <<>> DiG 9.10.3-P4-Ubuntu <<>> momex.cat +nostats +nocomments +nocmd
;; global options: +cmd
;momex.cat.			IN	A
momex.cat.		7200	IN	A	192.30.252.153
momex.cat.		7200	IN	A	192.30.252.154
{% endhighlight %}



{% highlight bash %}
git config --global user.email email
{% endhighlight %}

Al següent post (i últim, de moment) explicarem alguns consells per millorar la qualitat del blog.<br>
<a href="/jekyll-install-part6">Seguir Part6</a>
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

