---
description: Séance 4 - 07/11/2022
---

# TP - GitLab

## Mise en place et instructions

Vous aurez besoin pour ce TP de [git et git bash](https://gitforwindows.org/).

## Démarrage

1. Connectez-vous sur [GitLab](https://gitlab.com/) et faites un _fork_ du projet [tp-rebase-2021](https://gitlab.com/fnuttens/tp-rebase-2021)
2. Localement, dans le dossier de votre TP "rebase" de la dernière séance (ou un nouveau dossier créé à l'occasion d'un clone si vous ne l'avez plus), ajoutez un remote `personal` qui pointe vers le fork que vous venez de créer
3. Donnez-moi le rôle _Maintainer_ (@fnuttens) sur ce projet

## Votre branche

1. Créez une issue nommée "Modification du readme"
2. Créez une branche nommée `X-customize-readme` (`X` étant le numéro de l'issue créée précédemment) et placez-vous dessus
3. Ajoutez le texte de votre choix dans le fichier README.md, puis commitez ce changement
4. Essayez de pusher votre branche sur le remote `origin`. Que constatez-vous ?
5. Pushez votre branche sur le remote `personal`

### Merge Request

1. Créez une MR partant de votre branche et ciblant `main` (⚠️ visez bien le `main` de votre fork, pas celui du projet original)
2. Affectez la MR à l'un(e) de vos camarades. Pensez à lui donner le rôle de _Maintainer_ sur votre fork.
3. Demandez à votre camarade d'ajouter au moins un commentaire dans le code de votre MR
4. Répondez au commentaire puis demandez à votre camarade de merger votre branche
5. Que constatez-vous à propos de vos branches ? De votre issue ?
6. Mettez à jour votre branche `main` en local

## Rapport

Créez une nouvelle issue "Ajout du rapport". Sur une nouvelle branche, ajoutez votre rapport dans votre projet, commitez-le et faites de nouveau une MR à votre camarade, qui devra merger votre branche sur `main`.

{% hint style="info" %}
Comme je vous demande aujourd'hui de versionner votre rapport, je vous conseille d'utiliser un _markup language_ tel que Markdown ou AsciiDoc pour le réaliser. Certain·e·s d'entre vous ont peut-être déjà constaté qu'un fichier Word dans git ce n'était pas très pratique 😉
{% endhint %}
