# Maze.gd

> Ce script permet de gérer la scène maze, construire le labyrinthe et instancier les joueurs, ennemis....

**Extends:** [Node](https://docs.godotengine.org/fr/stable/classes/class_node.html)


## Variables

#### Déclaration des différentes scènes en les chargeant depuis un path

 - Chargement de la scène d'ennemis : <br/>
		||  **var Enemy**<br/>
---	
 - Chargement de la scène de bonus Vitesse : <br/>
		||  **var bonusVitesse**<br/>
---
 - Chargement de la scène de bonus Range : <br/>
		||  **var bonusRange**<br/>
---
 - Chargement de la scène de bonus Pousser : <br/>
		||  **var bonusPousser**<br/>
---
 - Chargement de la scène de bonus Nombre : <br/>
		||  **var bonusNombre**<br/>
---		
 - Chargement de la scène de bonus Lumiere : <br/>
		||  **var bonusLumiere**<br/>
---
 - Chargement de la scène de bonus GodMode : <br/>
		||  **var bonusGodMode**<br/>
---
 - Chargement de la scène de mur cassable : <br/>
		||  **var caillou** <br/>
---
 - Chargement de la scène de mur cassables contenant des bonus : <br/>
		||  **var bonusWall** <br/>
---
 - Chargement de la scène de joueur : <br/>
		||  **var player_model** <br/>
---		

#### Références à d'autres objets/scènes

 - Référence à la [TileMap](https://docs.godotengine.org/en/3.4/classes/class_tilemap.html) du labyrinthe : <br/>
		||  **onready var maze** <br/>
---
 - Générateur de nombre aléatoire : <br/>
		||  **onready var rng** <br/>
---
 - Récupération des données de [GameManager](../../GameManager) : <br/>
		||  **onready var GameManager** <br/>
---		
 -  Difficulté de la maze récupérée dans le [GameManager](../../GameManager) : <br/>
		||  **onready var difficulty** <br/>
---		
 -  Nombre de joueur à instancier sur la maze, récupéré dans le [GameManager](../../GameManager) : <br/>
		||  **onready var nb_player** <br/>
---
#### Déclaration des images de murs cassables en les chargeant depuis un path

 - Chargement de l'image de mur cassable 1 : <br/>
		||  **var wall1** <br/>
---
 - Chargement de l'image de mur cassable 2 : <br/>
		||  **var wall2** <br/>
---		
 - Chargement de l'image de mur cassable 3 : <br/>
		||  **var wall3** <br/>
---		
 - Chargement de l'image de mur cassable 4 : <br/>
		||  **var wall4** <br/>
---

#### Paramètres de génération du maze

 - Longueur extérieure du labyrinthe en cases, initialisée à 15 : <br/>
		||  **var length** <br/>
---
 - Largeur extérieure du labyrinthe en cases, initialisée à 13 : <br/>
		||  **var width** <br/>
---		
 - Multiplicateur de lenteur de génération (> 0, + petit = + rapide), initialisé à 1 : <br/>
		||  **var genSpeed** <br/>
---		
 - Probabilité minimum de faire apparaitre un mur (difficulté faible), initialisé à 0.2 : <br/>
		||  **var probaWallMin** <br/>
---
 - Probabilité maximum de faire apparaitre un mur (difficulté forte), initialisé à 0.95 : <br/>
		||  **var probaWallMax** <br/>
---		
 - Probabilité de base de créer un chemin pour un ennemi, initialisé à 0.6 : <br/>
		||  **var baseProbaEnemyPath** <br/>
---		
 - Probabilité retirée à la précédente chaque tour, initialisé à 0.15 : <br/>
		||  **var minusProbaEachTurn** <br/>
---		
 - Distance minimale requise entre le point de spawn et la sortie, initialisée à 8 : <br/>
		||  **var distanceMinSpawnExit** <br/>
---		
 - Distance minimale requise entre le spawn et un ennemi, initialisée à 5 : <br/>
		||  **var distanceMinSpawnEnemy** <br/>
---
 - Nombre maximal d'ennemis, initialisé à 7 : <br/>
		||  **var nbMaxEnemy** <br/>
---		
 - Probabilité de base d'avoir un mur cassable avec bonus au lieu d'un mur cassable lambda, initialisé à 0.2 : <br/>
		||  **var probaBonus** <br/>
---		
 - [Debug] Ennemis activés: <br/>
		||  **var spawnEnnemies** <br/>
---		
 - [Debug] Murs cassables activés 1 : <br/>
		||  **var spawnWalls** <br/>
---
 - [Debug] Apparition de la sortie : <br/>
		||  **var spawnExit** <br/>
---

#### Identifiants des tiles que l'on souhaite placer

 - Identifiant des blocs de murs incassables (tableau): <br/>
		||  **var obsidian** <br/>
---		
 - Identifiant du sol : <br/>
		||  **var sol** <br/>
---		
 - Identifiant de la sortie : <br/>
		||  **var exit** <br/>
---

#### Variables globales

 - Probabilité d'avoir un mur cassable sur une case : <br/>
		||  **var probaWall** <br/>
---		
 - Position du spawn : <br/>
		||  **var spawnPos** <br/>
---		
 - Position de la sortie : <br/>
		||  **var exitPos** <br/>
---
 - Tableau des positions des spawns des joueurs : <br/>
		||  **var playersSpawnPositions** <br/>
---		
 - Liste des joueurs : <br/>
		||  **var playersList** <br/>
---		
 - Tableau des positions de spawn des ennemis : <br/>
		||  **var enemyPositions** <br/>
---
 - Nombre d'ennemis : <br/>
		||  **var nbEnemy** <br/>
---		
 - Tableau des murs cassables dans le labyrinthe : <br/>
		||  **var walls** <br/>
---		
 - Tableau des textures des différents murs cassables : <br/>
		||  **var textWalls** <br/>
---
 - Joueur : <br/>
		||  **var player** <br/>
---		
 - Si le labyrinthe est chargé ou non, initialisé à false : <br/>
		||  **var loaded** <br/>
---		

## Fonctions

#### Scènes

- Fonction lancée à l'initialisation de la scène de labyrinthe sert à jouer la musique du mode de jeu choisi, désactive les ennemis et la sortie si le mode de jeu est en multi. Puis initialise le labyrinthe : <br/>
			|| **func ready()** <br/>
---
- Fonction lancée à chaque frame du labyrinthe, sert à détecter quand un joueur est mort : <br/>
			|| **func process(delta)** <br/>
---

#### Génération du labyrinthe
- Retourne un tableau contenant les positions des murs cassables du labyrinthe : <br/>
			|| **func getWallsPos()** <br/>
---
- Renvoie la distance de manhattan entre deux points : <br/>
			|| **func manhattan(a : Vector2, b : Vector2)** <br/>
---
- Renvoie la probabilité d'avoir un mur cassable à une position en fonction de la difficulté. Et des paramètres de génération comme la probabilité minimale d'avoir un mur cassable : <br/>
			|| **func getNewProba()** <br/>
---
- Renvoie si un point est dans le labyrinthe ou non : <br/>
			|| **func isInBounds(pos : Vector2)** <br/>
---
- Renvoie le nombre d'ennemis qu'il doit y avoir dans le labyrinthe en fonction de la difficulté, et des paramètres de génération comme nbMaxEnemy. Il y a aussi aléatoirement 1 ennemi en plus ou en moins : <br/>
			|| **func getNbEnemy()** <br/>
---			
- Permet de générer un labyrinthe avec :
	- Des murs incassables selon un pattern donné
	-  Des murs cassables aléatoirement selon la difficulté
	-  Des murs cassables contenants un bonus aléatoirement
	- Un point de spawn dans un des coins du labyrinthe
	- Une sortie
	- Des ennemis selon la difficulté, ayant une position et un type aléatoire
	- Une gestion du multijoueur (pas de HUD, + de bonus, pas d'ennemis ni de sortie,...)
Et suivant certaines règles :
	- Il y a 3 cases vides dans le coin du spawn (pour pouvoir poser une bombe)
	- La sortie est à + de distanceMinSpawnExit cases (manhattan) du spawn
	- Il n'y a pas d'ennemi à - de distanceMinSpawnEnemy case du spawn : <br/>
---			|| **func initMaze(nbPlayer : int)** <br/>
---

- Fonction servant à instancier, initialiser et placer le(s) joueur(s) qui vont jouer et prenant le nombre de joueurs en paramètres: <br/>
			|| **func initPlayers()** <br/>
---
- Instancie, initialise et place les ennemis à partir de la liste des ennemis : <br/>
			|| **func initEnemy()** <br/>
---
- Fonction récursive permettant de créer un chemin aléatoirement dans le labyrinthe case par case pour les ennemis, à chaque nouvel appel la probabilité de rallonger le chemin diminue : <br/>
			|| **func alterPath(pos : Vector2, proba : float)** <br/>
---
- Fonction récursive permettant de créer un chemin aléatoirement dans le labyrinthe case par case pour les ennemis, à chaque nouvel appel la probabilité de rallonger le chemin diminue : <br/>
			|| **func alterPath(pos : Vector2, proba : float)** <br/>
---
- Renvoie toutes les combinaisons possibles entre plusieurs listes d'un tableau de listes : <br/>
			|| **func combinaisons(a)** <br/>
---

Gère des instances de :
[Player](../../Player), [Wall](../../Maze/Wall), [Bonus](../../Bonus/Bonus), [BonusRange](../../Bonus/BonusRange), [BonusNombre](../../Bonus/BonusNombre), [BonusPousser](../../Bonus/BonusPousser), [BonusLumiere](../../Bonus/BonusLumiere), [BonusGodMode](../../Bonus/BonusGodMode), [BonusVitesse](../../Bonus/BonusVitesse), [HUD](../../IHM/HUD)
