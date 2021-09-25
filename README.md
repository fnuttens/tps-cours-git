---
description: Séance 0 - 27/09/2021
---

# TP - Les commandes de base

## Mise en place et instructions

Vous aurez besoin pour ce TP de [git et git bash](https://gitforwindows.org/).

À la fin de la séance, merci de déposer une archive \(ZIP ou équivalent\) à [cette adresse](https://drive.google.com/drive/folders/1Lye4CJje6IBkL5yYrlCLS3KILL1MhJfl?usp=sharing), au format **NOM\_prénom\_TP01**, contenant :

* l'intégralité de votre dossier de travail \(le dossier masqué .git/ doit être présent\)
* un document \(PDF, ODF, DOCX, TXT, etc.\) contenant les commandes exécutées lors de ce TP

Vous êtes libre d'ajouter à votre rapport les difficultés rencontrées.

## Votre premier dépôt

Créez un dossier pour accueillir votre projet. Placez-y un fichier `index.html` avec le contenu suivant :

```text
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

```text
Initialized empty Git repository in C:/repositories/mon-site/.git/
```

Configurez votre nom et adresse email dans git afin que vos prochains commits soient associés à votre identité. Vous pouvez définir ces paramètres de manière globale à l'aide de l'option `--global`.

