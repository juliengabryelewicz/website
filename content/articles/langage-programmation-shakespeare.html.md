---
title: Le langage de programmation Shakespeare
title_home: Coder en Shakespeare
excerpt_home: Shakespeare est un language de programmation créé en 2001 par Karl Hasselström et Jon Åslund. Sa particularité est d'écrire du code comme si vous écrivez une pièce de théâtre en anglais.
excerpt: Mélanger programmation et écriture de pièce de théâtre, c'est possible.
img: /img/articles/shakespeare.jpg
alt: Shakespeare
category: programmation
seo_title: Le langage de programmation Shakespeare
seo_keyword: shakespeare,langage,programmation,ésotérique,exotique,julien,gabryelewicz,développement
seo_description: Mélanger programmation et écriture de pièce de théâtre, c'est possible.
position: 1
date_creation: 24/08/2019
---

<p>Shakespeare est un language de programmation créé en 2001 par Karl Hasselström et Jon Åslund. Sa particularité est d'écrire du code comme si vous écrivez une pièce de théâtre en anglais.</p>

## Comment ça fonctionne?

<div>
<p>Un programme Shakespeare est composé des éléments suivants et dans l'ordre : </p>

<p><strong>Un titre</strong>, expliquant le but de votre programme.</p>
<p><strong>Les acteurs</strong> de votre pièce de théâtre, qui seront les variables de votre application. Il n'existe qu'un seul type de variable pour ce langage : les nombres entiers.</p>
<p><strong>Les actes et les scènes</strong>, qui permettent à la fois de découper proprement votre application et de revenir à un endroit du programme lors de son exécution, un peu à la manière d'un GOTO en Basic.</p>
<p><strong>Les dialogues</strong>, qui sont le moyen principal pour modifier des variables.</p>
<p>Pour chaque ligne de dialogue écrite, Shakespeare va trouver les noms qui sont utilisés, lister les adjectifs qui y sont attachés, et attribuer une valeur grâce à la formulaire suivante :</p> <p>Tout mot
positif (flower) augmente de 1 sa valeur, à l'inverse, tout mot négatif (bastard) diminue de 1. Pour le cas des mots neutres, cela est compté comme un adjectif positif. Tout adjectif précédent un mot multiplie de deux sa valeur.</p>
<p><strong>Une liste d'actions</strong>, permettant d'interagir avec les variables. On peut citer [Enter Hamlet] par exemple pour pouvoir autoriser à l'utiliser pendant un acte ou alors [Exit Hamlet] pour la réinitialiser.</p>
</ul>

</div>

## Les principales commandes

<div>
<p><strong>Enter [nom du personnage]</strong> : Appel de variable</p>
<p><strong>Exit [nom du personnage]</strong> : Réinitialisation de la variable</p>
<p><strong>Speak your mind. </strong>: Permet d'afficher le résultat d'une variable</p>
<p><strong>Let us proceed to [Nom de la scène ou de l'acte]</strong> : Revenir vers un acte ou une scène précise.</p>
</ul>
</div>

<h2>Un exemple : Ecrire 'hi'</h2>

<div>
<p>Tout ce qui a été dit précédement peut paraitre abstrait, passons à la pratique pour que tout cela soit plus clair. (Exemple repris de shakespearelang.com)</p>


<p><strong>Etape 1 :</strong> le titre</p>

<pre>
<code>
A New Beginning.
</code>
</pre>

<p>Comme dit auparavant, le titre est seulement à but informatif. Vous pouvez résumer en une phrase ce que fait le programme.</p>

<p><strong>Etape 2 :</strong> la génération des variables en présentant les acteurs</p>

<pre>
<code>
Hamlet, a literary/storage device.
Juliet, an orator.
</code>
</pre>

<p>On a donc ici deux variables qui sont "Hamlet" et "Juliet". Une petite description facultative peut être mise en place.</p>

<p><strong>Etape 3 :</strong> Ecriture des actes et des scènes</p>

<pre>
<code>
                    Act I: The Only Act.

                    Scene I: The Prince's Speech.
</code>
</pre>

<p>Les numéros des actes et des scènes doient obligatoirement être en chiffres romains.</p>

<p><strong>Etape 4 :</strong> Entrée en scéne des variables</p>

<pre>
<code>
[Enter Hamlet and Juliet]
</code>
</pre>

<p><strong>Etape 5 :</strong> Dialogue et modification des variables</p>

<pre>
<code>
Juliet: Thou art the sum of an amazing healthy honest noble peaceful fine Lord
        and a lovely sweet golden summer's day. Speak your mind.

        Thou art the sum of thyself and a King. Speak your mind.
</code>
</pre>

<p>Ici, Juliet est en train de parler à Hamlet. Cela veut dire qu'elle va modifier la variable Hamlet grâce aux mots et aux formules écrites. Prenons la première phrase : </p>

<pre>
<code>
Thou art the sum of an amazing healthy honest noble peaceful fine Lord and a lovely sweet golden summer's day. Speak your mind.
</code>
</pre>

<p>On peut la séparer en trois parties.</p>

<pre>
<code>
Thou art the sum of
</code>
</pre>

<p>En Shakespeare, cela signifie qu'il y aura une addition de plusieurs mots à faire. On peut le voir par la suite avec :</p>

<pre>
<code>
an amazing healthy honest noble peaceful fine Lord and a lovely sweet golden summer's day.
</code>
</pre>

<p>Il y a deux mots présents : "Lord" et "summer's day".</p>

<p>Le programme va donc calculer la valeur de ces noms grâce à leur adjectifs et ensuite faire la somme pour l'incrémenter à la variable Hamlet.</p>

<p>En reprenant la formule de calcul utilisée, cela donne : </p>

<p>2 (amazing) * 2 (healthy) * 2 (honest) * 2 (noble) * 2 (peaceful) * 2 (fine) * 1 (Lord) = 64</p>

<p>2 (lovely) * 2 (sweet) * 2 (golden) * 1 (summer's day) = 8</p>

<p>On arrive donc à 64 + 8 = 72 qui est maintenant la valeur d'Hamlet.</p>

<pre>
<code>
Speak your mind.
</code>
</pre>

<p>Cette commande demande à Hamlet sa valeur. Elle est ensuite transformée en lettre via la valeur keyCode. 72 donne donc 'h'.</p>

<pre>
<code>
Thou art the sum of thyself and a King. Speak your mind.
</code>
</pre>

<p>Pour le cas de la deuxième phrase, On demande à Hamlet de faire la somme entre sa valeur actuelle ("thyself") et un mot neutre ("king") ce qui amène à 72+1 = 73. Lors de l'appel 'Speak your mind', on arrive avec le lettre 'i'.</p>

<pre>
<code>
[Exeunt]
</code>
</pre>

<p>Cette commande termine le programme, et donc la pièce de théâtre écrite. Avec les lettres 'h' et 'i' récupérées, on aura pour réponse le mot "hi"</p>

</div>

## Concrètement, ça sert à quoi ?

<div>
<p>Honnêtement, on ne peut pas faire grand chose en Shakespeare, mise à part de l'arithmétique et de l'algorithmie de base. Comme vu lors de notre exemple, nous avons créé une pièce de théâtre pour juste avoir "hi" lors de l'exécution de notre programme.</p>

<p>Mais l'intérêt n'est pas là.</p>

<p>Shakespeare est assez intéressant dans le sens où sa construction se base essentiellement sur l'analyse syntaxique, ce qui fait que vous avez une certaine liberté sur les mots et les adjectifs que vous voulez utiliser, et un grand nombre de combinaisons possibles pour le même résultat.</p>

<p>Un exercice qui peut se révéler assez amusant au final.</p>

<p>Le projet n'a plus été mis à jour depuis 2001. Néanmoins, il existe encore des compilateurs permettant d'utiliser ce langage.</p>
</div>

## Quelques liens

<div>
<p><a href="https://github.com/drsam94/Spl/" target="_blank" class="underline">Un compilateur Shakespeare</a></p>
<p><a href="http://shakespearelang.sourceforge.net" target="_blank" class="underline">La page du projet</a></p>
<p><a href="https://github.com/juliengabryelewicz/shakespeare-examples" target="_blank" class="underline">Quelques exemples en Shakespeare (dont l'exemple ci-dessus)</a></p>
<p><a href="https://keycode.info" target="_blank" class="underline"> Récupérer le keyCode d'une lettre</a></p>
</div>