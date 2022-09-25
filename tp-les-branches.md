---
description: Séance 2 - 11/10/2021
---

# TP - Les branches

## Mise en place et instructions

Vous aurez besoin pour ce TP de [git et git bash](https://gitforwindows.org/).

À la fin de la séance, merci de déposer une archive (ZIP ou équivalent) à [cette adresse](https://cnam-my.sharepoint.com/:f:/g/personal/florent\_nuttens\_lecnam\_net/Evn3EStRbyBDo9w5i9kZ75oBJE8jFl123EGm9KGyNuEAdA?e=O6FlfX), au format **NOM\_prénom\_TP02**, contenant :

* l'intégralité de votre dossier de travail (le dossier masqué .git/ doit être présent)
* un document (PDF, ODF, DOCX, TXT, etc.) contenant les commandes exécutées lors de ce TP

Vous êtes libre d'ajouter à votre rapport les difficultés rencontrées.

## Enrichir le projet de nouvelles fonctionnalités

Reprenez le projet du précédent TP.

{% hint style="info" %}
Vous pouvez copier votre répertoire de travail pour être en mesure de recommencer si besoin.
{% endhint %}

### Créer des _feature branches_

On souhaite apporter deux évolutions à notre projet. Pour ce faire, on utilisera les deux branches suivantes :

* `ajout-styles`
* `modification-textes`

Créez la première branche puis faites-en votre branche courante. Ajoutez ensuite un fichier `styles.css` avec le contenu suivant :

```css
p .blue {
	color: "blue"
}
```

Dans le fichier `index.html`, affectez la classe `blue` au paragraphe. Votre fichier doit normalement ressembler à ceci :

```html
<!DOCTYPE html>
<html>

<head>
	<title>Welcome</title>
</head>

<body>
	<h1>This is a Heading</h1>
	<p class="blue">This is a paragraph</p>
</body>

</html>
```

Commitez ce changement en indiquant un message approprié.

En parallèle, on souhaite changer le texte de notre fichier. Placez-vous sur la branche `master`.

{% hint style="info" %}
Lorsque vous consultez l'historique des commits depuis cette branche, vous ne devez pas voir le dernier commit concernant l'ajout des styles, puisque celui-ci appartient à une branche différente. **Vérifiez que vous êtes bien dans cette situation.**
{% endhint %}

Créez la branche `modification-textes` puis faites-en votre branche courante. Remplacez le contenu du paragraphe par le texte suivant :

> Git c'est merveilleux

Votre fichier `index.html` doit ressembler à ceci :

```html
<!DOCTYPE html>
<html>

<head>
	<title>Welcome</title>
</head>

<body>
	<h1>This is a Heading</h1>
	<p>Git c'est merveilleux</p>
</body>

</html>
```

Commitez ce changement. Modifiez ensuite le titre de la page avec le texte suivant :

> TP Git

Le fichier se présente maintenant comme ceci :

```html
<!DOCTYPE html>
<html>

<head>
	<title>TP Git</title>
</head>

<body>
	<h1>This is a Heading</h1>
	<p>Git c'est merveilleux</p>
</body>

</html>
```

Commitez ce nouveau changement.

### Rapatrier le travail sur la branche `master`

Une fois le travail sur chaque branche terminé, on souhaite voir ce dernier incorporé à la branche principale.

Placez-vous sur `master`. L'historique des commits ne présente qu'un seul résultat à ce moment de l'exercice. Nous allons d'abord rapatrier les changements de la branche `modification-textes`.

Utilisez la commande appropriée pour fusionner cette branche dans la branche master. Le résultat de cette commande est le suivant :

```
Updating 8ce658a..43330ba
Fast-forward
 index.html | 4 ++--
 1 file changed, 2 insertions(+), 2 deletions(-)
```

En consultant l'historique de la branche `master`, vous constaterez que de nouveaux commits sont apparus. En ouvrant le fichier `index.html`, vous verrez que les textes sont bien à jour.

Tentez ensuite de rapatrier le commit de la branche `ajout-styles`. Le message d'erreur suivant apparaît :

```
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

Observez ce message d'erreur, puis l'état du dépôt :

```
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        styles.css

no changes added to commit (use "git add" and/or "git commit -a")
```

Un conflit s'est produit lors de la fusion des branches. Ouvrez le fichier `index.html` afin d'observer les parties du code que git n'a pas réussi à fusionner.

Le conflit se présente comme suit :

```html
<!DOCTYPE html>
<html>
<head>
    <title>TP Git</title>
</head>
<body>
    <h1>This is a Heading</h1>
<<<<<<< HEAD
    <p>Git c'est merveilleux</p>
=======
    <p class="blue">This is a paragraph</p>
>>>>>>> ajout-styles
</body>
</html>
```

{% hint style="info" %}
`HEAD` correspond à l'état du dépôt lors du dernier commit valide de la branche. On retrouve donc le texte original, puisque la branche `modification-textes` a déjà été mergée dans master.

La partie sous la ligne `=======` correspond à l'état de la branche que l'on tente de fusionner.
{% endhint %}

Résolvez le conflit de manière intelligente : on souhaite conserver le nouveau texte, mais également la classe ajoutée. En utilisant la commande `git log --graph`, vous devriez observer un résultat très similaire à celui-ci :

```
*   commit f8f53f4d023fed26acf6dae999beea433448f4da (HEAD -> master)
|\  Merge: 43330ba db77cf5
| | Author: Florent Nuttens <fnuttens@dabao.fr>
| | Date:   Sun Sep 23 23:47:46 2018 +0200
| |
| |     Commit de fusion de la branche ajout-styles dans master
| |
| * commit db77cf58b91adcaf6e175615b3b8afb4506cda9e (ajout-styles)
| | Author: Florent Nuttens <fnuttens@dabao.fr>
| | Date:   Sun Sep 23 23:27:39 2018 +0200
| |
| |     Ajout des styles
| |
* | commit 43330ba53e6859da860cd9ecb932c5d39bdd84c5 (modification-textes)
| | Author: Florent Nuttens <fnuttens@dabao.fr>
| | Date:   Sun Sep 23 23:29:39 2018 +0200
| |
| |     Modification du titre de la page
| |
* | commit ce5bbaa05924fc7371b93e31740a388fb9ff38ee
|/  Author: Florent Nuttens <fnuttens@dabao.fr>
|   Date:   Sun Sep 23 23:29:17 2018 +0200
|
|       Modification du paragraphe
|
* commit 8ce658a80f605415a3104614874d8497132a6ec5
  Author: Florent Nuttens <fnuttens@dabao.fr>
  Date:   Sun Sep 23 11:39:51 2018 +0200

      Ajout du fichier index.html
```

Vous savez désormais travailler avec les branches, et êtes en mesure de rapatrier les changements sur la branche principale !

### Partager votre projet

Essayez de publier votre projet (avec les trois branches) sur [GitLab](https://about.gitlab.com/). Ajoutez-moi (`@fnuttens`) comme [membre](https://docs.gitlab.com/ee/user/project/members/index.html#add-users-to-a-project) de votre projet avec le [rôle](https://docs.gitlab.com/ee/user/permissions.html) de `Maintainer`. Vous veillerez également à mentionner l'URL de votre dépôt dans votre rapport.

### Nettoyer votre dépôt local

Les branches de travail ayant été mergées sur `master`, elles ne devraient plus vous êtes utiles. Supprimez-les. La commande `git branch` ne devrait alors plus vous afficher que la branche `master`.

{% hint style="info" %}
Veillez à conserver les branches de travail sur GitLab.
{% endhint %}

## Questions

Dans votre rapport, répondez aux questions suivantes :

1. Après avoir effectué le premier merge, il était question de `Fast-forward` dans le log. Expliquez ce que cela signifie.
2. Expliquez brièvement pourquoi il y a eu un conflit lors du second merge.
3. Après avoir supprimé des branches locales, pouvez-vous les récupérer ? Si oui, comment ? Si non, pourquoi ?
4. Que pensez-vous du graph de votre projet visible sur GitLab (sous `Repository`/`Graph`) ?
