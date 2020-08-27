---
title: Les gardes en Elixir
title_home: Les gardes en Elixir
excerpt_home: Un système de pattern-matching permettant de mieux organiser votre code.
excerpt: Un système de pattern-matching permettant de mieux organiser votre code.
img: /img/articles/elixir.png
alt: Elixir
category: programmation
seo_title: Les gardes en Elixir
seo_keyword: julien,gabryelewicz,programmation,fonctionnelle,elixir,gardes,guard,guards,fonctionnel,defguard,vérification,condition,pattern,matching
seo_description: Un système de pattern-matching permettant de mieux organiser votre code.
position: 21
date_creation: 09/11/2019
---
<p class="py-4">En programmation fonctionnelle, les gardes sont une manière de vérifier si une fonction peut être exécuté selon certaines conditions.</p>

<p class="py-4">On retrouve ce principe dans les langages de programmation Haskell, Erlang et aussi Elixir.</p>

## Comment les implémenter en Elixir

<h3>La méthode classique</h3>

<p class="py-4">Pour pouvoir ajouter une garde, il suffit d'ajouter le mot-clé when dans votre fonction et d'y mettre la condition de votre choix. Cela donne le code suivant : </p>

<pre>
<code>
def round_float(value) when is_float(value), do: IO.puts round(value)
</code>
</pre>

<p class="py-4">Comment cela se passe au niveau de l'exécution de votre fonction ? </p>

<p class="py-4">- La fonction va d'abord vérifier when is_float(value) pour savoir si l'attribut envoyé respecte la condition</p>
<p class="py-4">- Si oui, la fonction est exécutée et renvoie round(value)</p>
<p class="py-4">- Si non, un message d'erreur apparait</p>

<p class="py-4">Avec ce système, on peut avoir des fonctions avec des noms identiques mais pas les mêmes gardes, ce qui amène à des traitements différents, comme ce code : </p>

<pre>
<code>
def round_float(value) when is_float(value), do: IO.puts round(value)
def round_float(value) when is_integer(value), do: IO.puts value
</code>
</pre>

<p class="py-4">La fonction va donc être utilisée dans cet ordre : </p>

<p class="py-4">- La fonction va d'abord vérifier when is_float(value) pour savoir si l'attribut envoyé respecte la condition</p>
<p class="py-4">- Si oui, la fonction est exécutée et renvoie round(value)</p>
<p class="py-4">- Si non, on passe à la fonction suivante en vérifiant la condition is_integer(value) et elle renvoit une réponse si value est de type integer</p>

<p class="py-4"><strong class="underline">Très important à savoir :</strong> l'ordre d'appel des fonctions que vous avez écrites se fait de haut en bas.</p>

<p class="py-4">Il est également possible de cumuler les conditions avec les mots-clés and et or : </p>

<pre>
<code>
def more_than_two(value) when is_integer(value) and value > 2, do: true
</code>
</pre>

<h3>Bien gérer ses gardes</h3>

<p class="py-4">Ecrire chaque garde sur vos fonctions peut s'avérer répétitif et long à maintenir par la suite. Heureusement, il existe les mot-clés defguard et defguardp qui nous permettent d'écrire les conditions et de les utiliser de manière générique.</p>

<p class="py-4">Nous allons définir un module qui va contenir la liste des gardes que nous allons utiliser : </p>

<pre>
<code>
defmodule MyGuards do
  defguard is_even(value) when is_integer(value) and rem(value, 2) == 0
  defguard is_odd(value) when is_integer(value) and rem(value, 2) != 0
end
</code>
</pre>

<p class="py-4">Pour les implémenter dans un autre module : </p>

<pre>
<code>
import MyGuards, only: [is_even: 1, is_odd: 1]

defmodule MyFunctions do
	def my_function(number) when is_even(number) do
	  # code
	end

	def my_function(number) when is_odd(number) do
	  # code
	end
end
</code>
</pre>

## Pourquoi utiliser des gardes?

<h3>Plus lisible qu'une condition if</h3>

<p class="py-4">Supposons que vous voulez écrire une fonction qui fait un traitement spécifique par rapport au type de l'attribut que vous envoyez, la méthode simple pour le faire est ceci : </p>

<pre>
<code>
defmodule Mymodule do
	def my_function(number) do
		if is_integer(number) do
			IO.puts number
		end
		if is_float(number) do
			IO.puts round(number)
		end
	end
end
</code>
</pre>

<p class="py-4">En utilisant le système des gardes, vous allez l'écrire de cette façon pour le même résultat : </p>

<pre>
<code>
defmodule Mymodule do
	def my_function(number) when is_integer(number), do: IO.puts number
	def my_function(number) when is_float(number), do: IO.puts round(number)
end
</code>
</pre>

<p class="py-4">De cette manière, vous vous assurez de bien séparer les traitements en fonction du type de votre attribut et vous y gagnez en lisibilité étant donné que vous gagnez un niveau de profondeur sur vos conditions.</p>

<h3>Utilisable à plusieurs endroits de votre code</h3>

<p class="py-4">J'ai parlé essentiellement des fonctions nommées dans cet article mais sachez qu'il est possible de mettre des gardes ailleurs en Elixir, comme par exemple avec la mot-clé case :</p>

<pre>
<code>
  case x do
    1 -> "one"
    2 -> "two"
    value when is_integer(value) and value > 2 -> "more than two"
  end
</code>
</pre>

<p class="py-4">Ou alors avec les fonctions anonymes : </p>

<pre>
<code>
more_than_two? = fn
    value when is_integer(value) and value > 2 -> true
    value when is_integer(value) -> false
end
</code>
</pre>

