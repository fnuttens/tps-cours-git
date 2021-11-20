---
description: Séance 5 - 22/11/2021
---

# TP - CI

## Mise en place et instructions

Vous aurez besoin pour ce TP d'un compte [GitLab](https://gitlab.com/).

À la fin de cette séance, veillez à ce que :

- votre dépôt git est accessible publiquement
- je sois ajouté comme *maintainer* à votre projet

Vous êtes libre d'ajouter un rapport (fichier versionné ou [wiki](https://docs.gitlab.com/ee/user/project/wiki/)) avec les difficultés rencontrées.

## Configuration de la CI et création des jobs

Forkez le projet [tp-ci](https://gitlab.com/fnuttens/tp-ci).

Il s'agit d'un projet [Node.js](https://nodejs.org/). Vous veillerez donc à utiliser la bonne image docker pour exécuter votre CI.

Faites le nécessaire pour exécuter les commandes suivantes dans la pipeline de CI :

1. installation du projet (`npm install`)
2. lancement des tests (`npm run test`)
3. lancement de l'analyse syntaxique du code (`npm run lint`)
4. affichage d'un message dans la console (`echo...`)

## Stages

Organisez vos jobs en les regroupant en trois catégories :

1. setup : job 1
2. test : jobs 2 + 3
3. end : job 4
