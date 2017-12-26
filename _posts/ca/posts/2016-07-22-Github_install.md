---
type: posts
layout: post
lang: ca
comments: true
title: Com crear un lloc web econòmicament per menys de 6€ amb Github i Jekyll - Part1
name: jekyll-install-Part1
permalink: jekyll-install-part1
category: jekyll
keywords: Jekyll, github, github-pages, web, estàtic, instal·lació, Part1
---
<p>
<font size="2"> 
Índex:
<a href="/jekyll-install-part1"> Part1 </a>/
<a href="/jekyll-install-part2"> Part2 </a>/
<a href="/jekyll-install-part3"> Part3 </a>/
<a href="/jekyll-install-part4"> Part4 </a>/
<a href="/jekyll-install-part5"> Part5 </a>
</font>
</p>

Sempre m'havia fet especial gràcia això de tenir un domini propi i tenir un web/blog. Fins ara n'havia tingut un parell (totalment abandonats des de fa anys) allotjats a subdominis com geocities i iespana. L'altre cosa és que aquests webs eren totalment estàtics i els havia fet a base de picar codi html/css amb el <i>Notedap</i> i amb alguns objectes flash.<br>
Després de finalitzar <a href="/HD-tacho-part1">aquest projecte </a> i de portar un temps veient promocions com la de la imatge d'abaix (dominis .cat a 5€ el primer any!) vaig decidir que aquell era el moment de donar un pas més i fer algun web dinàmic amb wordpress o similar.<br>
<center><img src="/images/160722-jekyll/promoweb5euros.jpg"></center>

Algunes empreses ofereixen un cert espai de <i>hosting</i> quan adquireixes el domini amb ells, però aquest <i>hosting</i> només et permet, un altre cop, la creació de webs estàtics i aquest no era el meu cas. Sense entrar molt en detall, una manera comuna de crear un lloc web dinàmic seria tenir un <i>hosting</i> on poder instal·lar un servidor web (com Apache) on poder executar codi generador de contingut html (com php) i tenir alguna base de dades (com MySQL). El preu d'aquest pack oscil·la més o menys entre 5€/mes fins a l'infinit depenent d'altres aspectes com l'espai en disc, tràfic mensual, comptes de correu, etc.<br>
Wordpress també ofereix packs per muntar el teu blog dinàmic amb donimi propi, però els preus tornen a oscil·lar entre 8$/mes (sense google analytics i 13GB d'espai en disc) i 25$/mes (amb google analytics).<br>

Així que l'opció més econòmica, complexa d'instal·lar i més limitada sortiria al voltant de 60€/any i la més fàcil i ràpida per... és igual, massa calers!!. Llavors, com ho fa la gent que té blogs no professionals per no deixar-se una petita fortuna cada any? Alguns cedeixen i registren un subdomini a wordpress (0€) i alguns altres pagen entre 60 i 200€/any per tenir un web més o menys complert. Però <i>googlejant</i> em vaig portar una gran sorpresa quan, per casualitat, vaig veure aquest <a href="https://alexcican.com/" target="_blank"> web </a>, el seu <a href="https://alexcican.com/blog/" target="_blank">blog</a> i en especial aquest <a href="https://alexcican.com/post/guide-hosting-website-dropbox-github/" target="_blank">post</a>.<br>
<!--more-->

<center><img src="/images/160722-jekyll/githublogo.png"></center>

Un web allotjat a <a href="https://github.com/" target="_blank">Github</a>? La idea era molt interessant. Bàsicament, GitHub Pages et permet tenir un domini estàtic gràcies a que  funciona mitjançant el motor Jekyll. Jekyll és un generador estàtic de <i>webblogs</i> bastant simple. Agafa per una banda un directori amb plantilles i per altra uns fitxers de text (els posts), executa un convertidor i retorna un lloc web totalment llest per ser servit/mostrat a qualsevol navegador web. En resum, tot això funciona com un generador dinàmic de llocs web estàtics..simplement primer hauràs de crear unes plantilles amb un llenguatge anomenat <i>liquid</i> (bastant senzill) que definiran l'estructura del teu blog o web. Un cop fet això ja tindràs la base feta.<br>
 A partir d'aquí, ja podràs dedicar el temps a crear fitxers <i>de text o markdown</i> amb codi html i imatges que seran els teus posts del blog o les teves pàgines web. Val a dir que també s'accepten fitxers d'estil CSS, injecció de codi javascript i el millor de tot, permet incloure també codi liquid.<br>

A més a més, pots instal·lar un conjunt de paquets al teu ordinador que et permetran treballar en local i previsualitzar els teus posts o pàgines abans de pujar-les al teu repositori de Github i generar així el nou contingut del teu web.<br>

Dividiré aquesta entrada en 5 parts:<br>
<a href="#Part1"><b>Part1 - Instal·lació de github-pages / jekyll a Ubuntu</b></a><br>
<a href="/jekyll-install-part2"><b>Part2 - Creació o Clonació del web/blog</b></a><br>
<a href="/jekyll-install-part3"><b>Part3 - Estructura de fitxers</b></a><br>
<a href="/jekyll-install-part4"><b>Part4 - Creació d'un repositori a Github i com pujar les actualitzacions</b></a><br>
<a href="/jekyll-install-part5"><b>Part5 - Com enllaçar el teu domini propi amb Github </b></a><br>


<a name="Part1"></a> 
<font size="5"><b><u>Part1 - Instal·lació de github-pages / jekyll a Ubuntu</u></b></font>

Haurem d'instal·lar el següent:<br>
- <b>GEM</b>: Graphics Environment for Multimedia.<br>
- <b>Ruby</b>: cito textualment de la <a href="https://ca.wikipedia.org/wiki/Ruby" target="_blank">wiquipedia</a>, <i>El llenguatge de programació Ruby va ser creat per Yukihiro "Matz" Matsumoto l'any 1993. És un llenguatge de guions totalment orientat a objectes. Està molt orientat al tractament de fitxers i per manteniment del sistema. És simple, extensible i portable.</i><br>
- <b>Rubygems</b>: cito textualment de la <a href="https://en.wikipedia.org/wiki/RubyGems" target="_blank">wiquipedia</a>, <i>és un gestor de paquets pel llenguatge de programació Ruby que proporciona un format estàndard i autocontingut (anomenat gem) per poder distribuir programes o biblioteques en Ruby, una eina destinada a gestionar la instal·lació d'aquests i un servidor per la seva distribució.</i><br>
- <b>github-pages</b>: és un gem de Rubygems. Clica <a href="https://rubygems.org/gems/github-pages/" target="_blank">aquí</a> per veure les dependències/que s'instal·larà.<br>
- <b>Node.js</b>: cito textualment de la <a href="https://ca.wikipedia.org/wiki/Node.js" target="_blank">wiquipedia</a>, <i>és un entorn de programació dissenyat per escriure aplicacions d'Internet escalables, notablement servidors web. Els programes estan escrits en JavaScript, utilitzant una arquitectura orientada a esdeveniments, i entrada/sortida asíncrona per tal de minimitzar el temps de sistema i maximitzar l'escalabilitat</i>.<br>

Per instal·lar aquests paquets a Ubuntu, introduir al terminal les següents línies:
{% highlight bash %}
sudo apt-get install build-essential
sudo apt-get install gem
sudo apt-get install ruby rubygems-integration
sudo apt-get install ruby2.3-dev
sudo gem update --system
sudo apt-get install zlib1g-dev
sudo gem install github-pages
sudo apt-get install nodejs
{% endhighlight %}

<font size="3"><b>Nota1</b>: ruby2.3-dev o l'última versió disponible.<br>
<b>Nota2</b>: a l'instal·lar el gem de github-pages, Jekyll també s'instal·la.</font><br>

Un cop instal·lats els paquets, ara tocarà començar a jugar amb Github i els repositoris.<br>
<a href="/jekyll-install-part2">Seguir Part2</a>

<p>
<font size="2"> 
Índex:
<a href="/jekyll-install-part1"> Part1 </a>/
<a href="/jekyll-install-part2"> Part2 </a>/
<a href="/jekyll-install-part3"> Part3 </a>/
<a href="/jekyll-install-part4"> Part4 </a>/
<a href="/jekyll-install-part5"> Part5 </a>
</font>
</p>

<font color="white" size="1">Instal·lar jekyll. Instal·lar github-pages. Com vaig moure la meva pàgina web el meu web a github? Blogs amb github jekyll. Blog gratuït </font>

