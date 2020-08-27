---
title: Day.js - une librairie JavaScript pour les dates
title_home: Gestion des dates avec Day.js
excerpt_home: Une meilleure gestion des dates pour seulement 2kB
excerpt: Une meilleure gestion des dates pour seulement 2kB
img: /img/articles/dayjs.png
alt: WordPress
category: programmation
seo_title: Day.js - une librairie JavaScript pour les dates
seo_keyword: julien,gabryelewicz,dayjs,day.js,javascript,date,gestion,momentjs,moment.js,heure,parse,manipuler,formatter
seo_description: Une meilleure gestion des dates pour seulement 2kB
position: 8
date_creation: 12/09/2019
---

<p>Day.js est une librairie JavaScript pouvant être considérée comme une alternative à <a href="https://momentjs.com" target="_blank" title="Moment.js" class="underline">moment.js</a>. Elle est compatible pour tous les navigateurs modernes, et peut aller jusqu'à Internet Explorer 9.</p>

<p>Plus légère que cette dernière et offrant plus de choix, elle est également facile à utiliser.</p>

## Installation

<p>Pour l'installer, c'est très simple, il vous suffit soit :</p>

<p>- de lancer la commande npm</p>

<pre>
<code>
npm install dayjs --save
</code>
</pre>

<p>- d'utiliser une balise script avec le lien externe</p>

<pre>
<code>
&lt;script src="https://unpkg.com/dayjs"&gt;&lt;/script&gt;
</code>
</pre>

<p>- de la télécharger à partir de ce lien : https://unpkg.com/dayjs</p>

## Les possibilités

<p>Si vous avez déja utilisé moment.js, vous allez retrouver de nombreuses fonctions similaires.</p>

<p>Parser une date</p>

<pre>
<code>
dayjs('2019-09-13')
</code>
</pre>

<p>Afficher une date à un format précis</p>

<pre>
<code>
dayjs().format('YYYY MM-DD HH:mm')
</code>
</pre>

<p>Manipuler une date</p>

<pre>
<code>
dayjs().add(3, 'month')
</code>
</pre>

<p>Faire des conditions</p>

<pre>
<code>
dayjs().isBefore(dayjs())
</code>
</pre>

<p>Définir une langue pour le formattage de vos dates</p>


<pre>
<code>
import 'dayjs/locale/es'

dayjs.locale('es')
</code>
</pre>


<p>Day.js est un excellent choix si vous ne voulez pas utiliser la classe Date en JavaScript.</p>

<p>Voici le lien vers le projet : <a href="https://github.com/iamkun/dayjs" target="_blank" title="Github day.js" class="underline">https://github.com/iamkun/dayjs</a></p>