# BonusLumiere.gd

> Ce script permet de gérer le bonus Lumiere. Le bonus Lumiere permet au joueur l'ayant récupéré de voir la maze en entier (seulement en mode Solo).

**Extends:** [Area2D]

## Fonctions

#### Collision
- Fonction appelée quand un corps entre dans un bonus de lumière. Cette fonction vérifie que le corps entré en collision avec ce bonus est un joueur (et non un ennemi) puis rend le labyrinthe visible pendant quelques secondes (par la fonction correspondante) :<br/>
		  || **func on_Bonus_body_entered(player)** <br/>