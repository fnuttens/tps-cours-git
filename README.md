---
description: Séance 1 - 27/09/2021
---

# TP - Les commandes de base

## Mise en place et instructions

Vous aurez besoin pour ce TP de [git et git bash](https://gitforwindows.org/).

À la fin de la séance, merci de déposer une archive (ZIP ou équivalent) à [cette adresse](https://cnam-my.sharepoint.com/:f:/g/personal/florent\_nuttens\_lecnam\_net/EunozwiJPz1LhOH6\_lRVJrEBv-f5\_p2-fpXv24t7A\_xm1Q?e=eDgpom), au format **NOM\_prénom\_TP01**, contenant :

* l'intégralité de votre dossier de travail (le dossier masqué .git/ doit être présent)
* un document (PDF, ODF, DOCX, TXT, etc.) contenant les commandes exécutées lors de ce TP

Vous êtes libre d'ajouter à votre rapport les difficultés rencontrées.

## Votre premier dépôt

Créez un dossier pour accueillir votre projet. Placez-y un fichier `index.html` avec le contenu suivant :

```markup
<!DOCTYPE html>
<html>

<head>
	<title>Welcome</title>
</head>

<body>
	<h1>This is a Heading</h1>
	<p>This is a paragraph</p>
</body>

</html>
```

Initialisez un dépôt git dans le dossier. Vous devez obtenir un message similaire à ceci :

```
Initialized empty Git repository in C:/repositories/mon-site/.git/
```

Configurez votre nom et adresse email dans git afin que vos prochains commits soient associés à votre identité. Vous pouvez définir ces paramètres de manière globale à l'aide de l'option `--global`.

{% hint style="info" %}
Si vous avez déjà configuré votre identité de manière globale, alors vous n'avez pas besoin de le faire à nouveau.
{% endhint %}

Affichez l'état du dépôt. Le résultat doit être similaire à ceci :

```
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        index.html

nothing added to commit but untracked files present (use "git add" to track)
```

Ajoutez le fichier `index.html` à l'index git. Consultez à nouveau l'état du dépôt. Le résultat doit être similaire à ceci :

```
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   index.html
```

Enregistrez un nouveau commit à partir des modifications présentes dans l'index. Vous préciserez le message suivant :

> feat: ajoute le fichier index.html

Le résultat suivant devrait s'afficher :

```
[master (root-commit) b063607] feat: ajoute le fichier index.html
 1 file changed, 13 insertions(+)
 create mode 100644 index.html
```

## Questions

Répondez aux questions suivantes dans votre rapport :

1. Deux commits peuvent-ils avoir le même identifiant (hash) ? Si oui, dans quel cas ?
2. Peut-on ajouter en une seule commande tous les fichiers du répertoire de travail à l'index ? Si oui, comment ?
3. Peut-on ajouter un fichier à l'index si celui-ci n'est pas dans le répertoire de travail ? Si oui, comment ?
4. Pensez-vous que certaines entreprises n'ont pas besoin d'utiliser de VCS ? Justifiez votre réponse en donnant quelques exemples. _Ce n'est pas une question piège, la réponse "oui" est admissible tant qu'elle est justifiée_.
5. Une fois un fichier ajouté à l'index, est-il possible de l'en retirer ? Si oui, par quel moyen ?
