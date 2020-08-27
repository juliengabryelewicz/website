---
title: Arrivée de la version 1.2 de Tailwind CSS
title_home: Tailwind CSS passe en 1.2
excerpt_home: Nouvelle version du framework Tailwind avec son lot de nouveautés intéressantes (Transform, Transition, CSS Grid Layout...)
excerpt: Nouvelle version du framework Tailwind avec son lot de nouveautés intéressantes (Transform, Transition, CSS Grid Layout...)
img: /img/articles/tailwind.jpg
alt: Tailwind CSS
category: programmation
seo_title: Arrivée de la version 1.2 de Tailwind CSS
seo_keyword: julien,gabryelewicz,programmation,fonctionnelle,elixir,gardes,guard,guards,fonctionnel,defguard,vérification,condition,pattern,matching
seo_description: Nouvelle version du framework Tailwind avec son lot de nouveautés intéressantes (Transform, Transition, CSS Grid Layout...)
position: 22
date_creation: 12/02/2020
---
<p class="py-4">Depuis peu, Tailwind CSS a sorti une nouvelle version de son framework avec un bon nombre de nouveautés attendus</p>

## La gestion de transition en CSS

<p class="py-4">Une des nouveautés que j'attendais depuis un moment personnellement.</p>

<p class="py-4">Via les propriétés transition-property, transition-duration et transition-timing-function, il est tout à fait possible de faire des animations avec juste quelques classes.</p>

<p class="py-4">Exemple pour un bouton : </p>

<pre>
<code>
&lt;button class="opacity-50 hover:opacity-100 transition-opacity duration-100 ease-out"&gt;mon bouton&lt;/button&gt;
</code>
</pre>

<p class="py-4">L'effet d'opacité est désormais possible grâce à transition-opacity duration-100 et ease-out</p>

## La gestion de transform en CSS

<p class="py-4">Vous pouvez maintenant utiliser cet attribut avec TailwindCSS pour faire des rotations ou agrandir un élément sans difficultés.</p>

<p class="py-4">Exemple de code : </p>

<pre>
<code>
&lt;span class="transform scale-150 rotate-45 translate-x-full origin-center"&gt;&lt;/span&gt;
</code>
</pre>

<p class="py-4">Attention néanmoins, Adam Wathan, le créateur de Tailwind, nous avertit que cette solution n'est pas compatible avec le navigateur IE 11. Il faut donc créer nos propres classes pour pouvoir gérer cela.</p>

## CSS Grid Layout maintenant possible sous Tailwind

<p class="py-4">Le système de positionnement GridLayout est maintenant disponible sous TailwindCSS. Là encore, attention à IE11 qui n'est pas compatible avec ce système. Si IE11 a toujours de l'intérêt pour vous, je vous recommande de passer par Flexbox plutôt.</p>

<pre>
<code>
&lt;div class="grid grid-cols-2 lg:grid-cols-8 gap-6"&gt;
  &lt;div class="col-span-1 lg:col-span-3"&gt;&lt;/div&gt;
  &lt;div class="col-span-1 lg:col-span-3"&gt;&lt;/div&gt;
  &lt;div class="col-start-1 col-end-3 lg:col-start-4 lg:col-end-8"&gt;&lt;/div&gt;
  &lt;div class="col-span-1 col-start-1 lg:col-span-4 lg:col-start-2"&gt;&lt;/div&gt;
  &lt;div class="col-span-1 col-end-3 lg:col-span-6 lg:col-end-9"&gt;&lt;/div&gt;
&lt;/div&gt;
</code>
</pre>

## Et bien plus encore...

<p class="py-4">On pourrait se dire que Tailwind CSS propose de belles choses pour sa nouvelle version, mais c'est loin d'être fini. Plusieurs ajouts secondaires ont été faits comme l'ajout de md, lg et xs pour certains propriétés comem par exemple : </p>

<p class="py-4">border-radius</p>

<pre>
<code>
&lt;div class="max-w-md lg:max-w-none"&gt;...&lt;/div&gt;
</code>
</pre>

<p class="py-4">box-shadow</p>

<pre>
<code>
&lt;div class="shadow-sm"&gt;&lt;/div&gt;
</code>
</pre>