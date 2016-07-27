---
type: posts
layout: post
lang: ca
comments: true
title: Com crear un lloc web econòmicament per menys de 6€ amb Github i Jekyll - Part3
name: jekyll-install-Part3
permalink: jekyll-install-part3
category: jekyll
keywords: Jekyll, github, github-pages, web, estàtic, instal·lació, Part3
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
<font size="5"><b><u>Part3 - Estructura de fitxers</u></b></font>

Jekyll és un motor de transformació de text. Bàsicament, l'alimentem d'un text escrit en <i>markdown, txt o html</i> i mitjançant un procés intern et retorna un web estàtic. És a base d'editar unes plantilles (o <i>layouts</i>) internes que podem canviar l'interfície o distribució de la pàgina o decidir si volem un web o un blog. Al web de <a href="https://jekyllrb.com/" target="_blank">jekyllrb</a> hi trobarem molta informació sobre com funciona o quina estructura segueix.<br>
Per si algú vol llegir la informació de primera mà (en anglès), el contingut que conté aquest post prové <a href="https://jekyllrb.com/docs/structure/" target="_blank">d'aquí</a>.<br>

Agafant com a referència aquest blog, l'estructura simplificada és la següent:

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
|   ├── 2016-03-25-HD_tacho_Part1.md
|   ├── 2016-04-01-HD_tacho_Part2.md
|   └── ...
├── _public
|   └── hyde.css
├── _site
├── blog1.xml
├── README.md
├── 404.html
└── index.html
{% endhighlight %}

<!--more-->

<b>_config.yml</b>: Aquest fitxer pot contenir informació de configuració o variables globals.<br>
<b>_images</b>: Directori on guardar les imatges del teu blog o web.<br>
<b>_includes</b>: Fitxers que poden ser mesclats amb les plantilles (o <i>layouts</i>) o posts per simplificar el codi. Per exemple, per afegir comentaris a cada entrada del blog s'han d'afegir unes línies de codi determinades. Si es crea un fitxer amb aquestes línies i es guarda dins d'aquest directori, només farà falta cridar aquest fitxer al final de cada post.<br>
<b>_layouts</b>: Dins d'aquest directori es guarden les plantilles que formaran cadascuna de les parts del web o del blog. Les plantilles són escollides al començament de cada post o pàgina a la part superior (<i>YAML Front Matter</i>).<br>
<b>_posts</b>: La part dinàmica del teu web estàtic. Cada vegada que s'afegeixi un fitxer en aquest directori, Jekyll reconstruirà tot el web de nou. El nom de cada fitxer ha de seguir un format específic: Any-Mes-Dia-títol.MARKUP (Per exemple:<i>2016-07-24-Github_install3.md</i>). L'URL del post (<i>permalink</i>) es pot especificar a la part superior, però la data ve determinada pel nom del fitxer.<br>
<b>_public</b>: Dins d'aquest directori es pot posar els fitxers d'estil tals com *.css.<br>
<b>_site</b>: en aquest directori és on el web estàtic es genera per defecte quan Jekyll finalitza el seu procés.<br>
<b>blog1.xml</b>: Fitxer encarregat de proporcionar les noves publicacions als agregadors feed.<br>
<b>README.md</b>: Sol ser el primer fitxer que es publica quan es crea un repositori a Github. Pot incloure una descripció del lloc web o del blog. No és ni molt menys necessari.<br>
<b>404.html</b>: Per si es vol tenir un fitxer 404 personalitzat.<br>
<b>index.html</b>: Pàgina principal del web.<br>

Per entrendre com funciona Jekyll intèrnament, intentaré fer un diagrama que expliqui els pasos que va fent per arribar a donar el lloc web final:<br>
{% highlight txt %}
momex.cat --> index.html (comença a construir pel default)
   default.html -->head.html (amb tots els meta, title info, css, js, icons, ...)
                -->sidebar.html (barra lateral amb la seva configuració)
                --> { { content } } --> resta de l'índex --> list.html (generarà la llista de posts)
{% endhighlight %}

Un cop ja coneixem l'estructura bàsica d'un web basat en github-pages / Jekyll, ja ho tenim més o menys tot llest per començar a crear i editar el nostre web / blog de manera local. En el següent post, explicarem com crear un repositori per poder pujar el web a Github.<br>
<a href="/jekyll-install-part4">Seguir Part4</a>

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

