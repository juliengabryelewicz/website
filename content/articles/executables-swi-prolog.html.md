---
title: Créer des exécutables avec SWI-Prolog
title_home: Créer des exécutables avec SWI-Prolog
excerpt_home: Créer des programmes Prolog qui peuvent s'exécuter sans avoir besoin d'un interpréteur, c'est possible.
excerpt: Créer des programmes Prolog qui peuvent s'exécuter sans avoir besoin d'un interpréteur, c'est possible.
img: /img/articles/swiprolog.png
alt: SWI-Prolog
category: programmation
seo_title: Créer des exécutables avec SWI-Prolog
seo_keyword: julien,gabryelewicz,programmation,logique,prolog,colmerauer,alain,roussel,phillippe,intelligence,artificielle,ia
seo_description: Créer des programmes Prolog qui peuvent s'exécuter sans avoir besoin d'un interpréteur, c'est possible.
position: 17
date_creation: 28/10/2019
---

<p class="py-4">Il est assez rare de vouloir créer des exécutables en Prolog. On préfère généralement utiliser un interpréteur en ligne de commande ou alors passer par un script Shell. Néanmoins, quelques cas vous forcent à créer des programmes, comme par exemple, le fait de travailler sur une machine qui n'a pas d'interpréteur Prolog installé et dont il n'y a pas grande utilité.</p>

<p class="py-4">La méthode dont je vais vous parler se base sur Linux / Mac OS X et avec l'interpréteur <a href="https://www.swi-prolog.org/" target="_blank" class="underline" title="SWI-Prolog">SWI-Prolog</a>. Pour Windows, je vous invite à aller sur <a href="https://www.swi-prolog.org/FAQ/WinExe.html" target="_blank" class="underline" title="Créer des exécutables sous Windows - SWI-Prolog">cette page.</a></p>

## La méthode

<p class="py-4">Pour créer un exécutable, vous allez avoir besoin d'un fichier Prolog qui va contenir l'ensemble de vos faits et prédicats ainsi que d'un prédicat principal, qui va être exécuté lors de l'appel au programme en ligne de commande.</p>

<p class="py-4">Prenons un exemple simple : dire bonjour.</p>

<p class="py-4">Avec SWI-Prolog, cela donne ceci : </p>

<pre>
<code>
bonjour :-
    write('Bonjour'),
    halt.
</code>
</pre>

<p class="py-4">Insérez ce prédicat dans un fichier (pour notre exemple, nous allons l'appeler "bonjour.pl") puis lancez la commande suivante.</p>

<pre>
<code>
swipl -o bonjourexe -g bonjour -c bonjour.pl
</code>
</pre>

<p class="py-4">SWI-Prolog va alors automatiquement générer votre programme. Notez qu'il y a besoin de trois informations : </p>

<p class="py-4">- Le nom de votre exécutable (bonjourexe)</p>
<p class="py-4">- Le nom du prédicat à appeler (bonjour)</p>
<p class="py-4">- Le fichier contenant l'ensemble de votre programme (bonjour.pl)</p>

<p class="py-4">Un fichier va alors être créer sur le dossier sur lequel vous êtes. Pour l'appeler, il suffit d'écrire sur votre terminal : </p>

<pre>
<code>
./bonjourexe
</code>
</pre>

<p class="py-4">"Bonjour" va apparaitre. Votre programme a fonctionné ! </p>

<h3>Et si on veut donner des arguments à notre programme?</h3>

<p class="py-4">Il est tout à fait possible de le faire.</p>

<p class="py-4">Reprenons notre ancien exemple, et donnons la possibilité d'ajouter un prénom.</p>

<p class="py-4">On va donc avoir:</p>

<pre>
<code>
bonjour :-
    current_prolog_flag(argv, Argv),
    concat_atom(Argv, ' ', SingleArg),
    write('Bonjour '),
    write(SingleArg),
    halt.
</code>
</pre>

</p>Les deux premières lignes nous permettent de récupérer le ou les arguments et de pouvoir les utiliser par la suite.</p>

<p class="py-4">Nous lançons la même ligne qu'auparavant pour créer notre exécutable : </p>

<pre>
<code>
swipl -o bonjourexe -g bonjour -c bonjour.pl
</code>
</pre>

<p class="py-4">Puis testons notre programme : </p>

<pre>
<code>
./bonjourexe julien
</code>
</pre>

<p class="py-4">Nous obtenons "Bonjour julien".</p>

## Les bonnes pratiques

<h3>Ajoutez toujours halt à la fin de votre prédicat principal</h3>

<p class="py-4">Si vous ne le faites pas, cela va lancer votre interpréteur sans vous donner le résultat. Dans le cas d'une machine sans Prolog, rien apparaîtra car le programme ne saura pas quand s'arrêter. halt est une fonction SWI-Prolog forçant l'arrêt du script.</p>

<h3>Vous ne pouvez pas avoir plus d'un prédicat principal avec le même nom</h3>

<p class="py-4">Seul le premier prédicat visible sera utilisé. Il vous faudra donc bien organiser votre code si vous avez plusieurs prédicats avec le même nom.</p>

<h3>Passez des fichiers Prolog comme arguments si vous avez des données complexes à envoyer</h3>

<p class="py-4">Evitez de donner trop d'arguments sur votre exécutable. L'avantage du fichier Prolog est qu'il vous permet de mettre tous les faits et informations que vous souhaitez. Il suffira, dans votre prédicat principal, de passer par la <a href="https://www.swi-prolog.org/pldoc/doc_for?object=consult/1" target="_blank" class="underline" title="Fonction consult - SWI-Prolog">fonction consult</a> pour pouvoir les charger et les rendre utilisable pour votre exécutable.</p>