# cours-git

//////// sur le fichier même

* git add readme.md = j'ai l'intiention de commiter ce fichier. prend donc en compte le readme dans le prochain commit

* git commit = donner un nom au commit 
* git commit -m = "donner un nom au commit" (sans passer par un éditeur)

* git push = envoie le commit sur github

* git diff = permet de voir les modifications qui ont été réalisées 

* git pull = permet d'ajouter toutes les modifications du document initial (celui depuis lequel le clone a été fait)

* git checkout -b dev/diallo = on créer une branche et on bascule dans la branche (on les appels par leurs objectfs (ex: fix/button broken. un slash = un dossier))

*git branch = liste de toutes les branches et met en couleur la branche sur laquelle on se trouve

* git checkout master = retourner vers la branche master

* git checkout dev/diallo = retourner vers la branche dev/diallo

* git checkout 
ces commandes s’effectuent en bash

# quand le ficheier affiche un U = fichier créer
# quand le fichier affiche un M = fichier modifier
# quand le fichier afdfiche un A = c'est un fichier qui est en attente d'être ajouté
# La branche démarre à partir du dernier commit

///////// gestion des fichiers 


mkdir projet = crée un nouveau dossier nommé projet

cd projet = ouvre le dossier projet

git clone https://github.com/cantoute/cours-git.git = clone le fichier lié au lien 

cat README.MD = ouvre le fichier dans le terminal en lecture seule

Pour avoir une copie locale du repos :

```bash
$ cd to/where/you/want # move to this dir - projects ?
$ git clone https://github.com/cantoute/cours-git.git
```
