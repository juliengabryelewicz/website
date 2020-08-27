---
title: Améliorez la qualité de votre code Elixir avec Credo
title_home: Améliorez la qualité de votre code Elixir avec Credo
excerpt_home: Un module qui apportera plus de lisibilité et de rigueur dans votre code.
excerpt: Un module qui apportera plus de lisibilité et de rigueur dans votre code.
img: /img/articles/elixir.png
alt: Elixir
category: programmation
seo_title: Améliorez la qualité de votre code Elixir avec Credo
seo_keyword: julien,gabryelewicz,qualite,code,elixir,phoenix,programmation,linter,credo,refactorisation
seo_description: Un module qui apportera plus de lisibilité et de rigueur dans votre code.
position: 5
date_creation: 03/09/2019
---

<p>Credo est un module qui va analyser votre code Elixir et vous proposer des suggestions et des améliorations.</p>

<p>On peut le considérer comme un équivalent à <a class="underline" href="https://github.com/rubocop-hq/rubocop" target="_blank" title="Lien Github rubocop">Rubocop pour Ruby</a> ou bien à <a class="underline"  href="https://github.com/overtrue/phplint" target="_blank" title="Lien Github PHPLint">PHPLint pour PHP</a>.</p>

<p>On peut séparer son travail de recherche en plusieurs catégories : </p>

<p>- Lisibilité du code. Il ne s'agit pas de dire si votre code est bon ou pas, mais de montrer des façons plus simples et lisibles de le faire.</p>

<p>- Possibilités de refactorisation de votre code</p>

<p>- Découvertes d'erreurs potentielles</p>

<p>- L'optimisation de l'écriture, notamment pour l'indentation et les espaces<p>

## Comment l'installer?

<p>La meilleure façon de l'installer est, comme tout projet Elixir ou Phoenix, de l'inclure en tant que dépendance dans votre fichier mix :</p>

<pre>
<code>
defp deps do
  [
    {:credo, "~> 1.1.4", only: [:dev, :test], runtime: false}
  ]
end
</code>
</pre>

<p>et de lancer : </p>

<pre>
<code>
mix deps.get
</code>
</pre>

<p>Et voilà ! L'installation est faite !</p>

## Comment ça marche?

<p>Il vous suffit d'aller à la racine de votre projet et de lancer la commande suivante : </p>

<pre>
<code>
mix credo
</code>
</pre>

<p>Le module va regarder tous les fichiers de votre projet, et répartir ses propositions sous cinq catégories, à savoir : </p>

<p>- Code Readability</p>

<p>- Software Design</p>

<p>- Refactoring Opportunities</p>

<p>- Warning - Please take a look</p>

<p>- Consistency</p>

<p>Vous pouvez retrouver le détail de chacun d'entre eux avec ceci :</p> 

<pre>
<code>
mix credo categories
</code>
</pre>

<p>Chacune des affirmations de Credo est composée d'une catégorie, d'une priorité sainsi que d'un texte explicatif avec, par moment, un exemple.</p>

<pre>
<code>
 Phoenix.Channel

   [R] Category: refactor
    ↗  Priority: medium

       If/else blocks should not have a negated condition in `if`.
       lib/phoenix/channel.ex:26 (Phoenix.Channel.subscribe)

    __ CODE IN QUESTION

       if !Socket.authenticated?(socket, channel, topic) do

    __ WHY IT MATTERS

       An `if` block with a negated condition should not contain an else block.

       So while this is fine:

           if !allowed? do
             raise "Not allowed!"
           end

       The code in this example ...

           if !allowed? do
             raise "Not allowed!"
           else
             proceed_as_planned
           end

       ... should be refactored to look like this:

           if allowed? do
             proceed_as_planned
           else
             raise "Not allowed!"
           end

       The reason for this is not a technical but a human one. It is easier to wrap
       your head around a positive condition and then thinking "and else we do ...".

       In the above example raising the error in case something is not allowed
       might seem so important to put it first. But when you revisit this code a
       while later or have to introduce a colleague to it, you might be surprised
       how much clearer things get when the "happy path" comes first.
</code>
</pre>

<p>Exemple repris du github de l'application.</p>

<p>Je vous encourage à utiliser cet outil pour vos projets Elixir. Le temps que vous passerez à prendre en compte les recommendations de Credo vous seront bénéfiques au fur et à mesure de l'évolution de votre code.</p>

<p>Le lien du github de Credo pour plus d'informations : <a class="underline" href="https://github.com/rrrene/credo" target="_blank" title="Lien Github Credo">https://github.com/rrrene/credo</a></p>