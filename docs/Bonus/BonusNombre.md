# BonusNombre.gd

> Ce script permet de gérer le bonus Nombre. Le bonus Nombre permet au joueur l'ayant récupéré de poser une bombe de plus à la fois sur la map.

**Extends:** [Area2D]

## Fonctions

#### Collision
- Fonction appelée quand un corps entre dans un bonus de nombre de bombes. Cette fonction vérifie que le corps entré en collision avec ce bonus est un joueur (et non un ennemi) puis augmente le nombre de bombes pouvant être posées par le joueur (par la fonction correspondante) :<br/>
		  || **func on_Bonus_body_entered(player)** <br/>