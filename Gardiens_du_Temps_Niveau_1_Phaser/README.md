# Les Gardiens du Temps

Branche de travail : `refonte/niveau-1-phaser`.

Le chapitre I est reconstruit avec Phaser 3.90.0. Les chapitres II–V sont conservés dans leur version d’origine. Ne pas confondre cette livraison avec la refonte complète des cinq chapitres : cette étape sert à valider le niveau de référence.

## Jouer

Avec GitHub Desktop, choisir cette branche et effectuer **Fetch origin**, puis **Pull origin** si proposé. Le point d’entrée est `index.html` à la racine; GitHub Pages peut servir directement les fichiers sans compilation, lorsqu’on décide de publier cette branche.

Pour un essai local, lancer depuis le dossier du dépôt :

```sh
python3 -m http.server 8000
```

Ouvrir `http://localhost:8000/`. Les modules JavaScript nécessitent HTTP : un double-clic `file://` sur le HTML ne suffit pas.

Le nouveau chapitre se trouve dans `Gardiens_du_Temps_Campagne_5_niveaux/refonte/`. L’ancien niveau reste disponible dans `niveau_1_classique.html`. Le fichier `niveau_1.html` mène au nouveau chapitre.

## Commandes

- Flèches gauche/droite ou A/D : déplacement.
- Espace ou flèche haut : saut variable selon la durée d’appui.
- J ou X : attaque.
- K ou Maj : esquive courte, avec délai de récupération.
- E : observer ou interagir avec un poste.
- P ou Échap : pause. Perte de focus : pause automatique.
- 1–4 : répondre à la question documentaire. Les boutons sont accessibles au clavier.

## Contenu du chapitre I

1. Partager six parts de débit entre deux champs et les familles en aval, à l’aide de prises réglables.
2. Interpréter un registre reconstitué, sans déduire ce que le document ne dit pas.
3. Fermer la prise, consolider la digue, puis ouvrir l’évacuation en se déplaçant entre les postes.
4. Affronter le Gardien : vague simple, puis doubles vagues et chutes d’eau. Attaquer pendant les fenêtres de vulnérabilité.

Douze éclats optionnels récompensent l’exploration. Quatre éclats rendent une unité d’énergie. Les missions réussies débloquent les passages et les points de reprise. Le bilan mène au marché après huit secondes, avec un bouton pour suspendre le départ.

## Architecture

- `refonte/src/game.js` : scène Phaser, physique, entrées, objets, ennemis et boss.
- `refonte/src/model.js` : règles des missions et validation des sauvegardes, sans dépendance graphique.
- `refonte/src/ui.js` : menus, consignes, document et rétroactions accessibles en HTML.
- `refonte/src/qa.js` : essais d’intégration opt-in dans le vrai moteur.
- `refonte/vendor/` : Phaser livré localement, version figée et licence MIT.
- `refonte/*-sheet.png` : planches de six poses pour le Gardien et le sanglier.
- `refonte/irrigation-atlas.png` : six accessoires illustrés; `ur-sunset.png` : paysage, sol et plateformes référencés par des frames.
- `assets/kael_*.png` : animations du héros conservées du projet initial.

Tous les décors visibles proviennent d’images. La géométrie de collision est invisible. Les effets utilisent des textures; aucun décor n’est tracé par des primitives de dessin. Les nouvelles images sont générées pour ce projet; voir `refonte/ART.md`.

## Sauvegarde

Les réglages partiels des prises d’eau sont conservés, même avant de réussir la mission. La refonte utilise la clé `gardiens.refonte.level1.v1`, distincte de l’ancien niveau. La victoire ajoute seulement `level1` à `gardiens_campagne` en conservant les autres entrées. Pas de compte élève, pas d’envoi de données à un serveur. La sauvegarde dépend du navigateur et de l’appareil; une navigation privée ou un nettoyage peut l’effacer.

## Tests

```sh
npm test
```

Pour les scénarios du moteur, ouvrir `Gardiens_du_Temps_Campagne_5_niveaux/refonte/?qa=1` et cliquer **Exécuter les essais du moteur**. Ne pas changer d’onglet durant le parcours. Les essais positionnent le joueur dans des situations contrôlées et utilisent les vrais corps physiques et les commandes clavier. Ils restaurent les sauvegardes à la fin.

Consulter `TESTS.md` pour les résultats et limites de vérification. Une validation sur un Chromebook réel et l’avis de l’enseignant sur la difficulté restent nécessaires avant diffusion en classe.
