# Initiation à Git #
--------------------

## 1. Intro

Git permet à des groupes de travaux / personnes de travailler sur les mêmes projets, documents ou fichiers, généralement du code au même moment et sans que cela ne soit gênant.  

Il est possible d’utiliser git pour une gestion personnel du versionning de fichier, mais le projet a beaucoup évolué de son utilité de base, maintenant il est souvent utilisé pour des projets avec plusieurs membres et plusieurs développeurs.

## 2.	Git en local ##

L’utilisation de git en local va vous permettre de gérer les versions de vos fichiers. Et d’avoir une vue d’ensemble à tout moment sur votre état d’avancement.

Utiliser git sous Windows : [http://windows.github.com](http://windows.github.com/)  
> [Télécharger git](http://git-scm.com/downloads)  
> [Télécharger GUI Client](http://git-scm.com/downloads/guis)

Utiliser git sous Ubuntu : [Git sous Ubuntu](http://doc.ubuntu-fr.org/git)

> Avec la doc Ubuntu, de nombreuses commandes git sont expliquées

**Que Git soit utiliser sous Windows ou Ubuntu, ou tout autre système d'exploitation, les commandes Git restent les mêmes.**
  

>**Git sous linux** :  
>
- il est plus aisé de travailler,  
- plus simple, plus rapide, plus fluide.  
- l’environnement Linux est prévu pour.

## 3. Quelques cas concrets ##

BugTracker publique : `Github` - [https://github.com](https://github.com/)  
BugTracker privé : `Redmine` - [http://doc.ubuntu-fr.org/redmine](http://doc.ubuntu-fr.org/redmine)  
BugTracker privé : `Gitlab` - [http://gitlab.org/](http://gitlab.org/)  

> **Procédure** :
> 
- [https://github.com/gitlabhq/install](https://github.com/gitlabhq/gitlabhq/blob/stable/doc/install/installation.md#5-database)
- [https://github.com/gitlabhq/gitlabhq/tree/5-1-stable/doc](https://github.com/gitlabhq/gitlabhq/tree/5-1-stable/doc)
- [tutorial-setting-up-gitlab-on-debian-6](http://blog.phusion.nl/2012/04/21/tutorial-setting-up-gitlab-on-debian-6/)


## 4. Github initiation

### Se familiariser avec Github ###
On va suivre ce cours : [http://try.github.com](http://try.github.com)  

Vous pouvez ajouter vos collaborateurs sur le projet. Ainsi, ils seront autorisés. (Si des problèmes sont rencontrés, ajouter sa clé publique dans les clés de votre compte).


### Pour générer une clé SSH ###

	# Generate the SSH Key
	sudo -u gitlab -H ssh-keygen -q -N '' -t rsa -f /home/gitlab/.ssh/id_rsa

> Pour en savoir plus : [https://help.github.com/articles/generating-ssh-keys](https://help.github.com/articles/generating-ssh-keys)

## 5. Créer un repository ##

### Création du repository ###
Depuis github, se connecter avec son compte, se rendre sur la page de son profil et cliquer sur l'onglet "Repositories", puis créer un nouveau repository, via le bouton "New".

> Il est possible lors de la création de choisir de créer par défaut ou non le fichier README.md

#### Si le fichier README.md n'est pas créé ####
Une fois le repository créé, il suffit de lancer ces commandes : 

	touch README.md
	git init
	git add README.md
	git commit -m "add file readme"
	git remote add origin git@github.com:NOM_USER_GIT/NOM_REPO.git
	git push -u origin master

#### Si le fichier README.md est déjà créé ####
	git remote add origin git@github.com:Brydjy/test.git
	git push -u origin master


## 6. Cloner un repository déjà existant

Quand le repository est déjà existant, vous pouvez le cloner pour récupérer son contenu, sur github, les repository sont en général public (la partie privée est payante). 

	git clone git@github.com:NOM_USER/NOM_REPO.git

## 7. En plus ##

### Astuce ubuntu : ###
- Install tmux, shell partagé
- Ssh nom_compte@adresseIP
- Tmux –a
- Requiert  tmux et ssh

### Télécharger un fichier tar.gz et et le décomrpesser :  ###
- curl --progress http://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p327.tar.gz | tar xz  
OU
- Wget adresseDuFichier

### Les clés SSH ###
- Pour pouvoir se connecter en SSH, il faut donner sa clé publique et le serveur doit l’ajouter dans son fichier authorized_keys  
- La clé publique se trouve dans le dossier .ssh, elle est générée par la commande suivante :

		sudo -u gitlab -H ssh-keygen -q -N '' -t rsa -f /home/gitlab/.ssh/id_rsa  
- Après on peut se connecter grâce à notre clé pivée sur le serveur distant
-	Faire aussi des opérations GIT

### Editeur de texte : ###
-	Emacs
-	Fichier de config emacs
-	Commande de base

## Erreur Courante ##
**Attention** Sur Ubuntu, quand on crée sa clé sans la commande sudo, il faut faire de même quand clone ou crée des repository.  
Globalement, il est important de retenir, que l'utilisateur est susceptible d'avoir des erreurs s'il essai de clone ou push sur le serveur en utilisant sudo. Dans ce cas il est possible d'avoir une erreur de ce type :   

	Permission denied (publikey)

Pour plus d'explications voir [ici](https://help.github.com/articles/error-permission-denied-publickey)

## Commande pratique ##

Pour configurer basique : [https://help.github.com/articles/set-up-git#platform-windows](https://help.github.com/articles/set-up-git#platform-windows)

**Git init** : Initialiser un git dans le dossier du projet  
**Git add Nom_FICHIER** : permet d’ajouter dans la file d’attente un nouveau fichier (avec « . » on add plusieurs fichiers)  
**Git rm NOM_FICHIER**   
**Git rm -cached Nom_FICHIER** : permet de supprimer l’ajout d’un fichier dans la file d’attente  
**Git commit -m** : Stocker le fichier dans son repository avec un commentaire  
**Git commit --amend** : Changer le message du dernier commit  
**Git remote add**  
**Git remote rm**  
**Git clone ADRESSE_REPO** : Permet de récupérer le contenu d’un repo  
>Ex : git clone git@github.com:Brydjy/test_cesi.git  

**Git push** : Permet d’ajouter des modifications à un repo  
**Git pull** : Permet de mettre à jour son repo local par rapport au repo sur le serveur  
**Git log** : Journal des commits avec tous les changements  
**Git status** : Permet de voir les actions en attente (commit, ajout de fichier, etc)  
**Git diff** : Permet de voir les différences avec notre version actuelle (changement concret)   
**Git diff HEAD** : Permet de voir les différences avec notre dernier commit  
**Git reset fichier** : permet d’annuler l’ajout ou les modifications sur un fichier avant un commit par exemple.  
**Git reset HEAD^** : Annule le dernier commit et revient à l’avant dernier (Seul le commit est retiré de Git ; vos fichiers, eux, restent modifiés.)  
**Git reset  --hard HEAD^** : Annule le dernier commit et les changements dans les différents fichiers et revient à l’état lors de l’avant dernier commit  
**Git revert NUMERO_COMMIT** : Annule le commit portant ce numéro malgré un push (effet inverse)  
**Git checkout ID fichier** : Permet de récupérer une ancienne version du fichier  
**Git branch NOM_BRANCH** : Permet de créer une autre branche pour travailler, une branche temporaire par exemple  
**Git branch** : Permet de visualiser les branches existantes / disponibles (courante avec un * )  
**Git checkout NOM_BRANCH** : Permet de changer de branche   
**Git checkout NOM_FICHIER** : Annuler les modifications d’un fichier avant un commit  
**Git merge NOM_BRANCH** : permet de merger les fichiers depuis la branche souhaitée  


### Préventions ###

Un push est irréversible. Une fois que vos commits sont publiés, il deviendra impossible de les supprimer ou de modifier le message de commit ! Réfléchissez donc à deux fois avant de faire un push. C’est pour cela qu’il est recommandé de ne faire un push qu’une fois par jour, afin de ne pas prendre l’habitude d’envoyer définitivement chacun de vos commits trop vite.  

En effet, il est tout de même possible d’annuler un commit + push, via la commande git revert  NUMERO_COMMIT, ensuite, il suffit de push. 

### Les liens ###

[Infos Git](http://www.grafikart.fr/search?q=git)
[Infos Git](http://www.siteduzero.com/informatique/tutoriels/gerez-vos-codes-source-avec-)
[Git Challenge & Try](http://try.github.com/levels/1/challenges)
[Code School – apprendre avec plaisir](https://www.codeschool.com/users/sign_in)
[La doc (anglais)](http://git-scm.com/doc)  

**Tuto Gitlab :**  

- http://gitlab.org/  
- [Suivre le tuto ici](https://github.com/gitlabhq/gitlabhq/blob/stable/doc/install/installation.md)  
- [Problème connu](https://github.com/gitlabhq/gitlabhq/issues/2535)  
- [Bonne version à suivre](https://github.com/gitlabhq/gitlabhq/blob/4-0-stable/doc/install/installation.md)

