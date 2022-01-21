# TileMap.gd

> Ce script permet de gérer le pathfinding des ennemis.

**Extends:** [TileMap]


## Variables

 - Objet Godot permettant de créer et de gérer des chemins grâce un algorithme A* : <br/>
		||  **var astar**<br/>
---		
 - Cases étants utilisables (= cases avec du sol et non des murs incassables) : <br/>
		||  **var used_cells**<br/>
---		
 - Chemin retourné par l'algorithme A* : <br/>
		||  **var path** <br/>
---		
## Fonctions

#### Scènes

- Fonction lancée à l'instanciation, sert à lancer la préparation : <br/>
			|| **func ready()** <br/>
---

#### PathFinding A* 

- Fonction de préparation, sert à initialiser les variables déclarées plus tôt et à ajouter les points empruntables au gestionnaire A* et à les relier entre eux: <br/>
			|| **func setup()** <br/>
---
- Ajoute les points listés dans used_cells u gestionnaire A*: <br/>
			|| **func add_points()** <br/> <br/>			

- Relie les points du gestionnaire A* entre eux pour lui dire qu'il est possible de passer d'une case à une autre si elles sont directement adjacentes, utilise un système d'identifiant unique à chaque case en fonction de ses cooronnées: <br/>
			|| **func connect_points()** <br/>
---
- Renvoie le chemin le plus court empruntant les cases entrées dans le gestionnaire A\* partant de start pour aller à end: <br/>
			|| **func get_path()** <br/>
---
####  Autres fonctions

- Permet de rendre des cases non empruntables depuis un tableau de cases utiles pour tenter d'avoir un chemin qui ne repasse pas par des cases déja empruntées: <br/>
			|| **func removePoints()** <br/>
---
- Renvoie l'identifiant d'un point en fonction de ses coordonnées: <br/>
			|| **func id(point)** <br/>
---

