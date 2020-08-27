---
title: Rechercher des mots similaires sur RediSearch
title_home: Rechercher des mots similaires sur RediSearch
excerpt_home: Ou comment utiliser la distance de Levenshtein.
excerpt: Ou comment utiliser la distance de Levenshtein.
img: /img/articles/redisearch.jpg
alt: RediSearch
category: programmation
seo_title: Rechercher des mots similaires sur RediSearch
seo_keyword: julien,gabryelewicz,développeur,redis,redisearch,mots,similaires,distance,levenshtein,recherche,linguistique
seo_description: Ou comment utiliser la distance de Levenshtein.
position: 20
date_creation: 06/11/2019
---

<p class="py-4">Depuis la version 1.2 de RediSearch, le moteur de recherche de Redis, il est devenu possible de rechercher des mots similaires très facilement, grâce à ce que l'on appelle plus communément la distance de Levenshtein.</p>

<p class="py-4">Pour ceux qui ne connaissent pas, la distance de Levenshtein est une méthode de calcul définissant le nombre minimum de remplacement (ajout, suppression, modification) pour arriver d'un mot à un autre.</p>

<p class="py-4">Par exemple, pour passer du mot "voiture" à "voilure", nous ne faisons que remplacer le lettre t par la lettre l, ce qui implique une seule action, donc une distance équivalente à 1.</p>

## Ce que cela donne avec RediSearch

<p class="py-4">Créeons un index qui va contenir des prénoms :</p> 

<pre>
<code>
FT.CREATE liste_prenoms SCHEMA prenom TEXT SORTABLE
</code>
</pre>

<p class="py-4">Remplissons-là de données : </p>

<pre>
<code>
FT.ADD liste_prenoms doc1 1.0 FIELDS prenom "damien"
FT.ADD liste_prenoms doc2 1.0 FIELDS prenom "céleste"
FT.ADD liste_prenoms doc3 1.0 FIELDS prenom "julien"
FT.ADD liste_prenoms doc4 1.0 FIELDS prenom "maxime"
FT.ADD liste_prenoms doc5 1.0 FIELDS prenom "quentin"
FT.ADD liste_prenoms doc6 1.0 FIELDS prenom "angèle"
FT.ADD liste_prenoms doc7 1.0 FIELDS prenom "nicolas"
FT.ADD liste_prenoms doc8 1.0 FIELDS prenom "alexandre"
</code>
</pre>

<p class="py-4">Pour faire une recherche sur un mot similaire, il suffit d'entourer votre mot à rechercher du caractère "%", ce qui vous permet de rechercher des mots dont la distance à votre recherche est égale à 1. </p>

<p class="py-4">Avec la commande FT.SEARCH et en recherchant sur "damine", nous avons : </p>

<pre>
<code>
FT.SEARCH liste_prenoms "@prenom:%damine%"
1) (integer) 1
2) "doc1"
3) 1) "prenom"
   2) "damien"
</code>
</pre>

<p class="py-4">Plus vous en ajoutez, plus la distance pour votre requête sera élevée.</p>

<p class="py-4">Par exemple, faisons une recherche sur damien avec une distance de 3 : </p>

<pre>
<code>
FT.SEARCH liste_prenoms "@prenom:%%%damien%%%"
1) (integer) 2
2) "doc3"
3) 1) "prenom"
   2) "julien"
4) "doc1"
5) 1) "prenom"
   2) "damien"
</code>
</pre>

<p class="py-4">julien et damien ont une distance de 3 (remplacer j,u,l par d,a,m), il est donc accepté comme réponse.</p>

<p class="py-4">Attention, le maximum possible pour la distance de Levenshtein est de 3 pour RediSearch.</p>