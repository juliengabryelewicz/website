---
title: Strapi - un CMS Headless gratuit Node.js
title_home: Strapi - un CMS Headless gratuit
excerpt_home: Une alternative intéressante à WordPress et Contentful.
excerpt: Une alternative intéressante à WordPress et Contentful.
img: /img/articles/strapi.png
alt: Strapi
category: programmation
seo_title: PM2 - Une librairie Node.js pour vos projets en production
seo_keyword: strapi,julien,gabryelewicz,headless,cms,node,js,api,gestion,contenu,javascript
seo_description: Une alternative intéressante à WordPress et Contentful.
position: 13
date_creation: 11/10/2019
---

<p class="py-4">Strapi est un outil permettant de créer et de gérer facilement une API. A part l'installation où il faut passer en ligne en commande, il n'est pas nécessaire d'avoir des connaissances en programmation pour créer une API de base.</p>

<p class="py-4">Depuis quelques mois, Strapi propose une nouvelle version (actuellement, le projet est en bétâ) avec une refonte complète (transfert de Angular vers React, Waterline vers Mongoose et Bookshelf...).</p>

<p class="py-4">Il est idéal pour des sites internet de type blog, vitrine ou institutionel.</p>

## L'installation

<p class="py-4">Il est conseillé d'avoir la version 10 de Node pour installer Strapi en version bétâ.</p>

<p class="py-4">Ensuite, une ligne de commande sur votre terminal suffit pour installer Strapi via npm : </p>

<pre>
<code>
npm install strapi@beta -g
</code>
</pre>

<p class="py-4">La ligne de commande changera dès que la version 3 sera stable.</p>

<p class="py-4">Quelques minutes après suffisent pour installer un Strapi fonctionnel.</p>

<p class="py-4"><a href="https://strapi.io/documentation/3.0.0-beta.x/getting-started/quick-start.html" class="underline" target="_blank" title="Guide d'installation de Strapi">Voir la page d'installation.</a></p>

## Comment fonctionne Strapi ?

<p class="py-4">Strapi vous permet de gérer les points principaux suivants : </p>

<p class="py-4">- La création de types de contenu de votre choix (Articles, Catégories... sont des noms que vous pouvez leur donner) avec les champs que vous voulez mettre en place (texte, nombre, date, media...) ainsi que leurs attributs (obligatoire ou non, wysiwyg...).</p>

<p class="py-4">- La création d'utilisateurs avec les permissions d'utilisation des API.</p>

<p class="py-4">- La gestion des appels api de chacun de vos types de contenu (restriction, autorisation en fonction des rôles, champs à mettre en place...).</p>

<p class="py-4">Une fois vos types de contenus créés et vos contenus écrits, Strapi va générer automatiquement les appels API pour permettre la récupération et la gestion de ces contenus, ce qui amène à des urls comme par exemple : </p>

<pre>
<code>
http://localhost:1337/articles
</code>
</pre>

<p class="py-4 italic">Récuperation de tous les contenus de type "Articles"</p>

<p class="py-4">Il est également possible, via ces URLs, de filtrer ou ordonner vos contenus : </p>

<pre>
<code>
http://localhost:1337/articles/1
</code>
</pre>

<p class="py-4 italic">Récupération du contenu de type 'Article' à l'identifiant 1</p>

<pre>
<code>
http://localhost:1337/articles?title_contains=lorem%20ipsum&_sort=created_at:DESC&_limit=10
</code>
</pre>

<p class="py-4 italic">Récupération des contenus de type 'Article' dont le titre contient "lorem" et "ipsum" triée du plus récent au plus ancien avec une limite de 10 articles.</p>

<p class="py-4">Les endpoints de GET,POST,PUT et DELETE sont également possibles avec Strapi.</p>

## Les avantages et les inconvénients

<p class="py-4">+ De très bonnes performances depuis la refonte de la v1 vers la v3.</p>

<p class="py-4">+ Une interface d'administration très intuitive, qui ressemble beaucoup à celle de WordPress.</p>

<p class="py-4">+ Une large gamme de type de champs (Texte, image, case à cocher, éditeur wysiwyg avec rendu Markdown, média...)</p>

<p class="py-4">+ Possibilité d'utiliser GraphQL.</p>

<p class="py-4">+ Un vaste choix de base de données (MongoDB, PostgreSQL, SQLite, MariaDB...). Il est recommandé d'utiliser MongoDB.</p>

<p class="py-4">+ Peut être utilisé très facilement avec un technologie front (React, Vue, Svelte...).</p>

<p class="py-4">+ Peut être utilisé avec un système de génération de sites statiques (Gatsby, Jekyll...).</p>

<p class="py-4">- Projet encore en bétâ à l'heure où j'écris ces lignes, donc une existence encore possible de bugs.</p>

<p class="py-4">- Nécessité de mettre les mains dans le code pour des structures complexes (notamments pour des jointures multiples) afin d'améliorer les performances.</p>

<p class="py-4">- Nombre de plugins encore limité, étant donné que le projet n'est pas encore stable.</p>

## Conclusion

<p class="py-4">Strapi est un excellent outil Node.js pour du back-end. Une excellente alternative à d'autres solutions payantes comme Contentful. Son interface d'administration ainsi que sa simplicité d'utilisation plaira aussi bien aux non-développeurs qu'aux habitués de Node.js.</p>

<p class="py-4"><a href="https://strapi.io/" class="underline" target="_blank" title="Strapi">Lien du projet</a></p>