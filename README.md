# Git - Versioning et sauvegarde

---

## Installation de git

### Windows

### Mac OS X

Il est recommandé d'utiliser l'installation via `homebrew`.
- installer `homebrew`

Si votre ordinateur ne dispose pas de commande `brew`, suivre la procédure décrite ici : https://brew.sh/index_fr

- installer `git`

```bash
brew install git
```

## Configuration de git

```bash
# A effectuer la première fois
git config --global user.email your@email.com
git config --global user.name "Votre NOM"

# configurer `nano` comme l'éditeur par défaut
git config --global core.editor "nano"
```

---

## Git : fonctionnement élémentaire

https://education.github.com/git-cheat-sheet-education.pdf

---

### Initialiser un nouveau dépot dans le dossier en cours

```bash
# cd mon/dossier/de/travail
git init
```

### Ou cloner un dépot existant
```bash
# Avoir une copie locale de ce dépot
git clone https://github.com/cantoute/cours-git.git

# si vous devez travailler sur le code, (publier vos modifications)
# il est préférable d'utiliser le lien ssh
# il vous permettra d'utiliser l'authentification par clé ssh
git clone git@github.com:cantoute/cours-git.git
```

---

### Mettre à jour le dépot local

```bash
# Opération à effectuer avant de se préparer à valider 
# vos changements dans le dépot (commit)
$ git pull

# Récupérer toutes les branche
$ git pull --all
```

### Avoir un aperçu des éditions *(différences avec le dépôt)*

```bash
$ git diff

# voir les différences avec un autre branche
$ git diff master

# voir les différences avec un autre commit
$ git diff bea30b055a9775fb47d0fba6789fb0cd4fa46540

# voir la différence entre deux commits
$ git diff 5bb67658f74b217f8b8b9c5283a3dbc13be8017a bea30b055a9775fb47d0fba6789fb0cd4fa46540
```

### Les branches
```bash
# Créer une branche et on bascule dans la branche
$ git checkout -b dev/ma-branche
# on les nomme par leur intention
# Ex: fix/button feature/new-function

# liste de toutes les branches locales et met en couleur la branche sur laquelle on se trouve
$ git branch

# Basculer sur une branche existante
$ git checkout master

$ git checkout dev/ma-branche
```
### Indexer un ou des fichiers en prévision d'un `commit`
En anglais le terme utilisé est 'stage'

Cette action est préalable au commit.  Via `git add` on déclare (ajout à l'index) les fichiers qui seront impliqués dans le commit.

```bash
# ajouter un fichier seul
$ git add mon-fichier.txt

# ajouter des fichiers par groupe
$ git add *.txt

# ajouter tous les fichiers du dossier
# (sauf ceux mentionnés dans .gitignore)
$ git add .

# l'opération inverse :
# (utilisez "git restore --staged <fichier>..." pour désindexer)
$ git restore --staged mon-fichier.txt
```


*J'ai l'intention de 'commiter' ce fichier. Prend donc en compte `README.md` dans le commit que je me prépare à effectuer :*
```bash
$ git add README.md
```
```bash
# vous pouvez ensuite vérifier que tout est en ordre
$ git status
Sur la branche dev/ma-branche
Votre branche est à jour avec 'origin/master'.

Modifications qui seront validées :
  (utilisez "git restore --staged <fichier>..." pour désindexer)
        modifié :         README.md

Fichiers non suivis:
  (utilisez "git add <fichier>..." pour inclure dans ce qui sera validé)
```

### Inscrire au dépot les changements indexés (commit)
```bash
$ git commit -m "Message de l'inscription / nom au commit"

# pour saisir le message via l'éditeur (nano/vim/...)
$ git commit

# indexer tous les fichiers déjà suivi (`git add` automatique)
$ git commit -am "Message de l'inscription / nom au commit"
```

### Publier les changements sur le dépot distant
```bash
# envoie le commit sur github par exemple
$ git push
```
---
## Terminal *(Console ou Shell)*

Quelques Commandes shell incontournables

### `pwd` : dossier en cours

```bash
my-account@my-computer:~ $ pwd
/Users/my-account

```

### `ls` : lister le contenu d'un répertoire

```bash
my-account@my-computer:~ $ ls

# inclure les fichiers cachés
my-account@my-computer:~ $ ls -a

# montrer les fichiers cachés et donner une vue détaillé
my-account@my-computer:~ $ ls -al

# tailles des fichiers avec des valeurs humaines (ex: 123k)
my-account@my-computer:~ $ ls -lh *.txt

my-account@my-computer:~ $ ls Desktop/*

```

### `cd` : changer de répertoire courant

```bash
my-account@my-computer:~ $ pwd
/Users/my-account
my-account@my-computer:~ $ cd Desktop
my-account@my-computer:~/Desktop $ pwd
/Users/my-account/Desktop
my-account@my-computer:~/Desktop $ cd ..
my-account@my-computer:~ $ pwd
/Users/my-account

# retourner à la base de son répertoire personnel (home)
my-account@my-computer:~/n-importe-où $ cd
my-account@my-computer:~ $ pwd
/Users/my-account
```

### `mkdir` : création d'un dossier

```bash
my-account@my-computer:~ $ mkdir Démo
my-account@my-computer:~ $ cd Démo
my-account@my-computer:~/Démo $ pwd
/Users/my-account/Démo
```
### `rmdir` : supprimer un dossier vide

```bash
# supprimer un dossier vide
my-account@my-computer:~/Démo $ mkdir toto
my-account@my-computer:~/Démo $ rmdir toto

my-account@my-computer:~/Démo $ mkdir toto2
my-account@my-computer:~/Démo $ touch toto2/empty-file

# supprimer un dossier et tout son contenu
# -r = récursif
# -f = forcer (ne pas demander de confirmation)
my-account@my-computer:~/Démo $ rm -rf toto2
# Attention, cette manipulation ne passe pas par la corbeille,
# en tant que root (administrateur) "rm -rf /" supprimera tout
# et sans vous demander aucune confirmation.
```

### `cp` : copier

### `mv` : renommer / déplacer

### `rm` : supprimer

### `cat` : concaténation de fichier texte
Il permet entre autres de lire un fichier texte en retournant son contenu dans la console.  Souvent utilisé pour rediriger sa sortie vers une autre commande.

### `less` : lire le contenu d’un fichier texte de façon interactive. (utile pour les fichiers longs)

### `grep` : filtrer les lignes d’un fichier texte et de n’afficher que celles correspondant à un motif (pattern)

Il peut être utilisé pour recherche tout fichier contenant un mot.
```bash
$ grep "blabla" *.txt

# récursif (également dans tous les sous dossiers)
$ grep -R "blabla"
```
### `touch` : Création d’un fichier vide
Si le fichier existe, cela actualise la date de modification du fichier.

```bash
antony@dell-aio:~$ touch toto
antony@dell-aio:~$ ls -l toto
-rw-rw-r-- 1 antony antony 0 mai    7 19:04 toto

# 1 minute plus tard
antony@dell-aio:~$ touch toto
antony@dell-aio:~$ ls -l toto
-rw-rw-r-- 1 antony antony 0 mai    7 19:05 toto
```

### `nano` Éditeur de fichier texte en console (simple)

### `vi` / `vim`
Éditeur de fichier texte en console. Vim est plus complexe à prendre en main et sans quelques notions totalement inutilisable, nano est votre ami :) 

- Activer le mode insertion : `i`
- Quitter `vi` et enregistrer les changements :
<span style="border: 1px solid; border-radius: .5ex; padding: 0 2px">`Esc`</span> `:wq`

- Quitter `vi` **sans enregistrer** les changements :
<span style="border: 1px solid; border-radius: .5ex; padding: 0 2px">`Esc`</span> `:q!`

`history` l'historique des commandes saisies

```bash
$ history | grep git
328  git diff
329  git pull --all
330  git diff master
331  git merge master
333  touch demo/.gitkeep
334  git add .
335  git pull --all
336  history | grep git
```
