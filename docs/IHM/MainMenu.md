# MainMenu.gd

> Ce script permet de gérer l'écran d'accueil du jeu.

**Extends:** [Control]

## Fonctions

#### Scènes
- Lorsque le menu d'accueil apparaît les boutons indiquant le nombre de joueurs n'apparaîssent pas : <br/>
			|| **func ready()** <br/>
---
#### Mode SOLO
- Lorsque le joueur appui sur le bouton "SOLO GAME", on lance le maze et on libère le menu d'accueil. On en profite aussi pour jouer le son de validation du bouton, et la musique de jeu solo : <br/>
		  || **func on_Solo_pressed()** <br/>
---
#### Mode MULTI
- Lorsque le joueur appui sur le bouton "MULTIJOUEUR", on affiche les boutons indiquant le nombre de joueurs : <br/>
		  || **func on_Multi_pressed(id_joueur)** <br/>
---
- Si le joueur appuie maintenant sur le bouton "2", on lance une partie à 2 joueurs. On en profite aussi pour jouer le son de validation du bouton, et la musique de jeu multi : <br/>
		  || **func on_two_pressed(id_joueur)** <br/>
---
- Si le joueur appuie maintenant sur le bouton "3", on lance une partie à 3 joueurs. On en profite aussi pour jouer le son de validation du bouton, et la musique de jeu multi : <br/>
		  || **func on_three_pressed(id_joueur)** <br/>
---
- Si le joueur appuie maintenant sur le bouton "4", on lance une partie à 4 joueurs. On en profite aussi pour jouer le son de validation du bouton, et la musique de jeu multi : <br/>
		  || **func on_four_pressed(id_joueur)** <br/>
---

#### Gestion des sons

- Fonction permettant de déclencher un son lorsque la souris du joueur entre dans le cadre du bouton "SOLO" : <br/>
		  || **func on_Solo_mouse_entered()** <br/>
---		  
- Fonction permettant de déclencher un son lorsque la souris du joueur entre dans le cadre du bouton "MULTI" : <br/>
		  || **func on_Multi_mouse_entered()** <br/>
---		  
- Fonction permettant de déclencher un son lorsque la souris du joueur entre dans le cadre du bouton "2" : <br/>
		  || **func on_two_mouse_entered()** <br/>
---		  
- Fonction permettant de déclencher un son lorsque la souris du joueur entre dans le cadre du bouton "3" : <br/>
		  || **func on_three_mouse_entered()** <br/>
---
- Fonction permettant de déclencher un son lorsque la souris du joueur entre dans le cadre du bouton "4" : <br/>
		  || **func on_four_mouse_entered()** <br/>
---
