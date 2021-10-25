---
description: Séance 3 - 25/10/2021
---

# TP - Rebase

## Mise en place et instructions

Vous aurez besoin pour ce TP de [git et git bash](https://gitforwindows.org).

À la fin de la séance, merci de déposer une archive (ZIP ou équivalent) à [cette adresse](https://drive.google.com/drive/folders/1lfuJkouZb7\_GU7hc6E4Wxr64gZ6eAkUj?usp=sharing), au format **NOM\_prénom\_TP03**, contenant :

* l'intégralité de votre dossier de travail (le dossier masqué .git/ doit être présent)
* un document (PDF, ODF, DOCX, TXT, etc.) contenant les commandes exécutées lors de ce TP

Vous êtes libre d'ajouter à votre rapport les difficultés rencontrées.

## Gérer efficacement les branches

Récupérez en local le dépôt suivant avec ses branches :

```
git clone https://gitlab.com/fnuttens/tp-rebase-2021.git
cd tp-rebase-2021
git switch ajout-styles
git switch improve-doc
git switch modification-textes
git switch main
```

{% hint style="info" %}
Vous pouvez trouver un aperçu du graphe du dépôt à [cette adresse](https://gitlab.com/fnuttens/tp-rebase-2021/-/network/main).
{% endhint %}

### On démarre doucement

On merge d'abord la branche `improve-doc` dans `main`. En sachant que cette dernière n'a pas évolué depuis la création de `improve-doc`, utilisez la méthode qui vous paraît la plus adaptée. **Expliquez votre choix**.

### _So far so good_

Il est très probable que vous n'ayez pas rencontré de problème jusqu'ici. Si ce n'est pas le cas, alors je vous invite à me faire signe 🙂

On décide ensuite de merger la branche `modification-textes` dans `main`. On pourrait utiliser la commande merge, mais on souhaite conserver l'historique le plus linéaire possible. Il s'agit donc de rebaser notre branche sur `main`.

Donnez la ou les commandes que vous utilisez. Le résultat devrait être sensiblement similaire à celui-ci :

```
First, rewinding head to replay your work on top of it...
Applying: feat(index): modify paragraph content
Applying: feat(index): rename page title
```

{% hint style="info" %}
En cas de problème, contactez-moi immédiatement. Vous pourriez être bloqué pour la suite du TP.
{% endhint %}

Utilisez la commande adéquate pour vérifier la linéarité de votre branche `main`. Vous pouvez constater que le commit parent de votre branche est désormais celui intitulé `docs: add working instructions`.

Vous pouvez désormais rapatrier les modifications de la branche courante dans `main`.

### Un poil plus technique

Placez-vous sur la dernière branche à merger : `ajout-styles`, et rebasez-là sur la branche `main`.

Constatez puis expliquez le résultat suivant :

```
First, rewinding head to replay your work on top of it...
Applying: feat(index): add some colors
Using index info to reconstruct a base tree...
M       index.html
Falling back to patching base and 3-way merge...
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
error: Failed to merge in the changes.
Patch failed at 0001 feat(index): add some colors
The copy of the patch that failed is found in: .git/rebase-apply/patch
```

Résolvez le problème en respectant le contenu d'origine du commit en cours d'application :

* Conservez le nouveau titre de la page
* Conservez le nouveau texte du paragraphe
* Veillez à ce que le texte puisse s'afficher en bleu
* Le fichier CSS doit être inclus dans la page HTML

Validez puis passez à la suite. Lorsqu'un autre conflit survient, veillez à :

* Conservez le nouveau texte du paragraphe
* Veillez à ce que le texte puisse s'afficher en bleu et que la classe `text` soit bien appliquée

Validez et passez à la suite. Un nouveau conflit se produit lors de l'application du commit `feat(index): rename page title`. Cette fois, on constate que le conflit se produit sur le titre de la page HTML. Or, celui-ci a déjà été modifié sur une autre branche, et ce commit n'a plus de raison d'être. Ne l'appliquez pas et terminez le rebase.

Enfin, mergez la branche `ajout-styles` dans `main`.

### Checklist

Vérifiez les points suivants :

* [ ] Le fichier index.html correspond à :

```html
<!DOCTYPE html>
<html>
<head>
    <title>TP Git - Rebase</title>
    <link href="styles.css" rel="stylesheet" type="text/css">
</head>
<body>
    <h1>This is a Heading</h1>
    <p class="blue text">Git c'est merveilleux</p>
</body>
</html>
```

* [ ] La commande `git log --graph --oneline` donne le résultat suivant (les identifiants seront différents) :

```
* cd32090 (HEAD -> main, ajout-styles) feat(index): add text class to uniformize text displaying
* 3dbbe33 feat(index): add some colors
* c371aad (modification-textes) feat(index): rename page title
* 73f0549 feat(index): modify paragraph content
* cba676c (origin/improve-doc, improve-doc) docs: add working instructions
* c36d817 (origin/main, origin/HEAD) docs: add README
* aad15dc feat: add index page
```

## Rebase interactif

Clonez à nouveau le projet, dans un nouveau dossier. Par exemple :

```
cd ..
git clone https://gitlab.com/fnuttens/tp-rebase-2021.git tp-rebase-interactif
cd tp-rebase-interactif
git switch ajout-styles
git switch improve-doc
git switch modification-textes
git switch main
```

Mergez la branche `improve-doc` dans `main`.

Placez-vous sur la branche `modification-textes`, puis utilisez le mode interactif pour rebaser cette branche sur `main`. Inversez l'ordre des commits (indiquez précisément ce que vous avez fait pour). Enfin, mergez dans `main`.

Utilisez le rebase interactif pour rebaser `ajout-styles` sur `main`. Vous veillerez à :

* ne pas appliquer le commit `feat(index): rename page title` provenant de cette branche
* fusionner les commits `feat(index): add some colors` et `feat(index): add text class to uniformize text displaying`.

Enfin, mergez le tout dans `main`.

### Checklist

* [ ] La commande `git log --graph --oneline` donne le résultat suivant :

```
* b3166ef (HEAD -> main, ajout-styles) feat(index): add some colors
* 211cd8a (modification-textes) feat(index): modify paragraph content
* 434ee5c feat(index): rename page title
* cba676c (origin/improve-doc, improve-doc) docs: add working instructions
* c36d817 (origin/main, origin/HEAD) docs: add README
* aad15dc feat: add index page
```

## Questions

1. Quels sont les principaux cas d'utilisation du mode interactif ?
2. Dans quel cas ne devrait-on pas utiliser la commande rebase ?
3. Que pensez-vous de l'utilisation du mode interactif de rebase ?
