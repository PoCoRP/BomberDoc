# BonusGodMode.gd

> Ce script permet de gérer le bonus GodMode. Le bonus GodMode rend le joueur l'ayant récupéré invincible pendant quelques secondes.

**Extends:** [Area2D]

## Fonctions

#### Collision
- Fonction appelée quand un corps entre dans un bonus d'invincibilité. Cette fonction vérifie que le corps entré en collision avec ce bonus est un joueur (et non un ennemi) puis rend le joueur invincible par la fonction correspondante :<br/>
		  || **func on_Bonus_body_entered(player)** <br/>
