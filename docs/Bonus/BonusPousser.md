# BonusPousser.gd

> Ce script permet de gérer le bonus Pousser. Le bonus Pousser rend les bombes du joueur l'ayant récupéré 'poussables', de fait ses adversaires (Multi) ou ses ennemis (Solo) ainsi que  lui-même peuvent pousser ses bombes.

**Extends:** [Area2D]

## Fonctions

#### Collision
- Fonction appelée quand un corps entre dans un bonus pousser. Cette fonction vérifie que le corps entré en collision avec ce bonus est un joueur (et non un ennemi) puis rend les bombes du joueur "poussables" par la fonction correspondante :<br/>
		  || **func on_Bonus_body_entered(player)** <br/>