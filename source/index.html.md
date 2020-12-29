---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - html

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

# Autre options

```html
<div
	id="intconv-root"
	hide_searchbar="true"
>
</div>
```

Il est possible de masquer la barre de recherche avec l'attribut **hide_searchbar**.

Cela peut permettre d'avoir une interface simplifiée dans un contexte particulier.