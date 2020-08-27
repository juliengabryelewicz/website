---
title: PM2 - Une librairie Node.js pour vos projets en production
title_home: La librairie PM2
excerpt_home: Une librairie Node.js efficace qui garantit le fonctionnement de votre application. Mais pas que.
excerpt: Une librairie Node.js efficace qui garantit le fonctionnement de votre application. Mais pas que.
img: /img/articles/pm2.png
alt: PM2
category: programmation
seo_title: PM2 - Une librairie Node.js pour vos projets en production
seo_keyword: pm2,node.js,programmation,développement,processus,déploiement,julien,gabryelewicz
seo_description: Une librairie Node.js efficace qui garantit le fonctionnement de votre application. Mais pas que.
position: 3
date_creation: 25/08/2019
---

<img src="/img/articles/pm2.png" alt="PM2" class="mx-auto" title="PM2" />

<p>PM2 est un gestionnaire de processus pour les applications Node.js. Il est en charge de :</p>

<p>- S'assurer du bon déroulement des processus et de les rédemarrer en cas de panne.</p>
<p>- Gérer les logs de votre application.</p>
<p>- Monitorer les ressources utilisées par chacune de vos applications.</p>

## Fonctionnement et ligne de commandes principales

<p>Une simple ligne de commande suffit pour l'installer : </p>

<pre>
<code>npm install pm2 -g</code>
</pre>

<p>A partir de votre serveur, vous pouvez désormais de lier vos applications à PM2.
Pour cela, il vous suffit d'aller dans le dossier de votre application et d'écrire : </p>

<pre>
<code>pm2 start app.js</code>
</pre>

<p>(app.js étant un nom générique, il faudra l'adapter avec le nom de votre fichier ou de la requête en charge de votre projet)</p>

<p>Et c'est tout ! Votre application est désormais fonctionnelle et le restera en cas de problèmes. PM2 s'occupera du reste.</p>
<p>Vous pouvez en ajouter d'autres avec la même ligne de commande, la librairie peut gérer vos applications indépendament des unes des autres.</p>

<p>Pour les lignes de commandes disponibles, voici les plus importantes : </p>

<p>pm2 list Liste toutes les processus PM2</p>

<p>pm2 stop (id application) : Arrête un processus</p>

<p>pm2 start (id application) : Démarre un processus</p>

<p>pm2 restart (id application) : Redémarre un processus</p>

<p>pm2 monit : Ouvre le monitoring. En un seul écran, vous avez la liste des processus, les logs générés, ainsi que les informations metadata sur chaque application.</p>

## Quelques conseils d'utilisation

<p>N'hésitez pas à créer un fichier de configuration ecosysteme. Ce principe a plusieurs avantages : </p>

<p>- Vous pouvez y inclure des variables d'environnements</p>
<p>- La gestion des déploiements via Git est simplifiée et vous n'avez pas à intervenir au niveau du serveur</p>

<p>Pour générer le fichier de configuration : </p>

<pre>
<code>pm2 ecosystem</code>
</pre>

<p>Pour les logs, il est recommandé de le lier à logrotate afin de compartimenter et limiter la taille de ces fichiers.</p>

<p>Pour cela, il vous faudra pm2-logrotate</p>

<pre>
<code>pm2 install pm2-logrotate</code>
</pre>

## En résumé

<p>PM2 est une librairie indispensable pour tout projet Node.js.</p>

<p>Un seul article ne suffit pas pour expliquer tout le potentiel de PM2 et celui-ci a pour seul but de présenter les bases. Je vous laisse donc le lien pour en savoir plus : <a href="http://pm2.keymetrics.io" target="_blank">http://pm2.keymetrics.io</a></p>