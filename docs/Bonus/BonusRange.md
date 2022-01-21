# BonusRange.gd

> Ce script permet de gérer le bonus Range. Le bonus Range augmente la portée des bombes posées par le joueur l'ayant récupéré.

**Extends:** [Area2D]

## Fonctions

#### Collision
- Fonction appelée quand un corps entre dans un bonus de portée. Cette fonction vérifie que le corps entré en collision avec ce bonus est un joueur (et non un ennemi) puis augmente la portée des bombes posées par le joueur l'ayant récupéré par la fonction correspondante :<br/>
		  || **func on_Bonus_body_entered(player)** <br/>