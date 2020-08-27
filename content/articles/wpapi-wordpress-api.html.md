---
title: WPAPI - un client JavaScript utilisant WordPress REST API
title_home: WPAPI - un client JavaScript utilisant WordPress REST API
excerpt_home: Utilisez WordPress come un CMS Headless et facilitez vos appels API pour votre librairie front.
excerpt: Utilisez WordPress come un CMS Headless et facilitez vos appels API pour votre librairie front.
img: /img/articles/wordpress.png
alt: WordPress
category: programmation
seo_title: WPAPI - un client JavaScript utilisant WordPress REST API
seo_keyword: julien,gabryelewicz,wpapi,node,javascript,api,wordpress,rest,client,nodejs
seo_description: Utilisez WordPress come un CMS Headless et facilitez vos appels API pour votre librairie front.
position: 15
date_creation: 20/10/2019
---

<p class="py-4">WordPress possède nativement un système d'API permettant de faire des appels externes pour tout ce qui est demande ou manipulation de ressources (récupération des informations d'un article, inscription d'un client...).</p>

<p class="py-4">Grâce au module WPAPI, la gestion de ces appels devient très simple et nous permet d'utiliser WordPress comme un CMS Headless.</p>

<p class="py-4">Il est recommandé d'avoir la version 5 de WordPress afin de pouvoir exploiter toutes ses fonctionnalités.</p>

## Comment l'installer?

<p class="py-4">Comme toute librairie Node, une simple commande npm suffit :</p>

<pre>
<code>
npm install --save wpapi
</code>
</pre>

<p class="py-4">Puis, une fois le module installé, il faut définir dans vos scripts que vous avez besoin de l'utiliser : </p>

<pre>
<code>
var WPAPI = require( 'wpapi' );
</code>
</pre>

<p class="py-4">Ou alors, si vous utilisez une librairie front de type React : </p>

<pre>
<code>
import WPAPI from 'wpapi';
</code>
</pre>

## Comment cela fonctionne?

<p class="py-4">WPAPI, dans sa dernière version, se base sur le système des Promises en JavaScript.</p>

<p class="py-4">Elle possède des fonctionnalités de base pour chacun des éléments de WordPress (post,categories,comments,media,users....).</p>

<p class="py-4">Concrètement, une commande WPAPI sera écrite de cette manière : </p>

<pre>
<code>
var wp = new WPAPI({endpoint:'http://votre-url.wordpress/wp-json'});

wp.posts().get()
    .then(function( data ) {
        // votre code après récuperation des ressources
    })
    .catch(function( err ) {
        // votre gestion des erreurs
    });
</code>
</pre>

<p class="py-4">On instancie WPAPI et on définit vers quel lien nous faisons les appels.</p>

<p class="py-4">De là, nous pouvons faire nos appels, comme dans le précédent exemple où nous demandons tous les posts existant sur notre site WordPress.</p>

<p class="py-4">D'autres types d'appels sont possibles pour vos ressources, vous avez également create(), update() et delete().</p>

<h3>Filtrer les ressources</h3>

<p class="py-4">Il est possible d'effectuer des recherches spécifique sur un type de contenu de votre choix. Voici quelques exemples :</p>

<pre>
<code>
wp.pages().slug('a-propos')
</code>
</pre>

<p class="py-4 italic">Récupération de la page WordPress contenant le slug "a-propos" (il est possible de le faire avec d'autres champs comme id ou author par exemple).</p>

<pre>
<code>
wp.categories().search('programmation')
</code>
</pre>

<p class="py-4 italic">Récupération des catégories ayant le mot "programmation"</p>

<h3>Trier les ressources</h3>

<p class="py-4">Sur le même principe, les données peuvent être triées.</p>

<pre>
<code>
wp.posts().perPage(5)
</code>
</pre>

<p class="py-4 italic">Récupération des 5 premiers articles</p>

<pre>
<code>
wp.posts().perPage(5).page(3)
</code>
</pre>

<p class="py-4 italic">Récupération des 5 articles à partir de la troisième page</p>

<pre>
<code>
wp.posts().order('asc').orderby('title')
</code>
</pre>

<p class="py-4 italic">Récupération des articles triés par ordre alphabétique</p>

<h3>Et si nous avons des contenus qui ne sont pas possibles à récupérer via les fonctions WPAPI de base?</h3>

<p class="py-4">Pas de problème pour cela, la fonction registerRoute permet de créer une nouvelle route à votre application.</p>

<p class="py-4">Par exemple, si nous voulons récupérer un menu, nous allons définir le chemin nous permettant de faire cela.</p>

<pre>
<code>
wp.menus = wp.registerRoute('menus/v1', '/menus/(?P<id>[a-zA-Z(-]+)');
</code>
</pre>

<p class="py-4">Nous donnons à notre WPAPI le endpoint API ('menus/v1'), auquel nous indiquons que nous allons envoyer un identifiant nommé id avec des caractères spécifiques ('/menus/(?P<id>[a-zA-Z(-]+)').</p>

<p class="py-4">De cette façon, nous pouvons appeler les URLs de types 'https://votre-url.wordpress/wp-json/menus/v1/menu/id-de-mon-menu'. Et voila notre nouvelle fonction : </p>

<pre>
<code>
wp.menus().id('id-de-mon-menu')
</code>
</pre>

## En résumé

<p class="py-4">Si vous ne voulez pas utiliser GraphQL pour récupérer des informations depuis un WordPress, WPAPI est une librairie complète utilisable très facilement avec votre application Node ou avec la librairie front de votre choix.</p>

<p class="py-4">Si vous utilisez WooCommerce en plus, il existe un outil similaire : <a href="https://github.com/woocommerce/woocommerce-rest-api-js-lib" target="_blank" title="WPAPI - WooCommerce RESTAPI" class="underline">WooCommerce REST API</a>.</p>

<p class="py-4"><a href="https://github.com/WP-API/node-wpapi" target="_blank" title="WPAPI - Lien Github" class="underline">Le lien Github du projet WPAPI</a></p>