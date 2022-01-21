# Bonus.gd

> Ce script permet de gérer les Bonus de manière général (indépendant du type de bonus).

**Extends:** [Area2D]

## Fonctions

#### Collision
- Fonction appelée quand un corps (Player) entre dans un bonus, cela lance un son (pour indiquer que le bonus est récupéré) et le bonus disparaît de la Maze :<br/>
		  || **func on_Bonus_body_entered(player)** <br/>
