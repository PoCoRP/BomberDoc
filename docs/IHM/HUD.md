# HUD.gd

> Ce script permet d'afficher le HUD qui comporte les coeurs représentant la vie du joueur ainsi que les bonus acquis par le joueur au cours de la partie.

**Extends:** [Control]

## Variables

 - Joueur présent sur la maze (mode SOLO) : <br/>
		||  **var player**<br/>
---
 - Booléen permettant de savoir si le joueur est bien chargé sur la maze (initialisé à *false*): <br/>
		||  **var loaded**<br/>
---

## Fonctions

#### Scènes
- Fonction appelée quand le node entre pour la première fois sur la scène, elle permet de cacher les bonus présents dans le HUD (i.e. au départ le joueur n'a aucun bonus) : <br/>
			|| **func ready()** <br/>
---
-  Fonction exécutée tout au long de l'existence de la scène. Ici elle permet de mettre à jour le HUD en fonction des actions du joueur : s'il perd une vie un coeur disparaît, s'il récupère un bonus, le bonus en question s'affiche dans le HUD (si le bonus est temporaire, il disparaît du HUD lorsque le temps d'action du bonus est écoulé): <br/>
		|| **func process(delta)**<br/>
**NB :** Si le joueur n'a plus de vie dans le HUD, son instance est libérée de la Maze.
---

#### Getters
- Fonction appelée pour récupérer le joueur (si le joueur est récupéré, loaded passe à *true*):<br/>
		  || **func getPlayer(p)** <br/>
