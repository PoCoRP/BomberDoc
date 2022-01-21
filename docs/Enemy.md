# Enemy.gd

> Ce script permet de gérer les mouvements et les interactions des ennemis.

**Extends:** [KinematicBody2D]

## Variables

#### Déplacement de l'ennemi

 - Vitesse de l'ennemi, initialisée à 100 : <br/>
		||  **var speed**<br/>
---
 - Tableau de vector2 qui permet de stocker le chemin que doit suivre l'ennemi : <br/>
		||  **var path**<br/>
---
 - Position actuelle dans le path, initialisée à 0 : <br/>
		||  **var indice**<br/>
---		
 - Variable permettant de savoir dans quel sens se déplace l'ennemi, initialisée à 1 : <br/>
		||  **var direction**<br/>
---		
 - Variable permettant de stocker la TileMap du maze pour savoir comment se déplacer : <br/>
		||  **var maze**<br/>
---

#### Interactions avec le joueur

 - Variable permettant de stocker l'objet qui vient d'entrer en collision avec l'ennemi : <br/>
		||  **var pre**<br/>
---
 - Variable permettant de savoir si l'ennemi suit un joueur, initialisée à false : <br/>
		||  **var isChasing**<br/>
---		
 - Variable stockant le joueur qui est suivi : <br/>
		||  **var chasingPlayer**<br/>
---

#### Types d'ennemis

 - Variable permettant de gérer le type de l'ennemi (passif, actif ou aggressif) : <br/>
		||  **var type**<br/>
---		
 - Variable stockant un nombre généré aléatoirement : <br/>
		||  **onready var rng**<br/>
---		

## Fonctions

#### Scène

- Fonction lancée à l'instanciation de l'ennemi. Sert à seeder le générateur de nombres aléatoires et à donner un nouveau chemin aléatoire à l'ennemi. On en profite pour créer un timer qui donnera un nouveau chemin toutes les 15 secondes à l'ennemi si il est actif : <br/>
			|| **func ready()** <br/>
---
- Fonction lancée à chaque frame permettant de déplacer l'ennemi en fonction du chemin généré. Permet aussi de gérer les collisions lors des déplacements: <br/>
			|| **func process(delta)** <br/>
---
#### Misc
- Remplace les valeurs étant NaN d'un vecteur par des 0 : <br/>
			|| **func deNan(n)** <br/>
---			
#### Type

- Assigne aléatoirement un type d'ennemi à l'ennemi en cours parmi passif, actif et aggressif et lui donne une texture et une animation en conséquence : <br/>
			|| **func getType()** <br/>
---
#### Déplacements

- Renvoie un tableau de coordonnées constituant un chemin bouclant sur lui-même et commençant à la position actuelle de l'ennemi. La longueur dépend d'un paramètre aléatoire. On commence par faire la moitié du chemin en prenant aléatoirement une nouvelle case adjacente à chaque fois. Puis le retour se fait grâce à un algorithme A*, l'ennemi fera donc demi tour pour revenir à son point de départ, en essayant le plus possible d'éviter les cases par lesquelles il est déja passé afin d'éviter qu'il revienne simplement sur ses pas. : <br/>
			|| **func getNewPassivePath()** <br/>
---
#### Gestion de la mort des ennemis par les bombes

- Méthode qui est appellée par Bomb.gd si l'ennemi est touché par l'explosion d'une bombe. Il est alors détruit. : <br/>
			|| **func bombed()** <br/>
---
#### Ennemis Aggressifs

- Renvoie un tableau de positions établissant un chemin entre la case courante de l'ennemi et la position du joueur passée en paramètre : <br/>
			|| **func getPathToPlayer()** <br/>
---
- Si quelque chose entre dans le rayon de vision de l'ennemi. Sert à faire que les ennemis aggressifs chassent les joueurs si ils sont assez près : <br/>
			|| **func on_Area2D2_body_entered(body)** <br/>
---
- Si un objet quitte le rayon de vision de l'ennemi. Sert à rendre son comportement normal à un ennemi :<br/>
			|| **func on_Area2D2_body_exited(body)** <br/>
---
