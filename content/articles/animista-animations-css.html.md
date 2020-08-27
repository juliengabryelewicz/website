---
title: Animista - le guide des animations CSS
title_home: Animista - le guide des animations CSS
excerpt_home: 70 animations pré-codées disponibles pour vous faire gagner du temps sur vos projets front-end.
excerpt: 70 animations pré-codées disponibles pour vous faire gagner du temps sur vos projets front-end.
img: /img/articles/animista.png
alt: Animista
category: programmation
seo_title: Animista - le guide des animations CSS
seo_keyword: julien,gabryelewicz,programmation,css,front,animista,animation,keyframes,minification
seo_description: 70 animations pré-codées disponibles pour vous faire gagner du temps sur vos projets front-end.
position: 18
date_creation: 29/10/2019
---

<p class="py-4">Animista est un site internet créé par Ana Travas en 2017 dont le but est de proposer des animations pré-codées avec des keyframes afin de vous faire gagner du temps précieux.</p>

<p class="py-4">6 catégories d'animation sont disponibles (disparation, apparition, fonds, texte...) et vous pouvez les effectuer sur plusieurs types de contenus (image, texte, bouton, bloc div...).</p>

<p class="py-4">Là où Animista est très intéressant est que vous pouvez personnaliser votre animation grâce à un formulaire (gestion du temps de l'animation, du délai, de la direction...) qui vous donne par la suite le rendu. Une fois votre animation terminée, vous pouvez ensuite récupérer le code généré.</p>

<p class="py-4">
<img src="/img/articles/animista_1.jpg" alt="Ecran d'Animista" title="Ecran d'Animista" class="mx-auto" />
</p>

<p class="py-4">Exemple de code pour un bloc auquel vous voulez effectuer une rotation suivi d'une disparition :</p>

<pre>
<code>
.rotate-out-center {
	-webkit-animation: rotate-out-center 0.6s cubic-bezier(0.550, 0.085, 0.680, 0.530) both;
	        animation: rotate-out-center 0.6s cubic-bezier(0.550, 0.085, 0.680, 0.530) both;
}

@-webkit-keyframes rotate-out-center {
  0% {
    -webkit-transform: rotate(0);
            transform: rotate(0);
    opacity: 1;
  }
  100% {
    -webkit-transform: rotate(-360deg);
            transform: rotate(-360deg);
    opacity: 0;
  }
}
@keyframes rotate-out-center {
  0% {
    -webkit-transform: rotate(0);
            transform: rotate(0);
    opacity: 1;
  }
  100% {
    -webkit-transform: rotate(-360deg);
            transform: rotate(-360deg);
    opacity: 0;
  }
}
</code>
</pre>


<p class="py-4">La minification est également disponible pour votre code.</p>

<p class="py-4"><a href="http://animista.net/" target="_blank" class="underline" title="Animista">Le lien du projet</p>