# BonusWall.gd

> Ce script permet de gérer les murs cassables contenant des bonus (principalement leur apparence et leur destruction).

**Extends:** [KinematicBody2D]

## Variables

#### Chargement des scènes des différents bonus

 - Chargement de la scène du bonus vitesse : <br/>
		||  **var bonusVitesse**<br/>
---		
 - Chargement de la scène du bonus portée : <br/>
		||  **var bonusRange**<br/>
---		
 - Chargement de la scène du bonus pousser  : <br/>
		||  **var bonusPousser**<br/>
---		
 - Chargement de la scène du bonus de nombre de bombes : <br/>
		||  **var bonusNombre**<br/>
---		
 - Chargement de la scène du bonus lumière  : <br/>
		||  **var bonusLumiere**<br/>
---		
 - Chargement de la scène du bonus God Mode  : <br/>
		||  **var bonusGodMode**<br/>
---
#### Mode de jeu

 - Indique si le mode de jeu est en solo  : <br/>
		||  **var solo**<br/>
---
## Fonctions

#### Scènes

- Fonction lancée à l'initialisation du mur cassable avec bonus, servant à donner une texture de départ aléatoire pour que les cycles de tous les murs cassables ne soient pas synchronisés. On en profite pour rendre impossible l'obtention du bonus lumière en multijoueur : <br/>
			|| **func ready()** <br/>
---

#### Destruction du mur

- Fonction appelée lorsque le mur est détruit par une bombe, on fait donc aparaître un objet bonus en fonction de la texture qu'avait le mur au moment d'être détruit : <br/>
			|| **func bombed()** <br/> <br/>