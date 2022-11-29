---
description: Séance 6 - 05/12/2022
---

# TP - Commandes avancées

À la fin de la séance, merci de déposer l'archive de votre rapport à [cette adresse](https://cnam-my.sharepoint.com/:f:/g/personal/florent\_nuttens\_lecnam\_net/EjwtmE1eCzZIraUfqprB0rcBY95SaOaCxLFgchrqs5F1rg), au format **NOM\_prénom\_TP06**.

## Indexation avancée

Reprenez le dépôt [tp-rebase-2021](https://gitlab.com/fnuttens/tp-rebase-2021) dans sa forme terminée, c'est-à-dire avec toutes les modifications incorporées dans la branche `main`.

Si vous ne l'avez plus, vous pouvez éventuellement créer un nouveau dépôt et faire un commit avec les fichiers suivants :

{% code title="README.md" %}
```markdown
# La phase "compliquée" commence ici !

Vous venez de merger la branche `improve-doc` dans `main`.

Le travail sur les branches `ajout-styles` et `modification-textes` est terminé. Vous souhaitez donc logiquement le rapatrier sur la branche `main`.

Mais surprise ! Cette dernière a changé depuis la dernière fois... Vous pourriez utiliser la commande merge, mais vous vous souvenez du cours sur le rebase 😉
```
{% endcode %}

{% code title="index.html" %}
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
{% endcode %}

{% code title="styles.css" %}
```css
p .blue {
	color: "blue"
}

.text {
	font-size: 16px
}
```
{% endcode %}

En vue d'introduire plus de classes CSS par la suite, vous décidez de renommer `.text` en `.regular-text`. On vous a récemment parlé de la commande `sed` qui permet de faire des éditions simples dans plusieurs fichiers à la fois; vous décidez donc de l'utiliser via `git bash` :

```shell
> sed -i 's/text/regular-text/g' *
```

En consultant le statut du dépôt puis le `diff`, vous vous apercevez que deux occurrences du mot _text_ ont été modifiées alors que ce n'est pas ce que vous cherchez à faire.

Afin de ne garder que les modifications souhaitées (renommage de la classe CSS `.text`), utilisez le mode `patch` de la commande `git restore`.

{% hint style="warning" %}
Vous veillerez à prendre une capture d'écran de chaque commande que vous utilisez dans ce mode interactif.
{% endhint %}

## `git log`

Dans cette partie vous allez étudier l'historique de [reveal.js](https://revealjs.com/), un framework permettant de faire des présentations 2D en HTML. Commencez par cloner le [dépôt](https://github.com/hakimel/reveal.js) sur votre poste.

### Pretty format

Votre première tâche est de personnaliser l'affichage de `git log` pour qu'il soit lisible tout en donnant assez d'informations sur chaque commit. Vous veillerez à faire apparaître :

* le graphe
* le hash du commit en version abrégée
* le nom de l'auteur
* la date relative de création du commit

En dehors de ces contraintes, vous êtes libre de définir le format que vous souhaitez (données supplémentaires, ordre d'apparition, couleur). Soyez créatif !

{% hint style="info" %}
`git help log` est votre ami.&#x20;
{% endhint %}

### Git comme base de données

Donnez les commandes permettant de lister :

1. les commits introduits dans la branche `master` qui ne font pas partie du tag `4.4.0`
2. les commits de merge appartenant à `4.3.1` mais pas `4.3.0`
3. les commits non issus d'un merge dont le message contient le mot "typo"

Au total, combien de personnes ont participé au dépôt (nombre de committeurs) ? Donnez la commande `git log` qui vous a aidé et expliquez votre manière de procéder.

Établissez le classement (top 10) des contributeurs les plus prolifiques. Vous ne considérerez que la branche `master` et les commits non issus d'un merge. Comme avant, vous donnerez la commande `git log` utilisée et le cheminement de votre calcul.

{% hint style="info" %}
Afin de vérifier vos résultats, vous pouvez consulter cette [page](https://github.com/hakimel/reveal.js/graphs/contributors).

Si vous n'aboutissez pas aux chiffres exacts, pas de panique ! GitHub procède à un comptage plus fin qui exclut notamment les comptes gérés par des _bots_.
{% endhint %}

## Questions

1. Quelle commande permet de supprimer les quatre derniers commits de la branche ?
2. Quelle est la différence entre une stash et un patch ? Quelle commande utiliseriez-vous pour produire un patch à partir d'une stash ?
3. Quelle différence existe-t-il entre `git reset --soft` et `--mixed` ? Dans quel(s) cas utiliseriez-vous un mode plutôt que l'autre ?
4. Dans quelles conditions est-il possible de modifier un commit via la commande `git commit` ?
5. Après un _rebase_, la synchronisation avec le dépôt _remote_ échoue. Expliquez pourquoi et donnez la bonne commande à exécuter.
6. Quelle commande permet d'afficher les statistiques de modification de l'index ?
