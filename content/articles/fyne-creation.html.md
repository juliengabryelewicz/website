---
title: Créer des applications cross-platform en Go avec Fyne
title_home: Fyne - une UI cross-platform
excerpt_home: Une librairie graphique en Go capable de créer des applications logicielles (Windows, Mac, Linux) et mobiles (Android, iOS)
excerpt: Une librairie graphique en Go capable de créer des applications logicielles et mobiles
img: /img/articles/fyne_logo.png
alt: Fyne
category: programmation
seo_title: Fyne - une UI cross-platform
seo_keyword: julien,gabryelewicz,développeur,web,mobile,fyne,go,gui,cross,platform,android,ios,linux,mac,windows
seo_description: Une librairie graphique en Go capable de créer des applications logicielles et mobiles.
position: 25
date_creation: 03/09/2020
---
<p>Fyne est une librairie graphique écrite en Go permettant des créer des applications cross-platform et mobile. Elle se veut simple d'utilisation et a pour but de ne pas être dépendant des autres librairies graphiques connues (GTK, Vulkan...). Le projet initial a débuté en 2018.</p>

## Installation et démarrage d'un projet

<p>Je pars du principe que vous avez déja installé Go sur votre machine.</p>

<p>Créez un dossier puis utiliser ces lignes pour installer la librairie fyne</p>

<pre>
<code>
go mod init fynedemo
go get fyne.io/fyne
</code>
</pre>

<p>On va ensuite créer un fichier main.go dans notre dossier avec ce code (repris du site de fyne)

<pre>
<code>
package main

import (
  "fyne.io/fyne/app"
  "fyne.io/fyne/widget"
)

func main() {
  //Notre objet application
  app := app.New()
  //création de la fenêtre
  w := app.NewWindow("Hello")
  // Ajout de contenu dans notre fenêtre
  w.SetContent(widget.NewLabel("Hello Fyne!"))
  // On lance notre application
  w.ShowAndRun()
}
</code>
</pre>

<p>Et enfin, lancez la commande go run main.go, vous devriez voir une fenêtre apparaitre avec le texte "Hello Fyne au centre".</p>

<img src="/img/articles/fyne_intro.png" title="Fyne intro" alt="Fyne intro" class="mx-auto" />

## Un outil complet

<p>Nous avons réussi, en à peine quelque lignes de code, à créer une application certes très basique, mais déja fonctionnelle.</p>

<p>On peut d'ailleurs aller bien plus loin. Fyne a crée plusieurs packages permettant d'élaborer des interfaces plus complexes. Nous pouvons y trouver : </p>

<ul>
<li>Des widgets pour créer des boutons, des textes ...</li>
<li>Des layouts pour gérer les emplacements de nos différents widgets et canvas
<li>Des fenêtres de dialogues (demande de confirmation, erreur, chargement...)</li>
<li>etc...</li>
</ul>

<p>Je vous recommande de télécharger et de tester leur application de démo qui recense une grande partie des possibilités de Fyne.</p>

<img src="/img/articles/fyne_demo.png" title="Fyne démo" alt="Fyne démo" class="mx-auto max-w-full" />

<p>Fyne propose également une commande permettant de nous faciliter la tâche pour la création d'applications. Pour cela, il suffit de lancer en ligne de commande : </p>

<pre>
<code>
go get fyne.io/fyne/cmd/fyne
</code>
</pre>

<p>Une des principales fonctionnalités de cette commande est "fyne package" qui nous permet de générer les exécutables pour l'OS ou l'environnement mobile de notre choix. Un sacré gain de temps. Par exemple, pour Linux, cela va donner : </p>

<pre>
<code>
fyne package -os linux -icon icon.png
</code>
</pre>

## Mon avis

<p>Fyne est un excellent package si vous souhaitez faire du développement logiciel ou mobile rapidement.</p>

<p>Le seul point négatif que je citerai pour cette librairie est son affichage graphique, très proche de celle de l'environnement Linux ce qui peut rebuter un utilisateur d'un autre OS. Cela dit, le projet est encore très jeune comparé à GTK et rien ne dit qu'ils ne vont pas changer cela.</p>

<p>Si vous êtes intéressé par cet outil, sachez qu'il existe des tutoriels vidéo en anglais à cette adresse : <a href="https://www.youtube.com/c/Fyneio/videos" target="_blank" class="underline" title="Chaîne Youtube Fyne">https://www.youtube.com/c/Fyneio/videos</a></p>

## Pour en savoir plus

<p><a href="https://fyne.io/" target="_blank" class="underline" title="Le site internet de Fyne">Le site internet de Fyne</a></p>

<p><a href="https://developer.fyne.io/started/" target="_blank" class="underline" title="Le site internet de Fyne">Lien vers l'application de test de Fyne</a></p>

<p><a href="https://github.com/fyne-io/examples" target="_blank" class="underline" title="Autres exemples sur Github">Exemple d'applications Fyne sur Github</a></p>

<p><a href="https://github.com/juliengabryelewicz/gonews" target="_blank" class="underline" title="Github - Go News">Un autre exemple : lecture de flux RSS (travail en cours de construction)</a></p>