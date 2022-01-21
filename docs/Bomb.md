# Bomb.gd

> Ce script permet de gérer les bombes : leur apparence, leur temps d'explosion et les sprites de l'explosion.

**Extends:** [RigidBody2D]


## Variables

#### Gestion de la relation joueur-bombes

 - Collision pour savoir si le joueur est sorti de la bombe lorsqu'il la pose : <br/>
		||  **onready var cShape**<br/>
---		
 - Référence au GameManager, pour le prévenir quand le joueur perd (en cas de collision joueur-explosion): <br/>
		||  **onready var gameManager**<br/>
---

#### Importation des scènes affichant les sprites de l'explosion

 - Animation du centre de l'explosion : <br/>
		||  **var ExC** <br/>
---		
 - Animation des bras centre de l'explosion : <br/>
		||  **var ExM** <br/>
---
 -  Animation du centre de l'explosion : <br/>
		||  **var ExMC** <br/>
---
 - Animation de la fin des bras de l'explosion : <br/>
		||  **var ExF** <br/>
---

#### Données sur les capacités et l'état de la bombe

 - Indique si la bombe a déjà explosé : <br/>
		||  **onready var exploded** <br/>
---
 -  Portée de la bombe, initialisée à 3 : <br/>
		||  **var bomb_range** <br/>
---
 - Tableau des objets présents dans la zone d'explosion : <br/>
		||  **var in_bomb_range** <br/>
---


## Fonctions

#### Scènes

- Fonction appelée quand le node entre pour la première fois sur la scène, permet à la bombe une absence de rotation : <br/>
			|| **func ready()** <br/>
---
#### Mise à jour des variables

- Fonction appelée lorsque la bombe a été posée, sert à initialiser des variables nécessaires par la suite: <br/>
			|| **func posed()** <br/>
---

#### Animation de l'explosion

- Fonction servant à faire apparaître des textures d'explosion au moment de l'explosion de la bombe, en fonction de la portée de la bombe. Il faut aussi gérer le fait que les textures ne sont pas les mêmes au centre de l'explosion que sur les cotés ou au bout de la portée de l'explosion : <br/>
			|| **func explodeTextures()** <br/>
---
- Fonction d'explosion de la bombe, lancée au terme du timer qui lui est associé, joue le son d'explosion, crée les textures d'explosion et détruit ce qui est à portée d'explosion. Pour cela, on regarde ce qu'il y dans le tableau des objets présents dans la zone d'explosion et on appelle la fonction "bombed" de chacun de ces objets si ils ont une telle méthode (= si ils peuvent être détruits) : <br/>
			|| **func MACRONEXPLOSION()** <br/>
---			

#### Gestion des collisions (effets de l'explosion)

- Change les tailles de CollisionShape2D associées à la détection d'objets étant dans la zone d'explosion de la bombe, en fonction de sa portée r : rayon d'explosion en cases : <br/>
			|| **func resizeShape(r)** <br/>
---
- Permet de ne pas pouvoir collisionner avec la bombe si elle vient d'être posée. On attend alors que le joueur ne soit plus sur la bombe pour la rendre collisionnable à nouveau : <br/>
			|| **func on_Area2D_body_exited(body)** <br/>
---
- Lorsqu'un objet entre dans la zone d'explosion de la bombe, on l'ajoute à un tableau : <br/>
			|| **func on_AreaExplo_body_entered(body)** <br/>
---
- Lorsqu'un objet sort de la zone d'explosion de la bombe on le retire du tableau : <br/>
			|| **func on_AreaExplo_body_exited(body)** <br/>
---








