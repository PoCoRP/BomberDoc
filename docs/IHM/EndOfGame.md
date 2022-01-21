# endOfGame.gd

> Ce script permet de gérer les écrans de fin de partie, en solo ainsi qu'en multijoueur.

**Extends:** [Node]

## Variables

#### Mode Solo

 - Score du joueur mis à jour au fur et à mesure de la partie, initialisée à 0 : <br/>
		||  **var score**<br/>
---
- Tableau des textes de victoire en solo : <br/>
		||  **var victoryTexts**<br/>
---
- Tableau des textes de défaite en solo : <br/>
		||  **var lostTexts** <br/>
---
#### Mode Multi

- Stockage des noms des couleurs des joueurs : <br/>
		||  **var colors**<br/>
---
- Tableau des textes de fin de partie (victoire) en multijoueur : <br/>
		||  **var multiEndTexts** <br/>
---
- Tableau des textes de fin de partie en multijoueur en cas d'égalité : <br/>
		||  **var multiDrawEndTexts** <br/>
---
- Random Number Generator : <br/>
		||  **onready var rng** <br/>
---

## Fonctions

#### Scènes
- Fonction appelée quand le node entre pour la première fois sur la scène, cache l'écran de fin de partie et génère un nombre aléatoire : <br/>
			|| **func ready()** <br/>
---
-  Fonction exécutée tout au long de l'existence de la scène. Ici elle permet de lancer une nouvelle partie dès l'appui sur la touche espace par le joueur : <br/>
		|| **func process(delta)**<br/>
---
#### Setters
- Fonction permettant de redéfinir le score à partir d'une autre classe que endOfGame :<br/>
		  || **func set_score(player_score)** <br/>
---

#### Mode SOLO
- Fonction appelée lors de la victoire du joueur et faisant apparaître l'écran de victoire (message sélectionné aléatoirement dans la liste des messages de victoire solo, score & boutons "Niveau Suivant" & "Menu") : <br/>
		  || **func on_Player_Victory()** <br/>
---
- Fonction appelée lors de la défaite du joueur et faisant apparaître l'écran de défaite (message sélectionné aléatoirement dans la liste des messages de défaite solo, score & boutons "Rejouer" & "Menu") : <br/>
		  || **func on_Player_Death()** <br/>
---

#### Mode MULTI
- Fonction appelée lorsque la partie en multijoueur est terminée et faisant apparaître l'écran de fin de partie multijoueurs (message sélectionné aléatoirement dans la liste des messages de victoire d'égalité multi (en fonction du résultat de la partie) & boutons "Rejouer" & "Menu"): <br/>
		  || **func on_End_Multi(id_joueur)** <br/>


##### Gestion des boutons

- Fonction permettant de lancer la scène de menu lorsque le joueur appui sur le bouton menu (elle permet également de gérer les transitions du son entre les interfaces) : <br/>
		  || **func on_MenuButton_pressed()** <br/>
---		  
- Fonction permettant de lancer la scène de menu lorsque le joueur appui sur le bouton NextLevel (elle permet également de gérer les transitions du son entre les interfaces) : <br/>
		  || **func on_NextLevelButton_pressed()** <br/>
---		  
- Fonction permettant de générer un son lorsque la souris passe sur le bouton Menu : <br/>
		  || **func on_MenuButton_mouse_entered()** <br/>
---		  
- Fonction permettant de générer un son lorsque la souris passe sur le bouton NextLevel : <br/>
		  || **func on_NextLevelButton_mouse_entered()** <br/>
---