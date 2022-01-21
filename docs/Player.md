# Player.gd

> Ce script permet de gérer les actions du joueur (son comportement et ses réactions à son environnement).

**Extends:** [KinematicBody2D]

## Variables

#### Relatives à Maze
**Ces variables vont récupérer les données du parent de player : Maze** <br/>

 -  Récupération de la Maze dès que la scène Player est appelée  : <br/>
		||  **onready var Maze** <br/>
---
 - Récupération de la position de la sortie du labyrinthe (mode Solo) depuis Maze : <br/>
		||  **var exitPos** <br/>
---		
 -  TileMap du labyrinthe : <br/>
		||  **var maze**<br/>
---		
 - Pour stocker la taille de l'écran : <br/>
		||  **var screen_size**<br/>
---
				
#### Relatives au score

 - Score du joueur (Mode Solo) : <br/>
		||  **var score**<br/>
---
#### Relatives au joueur

 - Vitesse du joueur, initialisé à 250 : <br/>
		||  **var speed**<br/>
---		
 - Dernière position du joueur (il est nécessaire de la connaître pour le bon fonctionnement des annimations), initialisé à 0 (ce qui correspond à la front view du personnage) : <br/>
		||  **var lastDirection**<br/>
---
 - Nombre de vies du joueur en mode solo, initialisée à 3 : <br/>
		||  **var heart**<br/>
---
 - Identifiant (entier) du joueur instancié (utilisé en mode Multi) : <br/>
		||  **var id**<br/>
---

#### Chargement et nom des animations des mouvements des joueurs

 - Animations marcher vers le bas : <br/>
		||  **var animDown<br/>
---
 - Animation immobile vers le bas : <br/>
		||  **var animIdleFront**<br/>
---
 - Animation marcher vers le haut : <br/>
		||  **var animUp<br/>
---
 - Animation immobile vers le haut : <br/>
		||  **var animIdleBack<br/>
---
 - Animation marcher vers la gauche : <br/>
		||  **var animLeft<br/>
---
 - Animation immobile vers la gauche : <br/>
		||  **var animIdleLeft**<br/>
---
 - Animation marcher vers la droite : <br/>
		||  **var animRight<br/>
---
 - Animation immobile vers la droite : <br/>
		||  **var animIdleRight**<br/>
---

#### Relatives aux bombes

 -  Déclaration de la scène "Bombe" en la chargeant depuis un path : <br/>
		||  **var Bombe** <br/>
---		
 - Portée de l'explosion des instances de "Bombe", initialisée à 2 : <br/>
		||  **var bombRange**<br/>
---
 -  Tableau des bombes que le joueur possède: <br/>
		||  **var bombList** <br/>
---		
 - Nombre d'instances de "Bombe" que le joueur peut poser, initialisée à 2 : <br/>
		||  **var bombCapacity**<br/>
---

#### Relatives aux bonus

 -  Booléen donnant la situation du bonus GodMode : s'il est à *false* le joueur n'a pas le bonus et s'il est à *true* le joueur a le bonus. Initialisée à *false* : <br/>
		||  **var invincible** <br/>
---		
 -  Booléen donnant la situation du bonus Lumière : s'il est à *false* le joueur n'a pas le bonus et s'il est à *true* le joueur a le bonus. Initialisée à *false* : <br/>
		||  **var lumi** <br/>
---
 -  Booléen donnant la situation du bonus Nombre : s'il est à *false* le joueur n'a pas le bonus et s'il est à *true* le joueur a le bonus. Initialisée à *false* : <br/>
		||  **var nb** <br/>
---
 -  Booléen donnant la situation du bonus Pousser : s'il est à *false* le joueur n'a pas le bonus et s'il est à *true* le joueur a le bonus. Initialisée à *false* : <br/>
		||  **var pousse** <br/>
---
 -  Booléen donnant la situation du bonus Range : s'il est à *false* le joueur n'a pas le bonus et s'il est à *true* le joueur a le bonus. Initialisée à *false* : <br/>
		||  **var rang** <br/>
---
 -  Booléen donnant la situation du bonus Vitesse : s'il est à *false* le joueur n'a pas le bonus et s'il est à *true* le joueur a le bonus. Initialisée à *false* : <br/>
		||  **var vite** <br/>
---

#### Relatives à la lumière

 -  Booléen indiquant si la lumière est allumée (= le bonus lumière est actif). Initialisée à *true* : <br/>
		||  **var light** <br/>
---		
		
#### Mode de jeu

 -  Indique si la partie est en solo ou en multi, initialisée à *true* : <br/>
		||  **var isSingleplayer** <br/>
---

#### Commandes des joueurs
 - Tableau des touches pour chaque joueur en fonction de son ID : <br/>
		||  **var keyMapping**<br/>
---


## Fonctions 

#### Scène

- Fonction appelée quand le node entre pour la première fois sur la scène. On détermine si nous sommes en solo ou en multijoueur et le cas échéant on rajoute la restriction de lumière ou non :<br/>
		  || **func ready()** <br/>
---
- Fonction appelée à chaque frame du jeu. Sert à gérer les déplacements, l'arrivée à la sortie, les animations et la capacité de bombes :<br/>
		  || **func process(delta)** <br/>
---

#### Getters
- Fonction permettant de récupérer le nombre de vie restant au joueur (utilisée par HUD) :<br/>
		  || **func getHeart()** <br/>
---		  
- Fonction permettant de savoir si le joueur a le bonus GodMode (utilisée par HUD) :<br/>
		  || **func getInvincible()** <br/>
---		  
- Fonction permettant de savoir si le joueur a le bonus Lumière (utilisée par HUD) :<br/>
		  || **func getLumiere()** <br/>
---		  
- Fonction permettant de savoir si le joueur a le bonus Nombre de Bombes (utilisée par HUD) :<br/>
		  || **func getNb()** <br/>
---		  
- Fonction permettant de savoir si le joueur a le bonus Pousser (utilisée par HUD) :<br/>
		  || **func getPousse()** <br/>
---
- Fonction permettant de savoir si le joueur a le bonus Portée (utilisée par HUD) :<br/>
		  || **func getRange()** <br/>
---
- Fonction permettant de savoir si le joueur a le bonus Vitesse (utilisée par HUD) :<br/>
		  || **func getVite()** <br/>
---
#### Relatives aux Bonus 

- Fonction appelée lorsque le joueur obtient le bonus GodMode. Elle permet d'aumenter le score en conséquence (+30 points pour l'obtention d'un bonus) puis de rendre le joueur invincible pendant 5 secondes :<br/>
		  || **func godmode()** <br/>
---
- Fonction appelée lorsque le joueur obtient le bonus Lumière. Elle permet d'aumenter le score en conséquence (+30 points pour l'obtention d'un bonus) puis de rendre la maze visible pendant 2 secondes :<br/>
		  || **func lumiere()** <br/>
---
- Fonction appelée lorsque le joueur obtient le bonus Nombre de Bombes. Elle permet d'aumenter le score en conséquence (+30 points pour l'obtention d'un bonus) puis d'augmenter le nombre de bombes que peut poser le joueur en même temps :<br/>
		  || **func augmenteBombCapacity()** <br/>
---
- Fonction appelée lorsque le joueur obtient le bonus Pousser. Elle permet d'aumenter le score en conséquence (+30 points pour l'obtention d'un bonus) puis de rendre les bombes posées par le joueur "poussables" :<br/>
		  || **func pousseBombe()** <br/>
---
- Fonction appelée lorsque le joueur obtient le bonus Portée. Elle permet d'aumenter le score en conséquence (+30 points pour l'obtention d'un bonus) puis d'augmenter la portée des bombes posées par le joueur :<br/>
		  || **func augmenteRange()** <br/>
---
- Fonction appelée lorsque le joueur obtient le bonus Vitesse. Elle permet d'aumenter le score en conséquence (+30 points pour l'obtention d'un bonus) puis d'augmenter la vitesse du joueur de 100 :<br/>
		  || **func augmenteSpeed()** <br/>
---

#### Gestion du multijoueur

- Attribue un ID au joueur :<br/>
		  || **func setId()** <br/>
---
- Désactive la restriction de vision en multijoueur :<br/>
		  || **func disabledLight()** <br/>
---
		  
#### Gestion des bombes et explosions

- Permet de poser une bombe. On instancie une bombe, on la place à la position du joueur et si le joueur a le bonus Pousser on met la bombe en mode character :<br/>
		  || **func setup_bomb(bomb_name, pos)** <br/>
---
- Fonction appelée lorsqu'on se fait toucher par une bombe. On vérifie alors si le joueur est invincible, si ce n'est pas le cas, alors soit il perd une vie soit il perd la partie le cas échant :<br/>
		  || **func bombed()** <br/>
---

#### Fin de partie

- En cas de victoire, on prévient GameManager qu'on a gagné :<br/>
		  || **func win()** <br/>
---
- En cas de défaite, on prévient GameManager, on joue le son de défaite et on arrête la musique de jeu :<br/>
		  || **func lose()** <br/>
---






