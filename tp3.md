# tp3-korichi-petit


## EXERCICE 1 : Commande de Base

#### 1. Quel sont les 5 derniers paquets installées sur votre machine ?
```bash
dpkg -l | tail -5
ls -ltr /var/lib/dpkg/info/*.list | tail -5
```

#### 2. Utiliser dpkg et apt pour compter le nombre de paquets installés. Comment explique-t-on la petite différence de comptage ?
```bash
Dpkg – l | wc -l
	4391
  
apt list - - installed | wc -l
	4179
```

#### 3. Combien de paquets sont disponibles en téléchargement ?
```bash
apt list - - installed | wc -l
  53521
```

#### 4. Créer un alias « maj » qui met à jour le système.
```bash
nano .bash_aliases
	alias maj='sudo apt upgrade'
```

#### 5. A quoi sert le paquet fortunes ? Installez-le.
```bash
Sudo apt install fortunes
fortunes
		retourne petites phrases
```

#### 6. Quel paquets proposent de jouer au sudoku ?
```bash
Sudo apt search sudoku
		Sorting... Fait
		Full Text Search... Fait
		fltk1.1-games/trusty 1.1.10-17 i386
 		 Boîte à outils Fast Light - exemples de jeux : jeux de dames, sudoku

		fltk1.3-games/trusty 1.3.2-4 i386
 		 Boîte à outils Fast Light - exemples de jeux : jeux de dames, sudoku

		gnome-sudoku/trusty-updates,now 1:3.10.2-0ubuntu3.1 all [residual-config]
		  Casse-tête Sudoku pour GNOME

		hitori/trusty 0.4.0-1 i386
		  Jeu de puzzle logique similaire au sudoku

		ksudoku/trusty-updates 4:4.13.3-0ubuntu0.1 i386
		  Jeu et Solveur de Sudoku
      
		sudoku/trusty 1.0.1-5 i386
 		 Sudoku en mode console

		texlive-games/trusty 2013.20140215-2 all
 		 TeX Live : Composition de jeux

		vdr-plugin-sudoku/trusty 0.3.5-17 i386
		  Greffon VDR pour générer et résoudre des Sudokus
```

#### 7. Lister les derniers paquets installés explicitement avec la commande apt install.
```bash
grep "Commandline: apt install" /var/log/apt/history.log
		Commandline: apt install fortunes
		Commandline: apt install sudoku
```


## EXERCICE 2 : 

A partir de quel paquet est installée la commande ls? Comment obtenir cette information en une seule commande, pour n’importe quel programme (indice : la réponse est dans le poly de cours 2, dans la liste des commandes utiles)? Utilisez la réponse à pour écrire un script appelé origine-commande (sans l’extension.sh) prenant en argument le nom d’une commande, et indiquant quel paquet l’a installée.
```bash
Nano origine-commande
		dpkg -S $(which $1)
```


## EXERCICE 3 : 

Ecrire une commande qui affiche ”INSTALLÉ” ou ”NON INSTALLÉ” selon le nom et le statut du package spécifié dans cette commande.

```bash
apt list --installed | grep -q nom_paquet && if [ $? -eq 0 ]; then echo "Non Installé" ; else echo "installé"; fi
```


## EXERCICE 4 :

Lister les programmes livrés avec coreutils. A quoi sert la commande '[' et comment afficher ce qu’elle retourne ?
```bash
dpkg -L coreutils | rev | cut -d '/' -f 1 | rev | cut -d '.' -f 1
```


## EXERCICE 5 :

Installez le paquet emacs à l’aide de la version graphique d’aptitude.


## EXERCICE 6 : 

#### 1. Installer la version Oracle de Java (avec l’ajout des PPA)
```bash
sudo add-apt-repository ppa:linuxuprising/java
sudo apt update
sudo apt install oracle-java11-installer
```

#### 2. Vérifiez qu’un nouveau fichier a été créé dans/etc/apt/sources.list.d. Que contient-il ?

