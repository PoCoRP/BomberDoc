# GameManager.gd

> Ce script permet de gérer les instances du jeu : la maze, le(s) joueur(s), les bonus, les bombes...
	>Il permet de lancer les parties et les différents écrans de transitions entre les parties. C'est le coeur du jeu.

**Extends:** [Node]


## Variables

#### Déclaration des différentes scènes en les chargeant depuis un path
 - Chargement de la scène d'accueil : <br/>
		||  **var accueil_scene**<br/>
---		
 - Chargement de la scène de fin de partie/niveau : <br/>
		||  **var endofgame_scene**<br/>
---		
 - Chargement de la scène de maze : <br/>
		||  **var maze_scene** <br/>
---
#### Déclaration des différentes instanciations liées aux scènes
 - Instance de l'écran d'accueil : <br/>
		||  **var accueil_instance** <br/>
---		
 - Instance de fin de partie/niveau : <br/>
		||  **var endofgame_instance**<br/>
---		
 -  Instance de la maze : <br/>
		||  **var maze_instance** <br/>
---

#### Déclaration des variables utiles à la maze

 - Difficulté de la maze pour le mode solo initialisée à 0.1 : <br/>
		||  **var maze_difficulty**<br/>
---		
 -  Nombre de joueur pouvant intéragir initialisé à 1 : <br/>
		||  **var nb_player** <br/>
---
 -  variable du score du joueur en mode solo initialisé à 0 : <br/>
		||  **var player_score** <br/>
---

## Fonctions

#### Scènes

- Lance une instance du splash screen (écran d'accueil) en fils du GameManager. Affiche cette instance : <br/>
			|| **func ready()** <br/>
---
#### Getters

- Retourne la valeur de la variable maze_difficulty : <br/>
			|| **func get_difficulty()** <br/>
---			
- Retourne la valeur de la variable nb_player : <br/>
			|| **func get_nbPlayer()** <br/>
---

#### Setters
- Met à jour la valeur de la variable nb_player :<br/>
		  || **func set_nb_player(nbPlayer)** <br/>
---
- Fonction permettant d'incrémenter le score en fonction des actions du joueur (Il marque 10 points pour un mur cassé, 30 points pour un bonus attrapé, 60 points pour un ennemi tué et 100 points pour la victoire sur un niveau) :<br/>
		  || **func change_score(action)** <br/>
---
#### Constructeurs 

 - Permet d'instancier et d'afficher la maze : <br/>
		||  **func new_maze()**<br/>
---		
 -  Permet d'instancier et d'afficher l'écran d'accueil (après une fin de partie) : <br/>
		||  **func retour_accueil()** <br/>
---
 -  Permet d'instancier et d'afficher l'écran de défaite en solo : <br/>
		||  **func defeat()** <br/>
---
-  Permet d'instancier et d'afficher l'écran de victoire en solo : <br/>
		||  **func victory()** <br/>
---		
-  Permet d'instancier et d'afficher l'écran de fin de partie multi (elle prend en paramètre l'id du joueur gagnant et affiche le nom de la couleur qui lui correspond comme étant le gagnant. Si aucun des joueurs ne gagne, le paramètre passé en entrée vaut -1) : <br/>
		||  **func multi(id_joueur)** <br/>
---

##### Killers
##### Les killers permettent de libérer les instanciations

- Permet de libérer l'instance de l'écran d'acceuil : <br/>
			|| **func kill_accueil()** <br/>
---			
- Permet de libérer l'instance de maze : <br/>
			|| **func kill_maze()** <br/>
---			
- Permet de libérer l'instance de l'écran de fin de partie : <br/>
			|| **func kill_endOfGame()** <br/>
---



Gère des instances de :
[EndOfGame](IHM/EndOfGame.md), [MainMenu](IHM/MainMenu.md) et [Maze](Maze/Maze.md)
