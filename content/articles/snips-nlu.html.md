---
title: Présentation de Snips NLU
title_home: Snips NLU
excerpt_home: Un outil d'extraction de données pour des phrases en langue naturelle en se basant sur des algorithmes de compréhension du langage.
excerpt: Un outil d'extraction de données pour des phrases en langue naturelle en se basant sur des algorithmes de compréhension du langage.
img: /img/articles/snips.png
alt: Snips NLU
category: programmation
seo_title: Présentation de Snips NLU
seo_keyword: julien,gabryelewicz,développeur,web,mobile,volcal,conversationnel,ia,nlu,snips,linguistique,extraction,données
seo_description: Un outil d'extraction de données pour des phrases en langue naturelle en se basant sur des algorithmes de compréhension du langage.
position: 23
date_creation: 03/03/2020
---
<p class="py-4">Snips NLU (acronyme pour Natural Language Understanding) est une librairie Python open-source permettant de faire de l'extraction de données sur des phrases en langages naturel.</p>

<p class="py-4">Un outil utile si vous comptez faire des chatbot ou des applications vocaux par exemple.</p>

## En quoi cela consiste?

<p class="py-4">Pour pouvoir comprendre un utilisateur, un outil NLU a besoin de deux éléments que nous devons fournir : </p>

<p class="py-4">- <strong>Les Intents</strong>, qui sont des classes contenant une ensemble de phrases prédéfeinis qui vont contenir une intention utilisateur.</p>

<p class="py-4">Par exemple, imaginons que nous voulons créer un chatbot qui recommande des voyages, nous allons donc créer une intent pour les demandes de vols, qui vont contenir un ensemble de phrases comme : </p>

<pre>
<code>
- Quel vol pour Sydney?
- Un vol pour Sydney, s'il vous plait.
- As-tu des vols pour Syndney?
- Avez-vous des vols pour Sydney?
- Un aller-simple pour Sydney.
- Un aller-retour pour Sydney.
- Comment puis-je aller à Sydney?
- ...
</code>
</pre>

<p class="py-4">Toutes ces phrases sont différentes mais possède la même intention : pouvoir voyager à un endroit spécifique.</p>

<p class="py-4">- <strong>Les Slots</strong>, qui sont les paramètres que nous pouvons extraire d'une phrase dans une intent.</p>

<p class="py-4">Reprenons notre exemple précédent. Nous avons créé une intent avec des phrases contenant la destination Sydney, mais nous n'allons pas faire des phrases similaires pour chaque ville, pays, ou endroit ce qui serait un travail colossal et une perte de temps.</p>

<p class="py-4">Pour améliorer cela, nous allons créé un Slot appelé destination qui va contenir des exemples de destination possible puis les insérer dans les phrases-types de l'intent.</p>

<p class="py-4">Cela va donner avec notre exemple :</p>

<pre>
<code>
- Quel vol pour [destination](Melbourne)?
- Un vol pour [destination](Tokyo), s'il vous plait.
- As-tu des vols pour [destination](Paris)?
- Avez-vous des vols pour [destination](New York)?
- Un aller-simple pour [destination](Moscou).
- Un aller-retour pour [destination](Berlin).
- Comment puis-je aller à [destination](Barcelone)?
- ...
</code>
</pre>

<p class="py-4">Comme vous le voyez, non seulement l'information est ciblée, mais Snips saura qu'il s'agit d'une information intéressante que l'utilisateur nous donne.
On pourrait éventuellement aller plus loin en utilisant également pour slot le type de voyage (aller-simple, aller-retour...).</p>

## Comment utiliser Snips?

<h3>Installation</h3>

<p class="py-4">Pour commencer, il faut installer snips via pip</p>

<pre>
<code>
pip install snips-nlu
</code>
</pre>

<p class="py-4">Une fois cela fait, il faut également télécharger la librairie de la langue naturelle dont nous avons besoin pour faire notre traitement de langage naturel : </p>

<pre>
<code>
python -m snips_nlu download fr
</code>
</pre>

<p class="py-4">ou bien : </p>

<pre>
<code>
snips-nlu download fr
</code>
</pre>

<h3>Création de notre fichier NLU avec les intents et les slots</h3>

<p class="py-4">Nous allons maintenant créer un fichier YAML du nom de dataset.yaml qui va contenir notre intent en exemple : </p>

<pre>
<code>
# demandeVoyage intent
---
type: intent
name: demandeVoyage
slots:
  - name: destination
    entity: snips/city
utterances:
  - Quel vol pour [destination](Melbourne)?
  - Un vol pour [destination](Tokyo), s'il vous plait.
  - As-tu des vols pour [destination](Paris)?
  - Avez-vous des vols pour [destination](New York)?
  - Un aller-simple pour [destination](Moscou).
  - Un aller-retour pour [destination](Berlin).
  - Comment puis-je aller à [destination](Barcelone)?
</code>
</pre>

<p class="py-4">Sur Snips, l'intent est composé des éléments suivants : </p>

<p class="py-4">- Son nom</p>
<p class="py-4">- Ses utterances, où les exemples de phrases que l'on reconnait comme appartenant à l'intent. Plus vous donnerez des exemples de phrases, plus la machine donnera des résultats pertinents.</p>
<p class="py-4">- Les slots pouvant être utilisés dans l'intent pour extraire les informations. Vous pouvez créer vos slots personnalisés, mais sachez que Snips propose des slots prêts à l'emploi (ville, température, nombres, argent...) afin de vous faire gagner du temps. Dans notre cas, une liste de ville est déjà proposée.</p>

<p class="py-4">Attention, il arrive que certaines langues n'ont pas les slots que vous cherchez. Il vous faudra donc les créer vous-mêmes.</p>

<p class="py-4">Une fois votre fichier YAML, il vous faudra le générer au format JSON afin d'être compréhensible par Snips. Pour cela, il y a une ligne de commande : </p>

<pre>
<code>
snips-nlu generate-dataset fr dataset.yaml > dataset.json
</code>
</pre>

<p class="py-4">Ne pas oublier de définir la langue pour la génération de votre dataset</p>

<p class="py-4">Enfin, avec notre fichier, nous pouvons coder notre application afin de pouvoir utiliser la NLU de Snips</p>

<p class="py-4">Le code pour récupérer l'intent est le suivant : </p>

<pre>
<code>
import io
import json
from snips_nlu import SnipsNLUEngine
from snips_nlu.default_configs import CONFIG_FR
with io.open("dataset.json") as f:
   sample_dataset = json.load(f)
nlu_engine = SnipsNLUEngine(config=CONFIG_FR)
nlu_engine = nlu_engine.fit(sample_dataset)
text = "Un vol pour Paris, s'il vous plait"
parsing = nlu_engine.parse(text)
</code>
</pre>

<p class="py-4">Séparons ce code en plusieurs parties : </p>

<pre>
<code>
import io
import json
from snips_nlu import SnipsNLUEngine
from snips_nlu.default_configs import CONFIG_FR
</code>
</pre>

<p class="py-4">Nous importons les librairies dont nous avons besoin (io, json) et les librairies Snips avec la NLU pour l'extraction d'information et la langue avec laquelle nous voulons travailler</p>

<pre>
<code>
with io.open("dataset.json") as f:
	sample_dataset = json.load(f)
nlu_engine = SnipsNLUEngine(config=CONFIG_FR)
nlu_engine = nlu_engine.fit(sample_dataset)
</code>
</pre>

<p class="py-4">Avec le fichier JSON que nous avons créé, nous allons l'imbriquer dans notre système NLU afin que Snips puisse s'entraîner et générer son modèle.</p>

<pre>
<code>
text = "Un vol pour Paris, s'il vous plait"
parsing = nlu_engine.parse(text)
</code>
</pre>

<p class="py-4">Et enfin avec la fonction parse, nous obtenons un tableau qui va contenir les informations nécessaires à la compréhension de la phrase de l'utilisateur (intents, slots...), ce qui permettra par la suite de faire un traitement comme par exemple, trouver le vol le moins cher pour Paris.</p>

<p class="py-4">Si vous essayez : </p>

<pre>
<code>
parsing["intent"]["intentName"]
</code>
</pre>

<p class="py-4">Vous allez obtenir demandeVoyage.</p>

<p class="py-4">Avec seulement quelques lignes de code et un peu de travail au niveau de votre dataset, il est tout à fait possible de créer un système de compréhension du langage en peu de temps.</p>

## Les avantages de Snips

<p class="py-4">- Très léger, performant et consomme peu de mémoire (comptez entre 100 et 300Mo pour une utilisation avec une seule langue), marche bien sur un Raspberry.</p>
<p class="py-4">- Très facile à utiliser pour un linguiste ou un développeur vu que l'on se base sur des fichiers YAML</p>
<p class="py-4">- Nécessite peu de lignes de code pour une utilisation basique, et peut s'imbriquer facilement sur n'importe quel framework Python</p>
<p class="py-4">- Obtient des scores de pertinence très élevés (87% de réussite en Janvier 2018)</p>
<p class="py-4">- Open-source</p>
<p class="py-4">- Existe aussi en Rust</p>

## Les inconvénients de Snips

<p class="py-4">- Ne fonctionne que sur 8 langues, ce qui est peu par rapport à ses concurrents comme DialogFlow ou Watson</p>
<p class="py-4">- Moins de mises à jour suite au rachat de Snips par Sonos.</p>
<p class="py-4">- A vérfier, mais il n'est pas possible de générer ses propres modèles de langues. Il vous faut passer par ceux proposés par Snips.</p>