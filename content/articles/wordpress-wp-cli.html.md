---
title: Gérer WordPress en ligne de commande avec WP-CLI
title_home: WordPress en ligne de commande avec WP-CLI
excerpt_home: Ou comment gagner du temps sans passer par l'interface d'administration.
excerpt: Ou comment gagner du temps sans passer par l'interface d'administration.
img: /img/articles/wordpress.png
alt: WordPress
category: programmation
seo_title: Gérer WordPress en ligne de commande avec WP-CLI
seo_keyword: julien,gabryelewicz,wp-cli,wp-cli,wordpress,woocommerce,ligne,commande,thème,plugin,gestion
seo_description: WP-CLI est un outil permettant de gérer et modifier un site WordPress seulement en passant par des lignes de commande.
position: 6
date_creation: 07/09/2019
---

<p>WordPress est le CMS PHP le plus utilisé dans le monde. Il permet de créer très facilement un site internet, sans forcément avoir besoin de connaissance technique. </p>

<p>Cependant, si à un moment, comme moi, vous étiez amené à gérer plusieurs WordPress en même temps, vous aviez remarqué que cela pouvait vite devenir chronophage, notamment pour la sécurité et la gestion des plugins.</p>

<p>Heureusement, depuis quelques années, il existe un moyen de gérer des sites WordPress en ligne de commande et d'avoir un énorme gain de temps : WP-CLI.</p>

## Comment l'obtenir?

<p>Pour l'installation , je vais partir du principe que vous utilisez Ubuntu ou Mac OS X</p>

<p>Quelques lignes de commande suffisent : </p>

<p>1) Récupérer le fichier PHAR sur le site du projet</p>

<pre>
<code>
wget -c http://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
</code>
</pre>

<p>2) Vérifier que le fichier fonctionne bien </p>

<pre>
<code>
php wp-cli.phar --info
</code>
</pre>

<p>3) Faire en sorte de l'utiliser avec la commande wp</p>

<pre>
<code>
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp
</code>
</pre>

<p>Et voilà ! Nous pouvons maintenant utiliser WP-CLI</p>

## les cas d'utilisation

<p>Je ne vais pas vous faire la liste complète des fonctionnalités, tellement la liste est grande. Je vais donc me concentrer sur les principales</p>

<p>- Installer WordPress</p>

<pre>
<code>
wp core download
wp core config --dbname="nom_base_donnees" --dbuser="nom_utilisateur" --dbprefix="wp_" --dbpass="mot_de_passe_base_de_donnees"
wp core install --url="http://monsite.fr" --title="Mon site WordPress" --admin_user="admin" --admin_password="mot_de_passe" --admin_email="votre@mail.fr"
</code>
</pre>

<p>Bien entendu , pour les paramètres, mettez ceux adaptés à vos besoins.</p>

 <p>- Installer un thème WordPress</p>

<pre>
<code>
wp theme install nomdemontheme --activate
</code>
</pre>

<p>activate n'est pas une option obligatoire, vous pouvez l'enlever si vous ne voulez pas que votre thème soit actif de suite.</p>

<p>Les thèmes sont disponibles sur ce lien : <a class="underline" href="https://fr.wordpress.org/themes/" target="_blank" title="Thèmes WordPress">https://fr.wordpress.org/themes/</a></p>

<p>- Installer un plugin WordPress</p>

<pre>
<code>
wp plugin install plugin1 plugin2 --activate
</code>
</pre>

<p>Les plugins pouvant être installés se trouvent ici : <a class="underline" href="https://fr.wordpress.org/plugins/" target="_blank" title="Plugins WordPress">https://fr.wordpress.org/plugins/</a></p>

<p>- Changer l'URL du site</p>

<pre>
<code>
wp option update home 'http://exemple.com'
wp option update siteurl 'http://exemple.com'
</code>
</pre>

<p>(Dieu merci, plus besoin d'aller toucher à la base de données MySQL).</p>

<p>- Vérification de mises à jour disponibles </p>

<pre>
<code>
wp core check-update
</code>
</pre>

<p>- Mise à jour de Wordpress</p>

<pre>
<code>
wp core update
</code>
</pre>

<p>- Mise à jour de la base de données du site</p>

<pre>
<code>
wp core update-db
</code>
</pre>

<p>- Vérification de la mise à jour des plugins</p>

<pre>
<code>
wp plugin update --all --dry-run
</code>
</pre>

<p>- Mise à jour des plugins</p>

<pre>
<code>
wp plugin update --all
</code>
</pre>

<p>- Même chose pour les thèmes</p>

<pre>
<code>
wp theme update --all --dry-run
wp theme update --all
</code>
</pre>

<p>Le fait de passer en ligne de commande vous fera gagner du temps, plutôt que d'aller vers l'administration et de vérifier un par un vos points de contrôle (plugins, thème, mise à jour WordPress...).</p>

<p>La liste que je vous ai présenté est exhaustive, mais sachez qu'il existe plein d'autres fonctions disponibles (pour les commentaires, les articles, les rôles et permissions, etc...). Il existe d'ailleurs des lignes de commande pour son extension e-commerce, WooCommerce.</p>

<p>Le lien vers le module si vous voulez en savoir plus est ici : <a class="underline" href="https://wp-cli.org/fr/" target="_blank" title="Plugins WordPress">https://wp-cli.org/fr/</a></p>



