# Vindor 3D — RPG (combat et immersion)

Module **complémentaire** de [Vindor 3D](https://github.com/isa16480-dotcom/vindor-3d) pour Foundry VTT (v12, v13) et The Forge.
Il ne remplace rien : il se branche sur l'API d'extension de la vue 3D (version 0.8 ou plus) et sur les mécanismes natifs
de Foundry (pause, combats, jetons, fiches, droits). On peut l'activer ou le désactiver sans toucher à Vindor 3D.

## Installation
1. Installer et activer **Vindor 3D** (0.8.0 ou plus).
2. Sur The Forge : *Bazaar* → *Install From Manifest* → coller :
   `https://github.com/isa16480-dotcom/vindor-3d-rpg/releases/latest/download/module.json`
3. Dans le monde : *Gérer les modules* → activer **Vindor 3D — RPG**. *libWrapper* est conseillé (déjà présent sur ton monde).

## Commandes (dans la vue 3D)
| Touche | Qui | Effet |
|---|---|---|
| **B** | MJ | Mode fantôme : caméra libre invisible pour les joueurs, traverse murs et bâtiments. ZQSD : avancer dans la direction du regard · clic + glisser : regarder · **Espace** : monter · **Ctrl** : descendre · **Maj** : 3 × plus vite · molette : vitesse · **B** : retour au personnage (qui n'a pas bougé). Depuis la carte 2D, B ouvre la 3D directement en mode fantôme. |
| **C** | tous | Caméra tactique : vue aérienne, le personnage reste immobile. ZQSD : déplacer la vue · molette : zoom · clic + glisser : tourner. Distances (nom + distance de chaque personnage, distance du repère) dans les unités de la scène. Joueurs : pas de traversée des murs ni des portes fermées, rayon maximal réglable (60 m). MJ : sans limite. **C** : retour. |
| **T** | tous | Ciblage : **clic** sur un personnage = cible principale · **Maj + clic** = ajouter / retirer une cible (plusieurs cibles) · clic sur sa seule cible = la retirer · **clic droit** = tout retirer · **T** ou **Échap** = terminer. Ce sont les cibles natives de Foundry : la carte 2D, le MJ et les autres joueurs les voient aussitôt (et un ciblage fait en 2D apparaît en 3D). |
| **M** | tous | Bascule vue 3D ⇄ carte de combat. La caméra 3D est retrouvée telle quelle au retour. Inactive pendant qu'on écrit (chat, champs, fiches). |
| **Espace** | MJ | Pause générale (pause native de Foundry, partagée par tous) : les joueurs ne peuvent plus bouger. |
| Espace | joueurs | Rien : **le saut est supprimé**. |
| Clic droit | joueurs | Sur son propre personnage 3D : ouvre sa fiche. Sur un autre : seulement si Foundry le permet (propriétaire ou observateur), sinon « accès refusé ». |
| Double clic droit | MJ | Sur n'importe quel personnage, monstre ou PNJ en 3D : ouvre sa fiche (une seule fois). |

Sur la **carte 2D** : double clic droit sur un jeton = fiche (MJ et joueurs, selon leurs droits). En option, un clic droit simple
ouvre la fiche pour les joueurs (cela remplace le menu du jeton, désactivé par défaut).

Les touches B, C, M se changent dans *Configurer les contrôles* → *Vindor 3D — RPG*. Hors de la 3D, C garde son rôle natif
(ouvrir sa fiche) et T son rôle natif (cibler).

## Cibles
- Sous chaque cible : un cercle animé à la couleur du joueur qui cible (plusieurs joueurs sur la même cible = cercles
  emboîtés). Ses propres cibles ont un chevron au-dessus de la tête ; la cible principale est plus grande et pulse.
- Étiquette de ses cibles : nom, distance depuis son personnage (unités de la scène), et **points de vie + CA seulement si
  Foundry le permet** (MJ, propriétaire ou observateur).
- En mode ciblage ou pendant un combat : ligne pointillée de son personnage vers sa cible principale.

## Combats
- Au début d'un combat Foundry : pause automatique, annonce « Le combat commence » en 3D pour chacun et message dans le chat,
  bordure rouge discrète pendant tout le combat. L'ordre d'initiative n'est pas touché.
- **Posture** : pendant le combat, à l'arrêt, chaque personnage se tourne vers la cible principale de son joueur
  (les PNJ vers la cible du MJ). L'animation de garde (« combat idle ») arrive à l'étape 3.
- Les vieux combats vides ou oubliés (sans combattant, ou sans scène et inactifs) sont ignorés.
- À la fin : le mode combat s'arrête. **La pause n'est jamais levée automatiquement** : le MJ relance avec Espace.

## Apparition et disparition des personnages
- Un jeton supprimé (ou caché par le MJ) disparaît aussitôt dans Foundry, pour tout le monde. En 3D, chaque joueur voit le
  modèle **se désintégrer** (le bruit ronge le modèle avec un liseré lumineux, transparence, cendres qui montent), puis les
  ressources sont libérées. L'animation ne retarde jamais la suppression.
- Un nouveau jeton (ou rendu visible) se matérialise progressivement ; un changement d'apparence fait un fondu.

## Réglages
MJ (*Paramètres du module*) : mode fantôme (oui/non, vitesse), rayon de la caméra tactique, durée des transitions,
pause automatique au combat, annonce du combat, désintégration (oui/non, durée), apparition, fiches au clic droit en 2D.
Joueurs : distances en caméra tactique, regarder vers le ciel.

## Feuille de route (étapes suivantes)
Ce module est construit par étapes. Déjà fait : **étape 1** (caméras, pause, combats, fiches, apparition / disparition)
et **étape 2** (ciblage T, posture de combat). À venir :
- **Étape 3** — animations de combat (garde, attaque, parade, esquive, dégâts, mort, victoire, sorts, gestes) reciblées dans Unreal Engine ; tête qui suit la caméra.
- **Étape 4** — armes 3D tirées de la fiche (épée, dague, lance, arc, arbalète, bâton, livre, bouclier) attachées aux os.
- **Étape 5** — attaques et sorts D&D 5e (activités dnd5e 5.x) : animation + effet visuel + son, résolution par le système de règles ; projectiles (flèches, boule de feu).
- **Étape 6** — ciblage de zone (portée, rayon, forme, ligne de vue, depuis les données dnd5e), bibliothèque VFX/SFX, correspondances capacité → animation.

## Pour les développeurs : API d'extension de Vindor 3D (0.8)
`Hooks.on("vindor3d.viewer", (viewer, adapter) => { ... })` puis :
`viewer.on("ready" | "frame" | "keydown" | "keyup" | "pointerdown" | "contextmenu" | "wheel" | "figureAdded" | "figureRemoving" | "close", fn)`
(un écouteur qui renvoie `true` consomme l'événement), `viewer.pick(x, y)`, `viewer.cameraOverride`, `viewer.movementLocked`,
`viewer.viewFocus`, `viewer.allowJump`, `viewer.pitchMin/Max`, `adapter.tokenDoc(id)`, `adapter.metersToUnits(m)`.
