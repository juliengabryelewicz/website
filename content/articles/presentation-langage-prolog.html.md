---
title: Petite présentation du langage de programmation Prolog
title_home: Le langage Prolog
excerpt_home: Un des premiers langages de programmation logique destiné à la linguisique et à l'Intelligence Artificielle.
excerpt: Un des premiers langages de programmation logique destiné à la linguisique et à l'Intelligence Artificielle.
img: /img/articles/swiprolog.png
alt: SWI-Prolog
category: programmation
seo_title: Petite présentation du langage de programmation Prolog
seo_keyword: julien,gabryelewicz,programmation,logique,prolog,colmerauer,alain,roussel,phillippe,intelligence,artificielle,ia
seo_description: Un des premiers langages de programmation logique destiné à la linguisique et à l'Intelligence Artificielle.
position: 9
date_creation: 21/09/2019
---

<p>Prolog est un langage de programmation créé dans les années 70 par Alain Colmerauer et Phillippe Rousel à Marseille. Il est l'acronyme de "PROgrammation en LOGique".</p>

<p>Je pense écrire par la suite un cours complet sur l'initation à Prolog.</p>

## à quoi cela ressemble?

<p>Ce qu'il faut savoir, c'est que Prolog est un langage déclaratif. C'est à dire que, dans votre programme, vous n'allez pas trouver d'instructions, ni d'affectations de variable. A la place, vous allez trouver deux éléments importants : </p>

<p>- des faits qui sont des informations génériques (par exemple, "Socrate est un homme").</p>

<p>- des prédicats qui sont des régles permettant de faire le lien entre les différents faits.</p>

<p>Prenons l'exemple le plus connu en Prolog pour illustrer tout cela, l'équivalent du hello world traditionnel : un arbre généalogique basique avec une relation parent/enfant.</p>

<p>Vous avez les faits où sont définis les différents personnages : </p>

<pre>
<code>
homme(arthur).
homme(julien).

femme(angele).
femme(elisabeth).

enfant(celeste,julien).
enfant(celeste,angele).
</code>
</pre>

<p>Nous voyons donc trois types de faits : </p>

<p>- les hommes et les femmes, auxquels nous y attribuerons leurs prénoms (ce qui donne une liaison de type "arthur est un homme" ou "angele est une femme").</p>
<p>- les enfants, qui ont la particularité d'avoir deux données. Le but étant de dire par la suite "celeste est un enfant et a pour parent julien".</p>

<p>Cela nous sera utile pour faire notre arbre généalogique grâce au prédicat que nous allons écrire : </p>

<pre>
<code>
parent(Y,X) :- enfant(X,Y).
</code>
</pre>

<p>Un prédicat est composé de son nom (parent), de ses variables (Y,X) et de la liaison entre un ou plusieurs faits (enfant(X,Y)).</p>

<p>Par ce biais, nous sommes en train de dire que Y est un parent de X si, et seulement si, le fait "X est un enfant de Y" est vérifié.</p>

<p>Ce qui fait que si nous interrogeons notre programme Prolog avec cette question "Est-ce que julien est parent de celeste?" : </p>

<pre>
<code>
?- parent(julien,celeste).
</code>
</pre>

<p>Le programme nous dira true car nous avons le fait suivant qui confirme cela.</p>

<pre>
<code>
enfant(celeste,julien).
</code>
</pre>

<p>En revanche, si vous posez cette question "est-ce que elisabeth est parent de celeste?" : </p>

<pre>
<code>
?- parent(elisabeth,celeste).
</code>
</pre>

<p>Le programme nous dira false car rien ne prouve qu'elisabeth est un parent de celeste et que nous n'avons pas défini cela dans nos faits.</p>

<p>Bien sur, il s'agit d'un exemple très basique, nous pourrions aller plus loin en définissant par exemple, des prédicats pour définir ce qu'est un père ou une mère. Ce qui donne :</p>

<pre>
<code>
pere(X,Y) :- parent(X,Y),homme(X). ("X est père de Y si X est parent de Y et X est un homme")
mere(X,Y) :- parent(X,Y),femme(X). ("X est mère de Y si X est parent de Y et X est une femme")
</code>
</pre>

<p>Pourquoi pas également écrire une liaison grands-parents/petit-enfants ? Il suffirait d'y écrire les prédicats et les faits nécessaires.</p>

<p>Pour résumer, imaginez Prolog comme une base de données, où vous incluez tous vos faits et tous vos prédicats, et une fois remplie, vous pouvez lui poser les questions que vous souhaitez et l'interpréteur Prolog y répondra à partir des informations que vous lui donnez.</p>

## Est-ce que Prolog est encore utilisé de nos jours?

<p>Pas autant que dans les années 70/80, il suffit de voir le très faible nombre d'emploi demandant à connaître Prolog. La programmation logique a été considérée comme un marché de niche, pour des problématiques précises, et incapable de détrôner les autres paradigmes comme la programmation orientée objet. Néanmoins, certaines entreprises et universités portent toujours un intérêt pour ce langage. parmi elles : </p>

<p>- La Swedish Institute of Computer Science (ou SICS), qui a créé son propre interpréteur Prolog qui est <a href="https://sicstus.sics.se" target="_blank" class="underline" title="SICStus">SICStus</a>. Ils ont crée plusieurs programmes pour la NASA (comme le système vocal Clarisse par exemple), ou pour Ericsson AB dans les télécoms.</p>

<p>- L'Université libre d'Amsterdam, notamment un de ses professeurs, Jan Wielemaker, pour l'interpréteur Prolog le plus connu et le plus utilisé : <a href="https://www.swi-prolog.org" class="underline" target="_blank" title="SWI-Prolog">SWI-Prolog</a>.</p>

<p>- <a href="https://kyndi.com" target="_blank" class="underline" title="Kyndi">Kyndi</a>, une entreprise d'Intelligence Artificielle préférant utiliser Prolog (et l'assumant sans problème) plutôt que les systèmes modernes à base de réseaux neuronaux qui ont le souci de "la boîte noire", c'est-à-dire qu'il est impossible de savoir par quel cheminement un programme basé sur un réseau neuronal arrive à la réponse qu'il vous donne. Ils ont d'ailleurs participé activement à la dernière version de SWI-Prolog en 2019.</p>

<p>- IBM, pour son outil IBM Watson, utilise en partie Prolog pour son système de compréhension de langage naturel. <a href="https://www.cs.nmsu.edu/ALP/2011/03/natural-language-processing-with-prolog-in-the-ibm-watson-system/" target="_blank" class="underline" title="IBM Watson utilise Prolog">En savoir plus ici (article en anglais)</a></p>

## Quels sont les avantages de Prolog et pourquoi l'apprendre?

<p>Elles sont multiples : </p>

<h3>Un langage mature</h3>

<p>Au fil des années, de nombreux interpréteurs et librairies ont été écrits pour Prolog. Vous pouvez ajouter des extensions pour faire de la programmation orientée objet (<a href="https://logtalk.org" target="_blank" class="underline" title="Logtalk">Logtalk</a>), des sites internet (<a href="https://blog-core.net" target="_blank" class="underline" title="Blog Core - création de sites internet sous Prolog">blog-core</a>) et j'en passe.</p>

<p>De plus, le langage a évolué avec de nouveaux mécanismes pour la programmation logique (comme la négation par l'échec ou la récursivité par exemple).</p>

<h3>Un langage adapté pour les problématiques liée à la linguistique</h3>

<p>Prolog a justement été pensé pour les problèmes liés à la linguistique. On peut d'ailleurs trouver des bibliothèques à ce sujet comme les Definite Clause Grammar pour la partie grammaire.</p>

<h3>Un autre paradigme à découvrir</h3>

<p>La programmation logique n'est pas le paradigme le plus connu. Il est utilisé seulement pour des cas précis (résolution de contraintes, linguistique, ambiguités...). Néanmoins, apprendre Prolog peut vous amener à raisonner différement, et à penser vos applications d'une autre manière.</p>

## Pour en savoir plus

<p><a href="https://www.swi-prolog.org" class="underline" target="_blank" title="SWI-Prolog">L'interpréteur SWI-Prolog</a></p>

<p><a href="http://alain.colmerauer.free.fr" class="underline" target="_blank" title="Alain Colmerauer">Le site d'Alain Colmerauer</a></p>

<p><a href="http://alain.colmerauer.free.fr/alcol/ArchivesPublications/PrologHistoire/24juillet92plus/24juillet92plusvar.pdf" target="_blank" class="underline" title="Les origines de Prolog">En savoir plus sur les origines de Prolog</a></p>


