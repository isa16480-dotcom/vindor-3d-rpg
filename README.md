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
| **G** | tous | Menu des gestes : saluer, montrer du doigt, lever la main, mains en l'air, pouce levé, non, bras croisés, parler, appeler, victoire, intimider, dégainer, rengainer, lever le bouclier, boire, interagir, ramasser, s'accroupir, torche, danser, s'asseoir. Les joueurs animent leur personnage ; le MJ anime sa cible, sinon le jeton sélectionné. Tout le monde voit le geste. Les postures (bras croisés, parler, danser...) durent jusqu'à ce que le personnage bouge ou qu'on rappuie. |
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
  (les PNJ vers la cible du MJ).

## Animations (modèles 3D Vindor animés, ex. « Garde chevalier »)
- **Garde de combat** selon l'équipement de la fiche : épée (garde basse), bouclier levé, arbalète, lanceur de sorts.
  En marchant pendant un combat, les jambes marchent et le haut du corps garde l'arme en garde.
- **Attaques automatiques**, déclenchées par les jets dnd5e (pour tout le monde) : épée (trois coups différents),
  arme lourde, lance (coup d'estoc), arc, arbalète, arme lancée, mains nues, sorts (préparation puis tir). Le personnage
  se tourne vers sa cible pendant l'attaque.
- **Début de son tour** : le personnage arme son coup (ou prépare un sort).
- **Points de vie** : coup reçu (tête ou poitrine), gros coup = projeté au sol puis se relève ; à 0 PV il s'effondre
  et reste au sol ; soigné, il se relève.
- **Fin du combat** gagné (tous les ennemis vaincus) : les personnages alliés fêtent la victoire.
- **Tête et cou** : la tête de son personnage suit la caméra (dans les limites du cou) ; les autres joueurs voient où
  l'on regarde. Les autres personnages regardent leur cible.
- Bibliothèque : 67 animations (Quaternius UAL 1 et 2, CC0, reciblées dans Unreal Engine 5.8 ; gestes Vindor créés
  sur le même squelette). Un modèle sans ces animations garde son comportement habituel.
- **Autres systèmes que dnd5e** (0.4.3, ex. Chroniques Oubliées) : un jet dont le titre nomme une arme ou une capacité
  d'attaque du personnage (ou une arme de rencontre), ou un jet « Attaque au contact / à distance / magique », déclenche
  l'attaque. Les jets de dégâts, de soins et de compétences n'animent rien.
- **Geste « Attaquer »** (0.4.3, menu G) : joue le coup d'arme à la demande, tourné vers la cible de l'utilisateur.
- **Figurines à attaque seule** (0.4.3) : un modèle qui n'a que « Idle » et « Sword_Attack » (ex. figurine Tripo
  riggée pour ses coups) reste immobile, se déplace comme une pièce (mode pion) et joue son coup à chaque attaque
  (arme lourde, lance, mains nues ou arme lancée comprises).
- Les vieux combats vides ou oubliés (sans combattant, ou sans scène et inactifs) sont ignorés.
- À la fin : le mode combat s'arrête. **La pause n'est jamais levée automatiquement** : le MJ relance avec Espace.

## Mini-carte 2D du MJ (0.4)
Dans la vue 3D, le MJ a un bouton **Mini-carte** en haut à droite : une petite fenêtre montre la carte de la scène et
tous ses jetons (les joueurs ne la voient pas).
- **Clic** sur un jeton : il est sélectionné (aussi sur la carte de Foundry) ; **Maj + clic** : ajouter / retirer.
- **Clic gauche glissé sur le fond** : rectangle de sélection (plusieurs jetons d'un coup ; Maj : ajouter).
- **Glisser un jeton** : il change de case avec toute la sélection (calé sur la grille) ; en 3D, les personnages marchent.
- **Clic droit sur un jeton** : menu comme le HUD de la carte 2D, pour toute la sélection — fiche, visible / invisible,
  ajouter / retirer du combat, cibler, états (à terre, mort, inconscient, étourdi, empoigné, invisible…), supprimer.
- En-tête : nombre de jetons sélectionnés et boutons **combat**, **visible / invisible**, **supprimer** pour la sélection.
- **Suppr** : supprime la sélection (rien n'est sélectionné à l'ouverture) ; **Échap** : ferme le menu, puis désélectionne.
- **Molette** : zoom ; **clic droit glissé** (ou clic molette) : déplacer la vue ; bouton **⤢** : recentrer ;
  **double clic** : fiche du personnage. Sur la mini-carte : point orange = en combat, anneau rouge = ciblé.
- **Orientation** (0.4.4) : chaque jeton a une petite pointe qui montre où il regarde. Autour des jetons sélectionnés,
  un **anneau orange** avec une poignée : glisser la poignée fait tourner le jeton vers la souris (par pas de 5°,
  **Maj** : par 45°), toute la sélection tourne du même angle, et en 3D les personnages se tournent en direct.
  **Clic droit** avec deux jetons sélectionnés : **Face à face** (chacun se tourne vers l'autre).
- La fenêtre se redimensionne par son coin inférieur droit.
- **Nouveau jeton** (0.4.1) : ouvrez l'onglet **Acteurs** (ou un **compendium**) dans la barre latérale de droite — elle
  reste utilisable en vue 3D : cliquez une icône pour ouvrir un panneau, recliquez pour le fermer — puis glissez l'acteur
  sur la mini-carte : le jeton est créé à cet endroit (Alt : caché ; Maj : sans calage sur la grille). La mini-carte se
  place toute seule à gauche du panneau ouvert.

## Marche et course des personnages animés (0.4, avec Vindor 3D 0.9.1)
- Les personnages animés **marchent** à leur vraie allure (environ 1,2 m/s, jambes à la bonne cadence) au lieu de trottiner.
- **Course** : touche **Maj** pour son propre personnage ; pour les jetons, choisir l'action de déplacement
  **Courir** dans le sélecteur d'action du jeton (Foundry v13). Un personnage qui a plus de 15 m de retard sur son jeton court.
- En marchant, les PNJ regardent devant eux (à l'arrêt, ils regardent leur cible).

## Mode pion : les statues se déplacent comme des pièces d'échecs (0.4)
Pour les jetons dont le modèle 3D est une **statue** (figurine imprimée, modèle Tripo, Meshy, Sketchfab... sans animations) :
quand le jeton bouge (glissé sur la carte 2D, déplacé au clavier, bougé par le MJ), on voit la figurine comme sur une vraie table :
1. elle se **soulève** (comme prise entre deux doigts), avec un petit « tic » ;
2. elle **glisse** au-dessus du sol vers sa nouvelle case, penchée dans le sens du mouvement, avec un léger balancement ;
3. elle se **repose** avec un petit choc, un « toc » et un nuage de poussière autour du socle.

- Fonctionne pour tout le monde (chaque joueur voit l'animation chez lui), y compris pour son propre personnage.
- Les modèles **animés qui marchent** (garde chevalier, troupe Vindor) ne sont pas concernés : ils marchent normalement.
  Une figurine qui n'anime que ses attaques se déplace comme une pièce (0.4.3).
- Correctif 0.4.3 : le bouton Mini-carte se replace bien à gauche de la barre latérale quand on rouvre la vue 3D.
- Option : appliquer aussi le mode pion aux **figurines par défaut** (jetons sans modèle 3D).
- Un très long déplacement (plus de 60 m, téléportation) reste instantané.
- Nécessite Vindor 3D 0.9.1 ou plus (avec 0.9.0, la figurine se soulève mais commence à glisser tout de suite).

## Apparition et disparition des personnages
- Un jeton supprimé (ou caché par le MJ) disparaît aussitôt dans Foundry, pour tout le monde. En 3D, chaque joueur voit le
  modèle **se désintégrer** (le bruit ronge le modèle avec un liseré lumineux, transparence, cendres qui montent), puis les
  ressources sont libérées. L'animation ne retarde jamais la suppression.
- Un nouveau jeton (ou rendu visible) se matérialise progressivement ; un changement d'apparence fait un fondu.

## Réglages
MJ (*Paramètres du module*) : mode fantôme (oui/non, vitesse), rayon de la caméra tactique, durée des transitions,
pause automatique au combat, annonce du combat, désintégration (oui/non, durée), apparition, fiches au clic droit en 2D,
animations de combat et gestes, mode pion (statues / statues + figurines par défaut / désactivé) et hauteur du soulèvement.
Joueurs : distances en caméra tactique, regarder vers le ciel, tête qui suit la caméra, volume du « toc » des pions.

## Feuille de route (étapes suivantes)
Ce module est construit par étapes. Déjà fait : **étape 1** (caméras, pause, combats, fiches, apparition / disparition),
**étape 2** (ciblage T, posture de combat) et **étape 3** (animations de combat, gestes G, tête qui suit la caméra). À venir :
- **Étape 4** — armes 3D tirées de la fiche (épée, dague, lance, arc, arbalète, bâton, livre, bouclier) attachées aux os.
- **Étape 5** — attaques et sorts D&D 5e (activités dnd5e 5.x) : animation + effet visuel + son, résolution par le système de règles ; projectiles (flèches, boule de feu).
- **Étape 6** — ciblage de zone (portée, rayon, forme, ligne de vue, depuis les données dnd5e), bibliothèque VFX/SFX, correspondances capacité → animation.

## Pour les développeurs : API d'extension de Vindor 3D (0.8)
`Hooks.on("vindor3d.viewer", (viewer, adapter) => { ... })` puis :
`viewer.on("ready" | "frame" | "keydown" | "keyup" | "pointerdown" | "contextmenu" | "wheel" | "figureAdded" | "figureRemoving" | "avatarAdded" | "close", fn)`
(0.9 : `fig.driver = (dt, speed) => true` pilote les animations d'une figure ; `fig.animations`, `fig.model` ;
0.9.1 : `o.hold = true` retient une figure sur place, `o.paceFixed` impose sa vitesse de déplacement, pour `o` dans `viewer.others`),
et pour ce module : `game.modules.get("vindor-3d-rpg").api.anim.playSet(tokenId, "melee" | "bow" | "cast" | ..., cibleId)`,
`.gesture("wave", tokenId)`
(un écouteur qui renvoie `true` consomme l'événement), `viewer.pick(x, y)`, `viewer.cameraOverride`, `viewer.movementLocked`,
`viewer.viewFocus`, `viewer.allowJump`, `viewer.pitchMin/Max`, `adapter.tokenDoc(id)`, `adapter.metersToUnits(m)`.
