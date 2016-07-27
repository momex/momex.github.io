---
type: posts
layout: post
lang: ca
comments: true
title: Crear un blog multilingüe (Github / Jekyll)
name: multilingüe-github
permalink: github-jekyll-multilingüe
category: jekyll
keywords: Jekyll, github, github-pages, web, estàtic, Multilingüe
---

Si rellegim la guia d'instal·lació de Jekyll i github-pages que vaig publicar fa uns dies, a la <a href="/jekyll-install-part3">Part3</a> explicava l'estructura d'aquest blog. Allà hi veureu que dins del directori <i>_posts</i> hi havia totes les entrades del blog. Per aconseguir de manera fàcil un blog on sigui possible seleccionar la llengua desitjada sense haver d'utilitzar <i>plugins</i> adicionals, s'han de fer uns canvis tant d'estructura com de codi.<br>

<b>1- Modificar l'estructura:</b> Dins del directori <i>_posts</i> crearem tantes carpetes com llengües desitgem tal i com podem veure a continuació. Dins de cadascuna, hi posarem els fitxers dels posts en el seu corresponent llenguatge. Com veureu, no és obligatori tenir un <i>post</i> en totes les llengües. En el meu cas, tot està publicat en català i si veig que pot tenir un cert interés global, aleshores preparo una traducció a l'anglès.<br>

{% highlight txt %}
.
├── _config.yml
├── _images
|   ├── test1.png
|   └── test2.jpg
├── _includes
|   ├── footer.html
|   ├── header.html
|   └── sidebar.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── ca
|   |    ├── 2016-03-25-HD_tacho_Part1.md
|   |    ├── 2016-04-01-HD_tacho_Part2.md
|   |    ├── 2016-04-15-Els_vehicles.md
|   |    └── ...
|   └── en
|        ├── 2016-03-25-HD_tacho_Part1.md
|        ├── 2016-04-01-HD_tacho_Part2.md
|        ├── 2016-05-04-Capacitors_summary.md
|        └── ...
├── _public
|   └── hyde.css
├── _site
├── blog1.xml
├── README.md
├── 404.html
└── index.html
{% endhighlight %}

<!--more-->

<b>2- Afegir els <i>tags</i> corresponents:</b> Si heu anat investigant els fitxers dels repositoris de github (repositoris destinats a webs o blogs), haureu vist que a la part superior dels <i>posts</i>, entre gions "- - -", hi ha unes etiquetes (o <i>tags</i>). Aquesta secció amb <i>tags</i> està escrita en llenguatge <i>YAML</i>, acrònim de <i>“YAML Ain’t Markup Language”</i> (YAML no és un llenguatge de marcatge), i serveix per afegir <i>metadata</i> al fitxer que després ens servirà per aplicar filtres. En el cas d'aquest blog, el <i>tag "lang"</i> podrà tenir el valor de <b>ca</b> (per català) o <b>en</b> (per anglès).

{% highlight txt %}
---
type: posts
layout: post
lang: ca
comments: true
title: Tacòmetre Digital per a Harley Davidson Sportster (Part 3 - Harley Davidson i SAE J1850 VPW)
name: HD-tacho-part3
permalink: HD-tacho-part3
category: tacho
keywords: HD, harley, davidson, tachometer, tacho, rpm, J1850, SAE, VPW, especificacions
---

La manera curta i millor d'entendre aquest protocol és llegint aquest document (en anglès). La manera llarga és llegint directament la SAE J1850. De totes maneres, tot seguit resumiré els punts bàsics que s'han d'entendre per a poder programar un codi per rebre i interpretar els missatges de l'ECU motor.
{% endhighlight %}

{% highlight txt %}
---
type: posts
layout: post
lang: en
comments: true
title: Digital Tachometer for Harley Davidson Sportster (Part 3 - Harley Davidson and SAE J1850 VPW)
name: HD-tacho-part3
permalink: en/HD-tacho-part3
category: ENtacho
keywords: HD, harley, davidson, tachometer, tacho, rpm, J1850, SAE, VPW, specification
---

The best and shortest way to understand this protocol is to read this document. The longest way is to read directly the SAE J1850 documentation. Nevertheless, in this post I will try to summarize the most relevant concepts of this protocol in order to be able to write the proper code to receive and interpret the ECM messages.
{% endhighlight %}

<b>3- Filtres:</b> Necessitem incloure com a mínim dos filtres per poder navegar amb comoditat pel blog i canviar de llengua quan volguem. <br>
<b>3.1 - <i>Sidebar</i>:</b> Si us fixeu, a la part superior esquerra just a sobre del títol d'aquest blog (Momex) hi ha l'opció d'escollir el llenguatge. Si només hi ha la possibilitat de català, llavors només tindrem "ca" (també es podria programar per no ensenyar res si només hi ha una opció), si existeix una versió en un altre idioma, per exemple l'anglès, aleshores al costat apareixerà "en".<br>
Per tant, cada vegada que es carregui la barra lateral (<i>sidebar</i>), mirarem si pel post que estem carregant existeix una versió en un altre idioma. Com? Un dels requisits és que el <i>tag "name"</i> ha de portar el mateix nom en tots els posts que siguin el mateix. Per exemple, a dalt en el punt 2, el <i>tag "name"</i> era "HD-tacho-part3" en totes dues versions però el <i>tag "lang"</i> era diferent. El següent codi permet generar tants enllaços com llengües diferents hi hagi d'un mateix post.

{% highlight txt %}
{% raw  %}
{% assign posts=site.posts | where:"name", page.name | sort: 'path' %}    <--A
{% for post in posts %}       <--B
   <a href="{{ post.url }}" {% if page.lang == post.lang %} class="{{ post.lang }} active {% endif %} ">{{ post.lang }}</a>  <----C
{% endfor %}
{% endraw  %}
{% endhighlight %}

Explicat ràpid:<br>
<b>A.</b> Creem un filtre per obtenir un conjunt anomenat "posts" que contingui tots els <i>posts</i> del nostre web que es diguin igual (<i>where:"name"</i>) que la pàgina que estem carregant (<i>page.name</i>). Adicionalment ho ordena per l'<i>URL</i>. <br>
<b>B.</b> Fem un <i>loop</i> per recorrer tots els post que hi ha dins del conjunt acabat de crear.<br>
<b>C.</b> Creem un enllaç ({% raw %} <a href="{{ post.url}}>{% endraw %}) per cadascun dels <i>post</i> dins del conjunt "posts". Adicionalment, amb l'ajuda d'un condicional (<i>if</i>), si la llengua actual correspon a la llengua del <i>post</i> dins de "posts", ho indicarem negreta. Finalment, el text a clicar serà el contingut del <i>tag "lang"</i>.<br>

<b>3.2 - <i>List</i>:</b> Un altre lloc on importarà el llenguatge seleccionat serà el fitxer "list.html" dins del directori <i>_includes</i>. Aquest fitxer és l'encarregat de crear la llista dels últims posts a la pàgina principal del blog. El contingut d'aquest llistat canviarà en funció de la llengua seleccionada.

{% highlight txt %}
{% raw  %}
{% assign posts=site.posts | where: "lang", page.lang | where:"type", "posts" %}   <--A
  {% for post in posts limit: 8 %}  <--B
  <div class="post">
    <h1 class="post-title">
      <a href="{{ post.url }}">     <--C
        {{ post.title }}            <--D
      </a>
    </h1>
    <span class="post-date">{{ post.date | date_to_string }} </font>   <--G
    </span>
  </div>
  {% endfor %}
{% endraw  %}
{% endhighlight %}

Explicat ràpid:<br>
<b>A.</b> Com abans, creem un filtre per obtenir un conjunt anomenat "posts" que contingui tots els <i>posts</i> del nostre web que tinguin el mateix <i>tag "lang"</i> i tinguin el <i>tag "type: posts"</i><br>
<b>B.</b> Fem un <i>loop</i> per recorrer els <i>post</i> que hi ha dins del conjunt creat al punt A. En aquest cas, limitarem el nombre de <i>post</i> a 8.<br>
<b>C.</b> Creem l'enllaç al <i>post</i>.<br>
<b>D.</b> Creem el text a clicar. Aquest serà el títol del <i>post (post.title)</i>. Si us hi fixeu bé, <i>"title"</i> és un altre <i>tag</i>.

