# BonusVitesse.gd

> Ce script permet de gérer le bonus Vitesse. Le bonus Vitesse rend le joueur l'ayant récupéré plus rapide.

**Extends:** [Area2D]

## Fonctions

#### Collision
- Fonction appelée quand un corps entre dans un bonus de vitesse. Cette fonction vérifie que le corps entré en collision avec ce bonus est un joueur (et non un ennemi) puis rend le joueur plus rapide par la fonction correspondante :<br/>
		  || **func on_Bonus_body_entered(player)** <br/>