---
description: Séance 6 - 05/12/2022
---

# TP - Commandes avancées

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
