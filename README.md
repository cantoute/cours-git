# Git - Versioning et sauvegarde

## Git : fonctionnement élémentaire

https://education.github.com/git-cheat-sheet-education.pdf

---
### Initialiser un nouveau dépot dans le dossier en cours

```bash
$ git init
```

### Ou cloner un dépot existant
```bash
# Avoir une copie locale de ce dépot
$ git clone https://github.com/cantoute/cours-git.git
```

---

### Synchroniser le dépot local
```bash
# Opération à effectuer avant de se préparer à valider 
# vos changements dans le dépot (commit)

$ git pull

# Récupérer toutes les branche (recommandé sauf sur les projets énormes)
$ git pull --all
```

### Avoir un aperçu des différences avec le dépot

```bash
$ git diff
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
$ git commit -m "Message de l'inscription / Donner un nom au commit"

# pour saisir le message via un éditeur (nano/vim/...)
$ git commit
```

### Publier les changements sur le dépot distant
```bash
# envoie le commit sur github par exemple
$ git push
```
---
## Terminal
Aussi nommé Console ou Shell

TODO

