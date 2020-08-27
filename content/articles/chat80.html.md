---
title: Le projet CHAT-80
title_home: Le projet CHAT-80
excerpt_home: Un programme des années 1980 capable de répondre à des questions de géographie en langage naturel.
excerpt: Un programme des années 1980 capable de répondre à des questions de géographie en langage naturel.
img: /img/articles/swiprolog.png
alt: SWI-Prolog
category: linguistique
seo_title: Le projet CHAT-80
seo_keyword: julien,gabryelewicz,chat80,chat-80,nlp,linguistique,prolog,intelligence,artificielle,langue,anglaise,langage,compréhension
seo_description: Un programme des années 1980 capable de répondre à des questions de géographie en langage naturel.
position: 19
date_creation: 03/11/2019
---

<p class="py-4">CHAT-80 est un projet d'Intelligence Artificielle créé dans les années 1980 par David Warren et Fernando Pereira à l'Université d'Edinburgh.</p>

<p class="py-4">Le but du projet était de créer un programme capable de répondre à des questions en langue anglaise sur la géographie : pays, villes, rivières, pays limitrophes, etc...</p>

<p class="py-4">Il fut crée pour l'interpréteur Quintus Prolog.</p>

## Les différentes parties du projet

<p class="py-4">Le fonctionnement du programme est divisé en plusieurs modules :</p>

<p class="py-4">- Un parser capable de reconnaître les chiffres et les mots.</p>

<p class="py-4">- Une liste des régles de grammaire de base pour la langue anglaise, de manière à bien pouvoir comprendre la question ("Where is France").</p>

<p class="py-4">Partie de code avec la conjugaison du verbe "to be" : </p>

<pre>
<code>
//verb_form(verbe_conjugue, infinitif, temps, forme).
verb_form(am, be, pres+fin, 1+sin).
verb_form(are, be, pres+fin, 2+sin).
verb_form(is, be, pres+fin, 3+sin).
verb_form(are, be, pres+fin, _+plu).
verb_form(was, be, past+fin, 1+sin).
verb_form(were, be, past+fin, 2+sin).
verb_form(was, be, past+fin, 3+sin).
verb_form(were, be, past+fin, _+plu).
verb_form(been, be, past+part, _).
verb_form(being, be, pres+part, _).
</code>
</pre>

<p class="py-4">- Un système de catégorisation des informations pour les transformer en régles grammaticales.</p>

<p class="py-4">- Un transformeur qui va réécrire la question de l'utilisateur en requête Prolog grâce aux régles de grammaire.</p>

<p class="py-4">- Un répondeur qui s'adapte en fonction de la question (réponse oui/non, comparateur...)</p>

<p class="py-4">- Les bases de connaissance sur chacun des domaines géographiques que l'on divise en fichiers (rivers.pl pour les rivières, countr.pl pour les pays...). Les requêtes Prolog faites auparavant permettent de lire ces fichiers et de trouver les réponses aux questions demandées.</p>

<p class="py-4">Partie de code avec les informations du pays : </p>

<pre>
<code>
//country(nom_pays, continent, latitude, longitude, superficie, population, capitale, monnaie)
country(afghanistan, indian_subcontinent, 33, -65, 254, 861, 18, 290, kabul, afghani).
country(albania, southern_europe, 41, -20, 11, 100, 2, 350, tirana, lek).
country(algeria, north_africa, 35, -11, 919, 951, 15, 770, algiers, dinar).
country(andorra, southern_europe, 42, -1, 0, 179, 0,25, andorra_la_villa, franc_peseta).
country(angola, southern_africa, -12, -18, 481, 351, 5, 810, luanda, ?).
country(argentina, south_america, -35, 66, 1072, 67, 23, 920, buenos_aires, peso).
country(australia,australasia, -23, -135, 2967, 909, 13, 268, canberra, australian_dollar).
country(austria, western_europe, 47, -14, 32, 374, 7, 520, vienna, schilling).
country(bahamas, caribbean, 24, 74, 4, 404, 0, 190, nassau, bahamian_dollar).
</code>
</pre>

## Utilisation sur SWI-Prolog

<p class="py-4">Il existe un module pour SWI-Prolog permettant d'utiliser CHAT-80. Ce dernier a été revisité afin de correspondre aux besoins de l'interpréteur.</p>

<p class="py-4"><a href="https://github.com/JanWielemaker/chat80/" target="_blank" class="underline" title="Chat-80 - Github">Le module se trouve ici.</a></p>

<p class="py-4">Une fois téléchargé, allez sur le dossier du module puis prolog et lancez la commande swipl (pour Unix) ou pl (pour Windows) pour pouvoir utiliser SWI-Prolog.</p>

<p class="py-4">Chargez la librairie chat80</p>

<pre>
<code>
[chat80].
</code>
</pre>

<p class="py-4">Puis démarrez une conversation avec CHAT-80.</p>

<pre>
<code>
chat80:hi.
</code>
</pre>

<p class="py-4">Un message "Question:" sera visible et vous pourrez poser vos questions en langue anglaise.</p>

<p class="py-4">Quelques exemples : </p>

<pre>
<code>
Question: Where is France?
europe' and 'western_europe'.'

Question: what is the capital of france? 
paris'.'

Question: what rivers are in china?
amur',  'brahmaputra',  'ganges',  'hwang_ho',  'indus',  'mekong',  'salween' and 'yangtze'.'

Question: does afghanistan border china?
'Yes.'

Question: which countries are bordered by two seas?
egypt', 'iran', 'israel', 'saudi_arabia' and 'turkey'.'
</code>
</pre>

<p class="py-4">Au cas où la question n'est pas comprise, CHAT-80 invite l'utilisateur à reformuler la question ou alors à trouver un synonyme avec "I don't understand".</p>

<p class="py-4">Si pas de réponse satisfaisante, le message "Nothing satisfies your question" sera visible.</p>

<p class="py-4">CHAT-80 ne possède pas de système d'apprentissage, il charge les faits écrits à l'avance pour pouvoir ensuite vous répondre.</p>

<h3>Anecdote</h3>

<p class="py-4">La librairie Python NLTK possède également des fonctionnalités pour simuler le CHAT-80.</p>

## Quelques liens

<p class="py-4"><a href="http://www.nltk.org/howto/chat80.html" target="_blank" class="underline" title="Chat-80 - NLTK">Le CHAT-80 pour NLTK</a></p>

<p class="py-4"><a href="https://dl.acm.org/citation.cfm?id=972944" target="_blank" class="underline" title="Chat-80 - présentation du projet">Présentation du projet par ses créateurs (en anglais)</a></p>

<p class="py-4"><a href="https://github.com/JanWielemaker/chat80" target="_blank" class="underline" title="Chat-80 - Github">Lien Github vers le projet SWI-Prolog</a></p>