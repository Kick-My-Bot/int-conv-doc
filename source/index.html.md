---
title: API Reference

search: true
---

# Introduction

Int-conv est une interface conversationelle.

Elle permet de mettre en place un moteur de recherche, pouvant prendre charge des phrases en langage naturel ou des fichiers vocaux, ainsi que de proposer des réponses aux intentions de l'utilisateur.

# Fonctionnement

```html
<div id="intconv-root"></div>
<script src="https://intconv.kmblabs.com/app.js"></script>
```

Tout d'abord, il faut mettre à disposition le point d'entrée de l'application avec une div ayant pour id **intconv-root**.

Le script de l'application doit également être récupéré, après que la div soit chargée dans la DOM.

Ensuite, 2 pages sont accessibles:

- la page d'accueil
- la page des résultats

Lors de l'écriture d'une recherche, des suggestions sont proposées en fonction des éléments déjà entrés par l'utilisateur.

Une fois la recherche envoyée, une redirection est faite vers la page des résultats.

Cette page reprend la barre de recherche, et met à disposition différents filtres pour affiner les résultats.

L'URL est manipulée par la requête de l'utilisateur, et chaque critère est passé en tant que paramètre.

Exemple:

`/offers?localisation.nom_ville=paris&jobname=developer`

# Gestion des pages

```html
<div
	id="intconv-root"
	path="nos-offres"
>
</div>
```

La page d'accueil est affichée par défaut, tant que la page courante sur laquelle est chargée l'application n'est pas celle des résultats.

La page de résultats par défaut est **/offers**, mais il est possible de définir cela avec l'attribut **path**.

Un chargement sur cette URL permettra d'afficher directement les résultats d'une requête.

Il peut s'agir par exemple d'un partage de recherche, permettant de rediriger sur des résultats précis.

```html
<div
	id="intconv-root"
	path="nos-offres"
	prevent_redirect="true"
>
</div>
```

Il est possible d'empêcher la redirection en utilisant l'attribut **prevent_redirect**.

L'URL sera toujours manipulée pour utiliser la page des résultats, mais aucune redirection ne sera faite.

# Wordpress

> Shortcode WordPress à insérer dans le contenu

```
[intconv path="nos-offres" prevent_redirect="true"]
```

> Fonction WordPress à exécuter dans un fichier PHP

```php
do_shortcode( '[intconv path="nos-offres" prevent_redirect="true"]' );
```

Le plugin WordPress est constitué de 2 fichier, à placer dans un dossier (par exemple **/kmblabs**) dans le dossier **/plugins** du thème.

- intconv.php:
	- plugin principal qui définit le shortcode
	- ajoute une div qui intégrera l'application
	- ajoute les feuilles de style de l'application et une police Google
	- ajoute le script pour l'exécution de l'application

- part-intconv.php:
	- appelle le shortcode à l'interieur d'une section du thème
	- permet d'encapsuler l'application dans certains éléments du thème à réutiliser à différents endroits (modifiable si besoin)

Il est alors possible d'utiliser le shortcode directement depuis le **contenu WordPress**, via l'appel de la fonction **do_shortcode** ou bien en **intégrant le fragment** mis à disposition.

# Autre options

## Cacher la barre de recherche

```html
<div
	id="intconv-root"
	hide_searchbar="true"
>
</div>
```

Il est possible de masquer la barre de recherche avec l'attribut **hide_searchbar**.

## Cacher les filtres de recherche

```html
<div
		id="intconv-root"
		hide_filters="true"
>
</div>
```

Il est possible de masquer les filtres de recherche avec l'attribut **hide_filters**.

## Limiter le nombre d'offres en résultat

```html
<div
		id="intconv-root"
		number_of_offers_limit=3
>
</div>
```

Il est possible de limiter le nombre d'offres en résultat de recherche avec l'attribut **number_of_offers_limit**.

La limite peut se trouver entre 1 et 10.

## Ne pas afficher la page d'accueil

```html
<div
		id="intconv-root"
		no_landing="true"
>
</div>
```

Il est possible de ne pas afficher la page d'accuiel avec l'attribut **no_landing**.

## Filtrer les résultats

```html
<div
		id="intconv-root"
		search_filters="jobname=audit"
>
</div>
```

Il est possible de filtrer les résultats avec l'attribut **search_filters**.

Cela permet de filtrer les résultats de recherche selon une requête précise, au format **clé=valeur**.

Afin d'obtenir la requête désirée, il est possible de manipuler l'application pour obtenir une combinaison de résultats, et ainsi utiliser l'URL obtenue pour l'utiliser comme valeur de l'attribut.

## Ajouter un bouton pour rediriger vers une page d'offres

```html
<div
		id="intconv-root"
		redirect_to_offers="https://exemple-site.com/nos-offres?skills=audit"
>
</div>
```

Il est possible d'ajouter un bouton afin de rediriger l'utilisateur vers une page d'offres avec l'attribut **redirect_to_offers**.

L'application doit être présente sur cette page.

Des paramètres peuvent être fournies à l'application en définissant l'URL de recherche souhaitée.

## Personnaliser le titre

```html
<div
		id="intconv-root"
		static_title="true"
		custom_title="Bonjour <br/>à vous !"
>
</div>
```

Il est possible de rendre le titre de l'accueil statique avec l'attribut **static_title**.

Il est également possible de modifier sa valeur avec l'attribut **custom_title**.

Ce changement peut prendre en compte des éléments HTML, afin de faire du formatage de texte.

L'attribut **custom_title** n'est utilisé que si le titre est statique.