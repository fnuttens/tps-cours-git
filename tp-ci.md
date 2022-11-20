---
description: Séance 5 - 21/11/2022
---

# TP - CI

## Mise en place et instructions

Vous aurez besoin pour ce TP d'un compte [GitLab](https://gitlab.com/).

À la fin de cette séance, veillez à ce que :

* votre dépôt git fasse partie du groupe [fip1a2022](https://gitlab.com/fip1a2022) et soit accessible publiquement
* je sois ajouté comme _maintainer_ à votre projet

Vous êtes libre d'ajouter un rapport (fichier versionné ou [wiki](https://docs.gitlab.com/ee/user/project/wiki/)) avec les difficultés rencontrées.

## Configuration de la CI et création des jobs

Demandez l'accès au groupe [fip1a2022](https://gitlab.com/fip1a2022). Forkez ensuite le projet [tp-ci](https://gitlab.com/fip1a2022/tp-ci).

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
