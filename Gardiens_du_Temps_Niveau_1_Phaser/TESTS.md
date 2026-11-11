# Validation du chapitre I — 11 novembre 2026

## Vérifications réalisées

- 6 tests Node réussis : sauvegardes invalides/indisponibles, aller-retour et séparation des clés, les 343 combinaisons d’allocation possibles, ordre de la crue, choix des attaques selon la phase, structure de la question et des rétroactions.
- 22 assertions d’intégration réussies dans Chromium avec Phaser en rendu Canvas : mouvement réel, montée/retombée du saut, dégâts et invulnérabilité, pause, esquive, barrière fermée, deux issues d’irrigation, traversée après ouverture, deux issues de la question, deux issues de la séquence de crue, sauvegarde, reprise, vague simple, double vague, chute d’eau, frappe vulnérable, victoire et écriture de la progression de campagne.
- Transition vers `niveau_2.html` observée dans le navigateur depuis le bouton de continuation d’une sauvegarde terminée.
- Inspection visuelle du paysage, des accessoires, du héros, du menu et du bilan.
- Analyse syntaxique des modules JavaScript.

Les tests d’intégration sont des scénarios contrôlés, avec des repositionnements du joueur et une santé du boss ajustée pour vérifier des branches précises. Ils ne constituent pas une partie complète jouée à la main ni une preuve d’équilibrage.

## Corrections issues des essais

- Dans ce navigateur distant, la boucle requestAnimationFrame ne progressait pas régulièrement entre interactions. La boucle temporisée Phaser à cible 60 Hz a permis de vérifier les déplacements et les collisions.
- Suppression d’accessoires hérités anachroniques et remplacement par un atlas de terre crue et de bois.
- Le mode de validation attend le chargement complet et démarre sans progression, indépendamment d’une sauvegarde de partie terminée.
- Remise à zéro des effets de crue et des projectiles à la reprise; arrêt du traitement après ouverture d’une fenêtre et après la victoire.
- La reprise d’une victoire propose le marché au lieu de réinitialiser le combat.

## Limites

- Pas de test sur matériel Chromebook réel ni de mesure fiable de performance matérielle.
- Pas encore de validation manuelle du parcours complet, de chaque saut optionnel ou de l’équilibrage du combat avec des élèves.
- Le départ automatique après huit secondes est implémenté; la navigation manuelle vers le marché a été observée. Le scénario automatisé suspend le compte à rebours pour permettre l’inspection du bilan.
- Les six poses du Gardien rendent ses états lisibles, mais ne sont pas une animation dessinée à chaque image. Le héros utilise les poses existantes.
- Les niveaux II à V restent ceux du jeu d’origine; leur moteur, leurs sauvegardes et leurs éventuels défauts ne sont pas refondus dans cette étape.

## Suite de la validation — même journée

- 7 tests Node réussis après ajout de la persistance des réglages partiels d’irrigation, avec validation des valeurs chargées.
- Réglages des prises conservés après fermeture du panneau et rechargement; les anciennes sauvegardes restent compatibles.
- Protection du déclenchement du saut pendant le décollage, remise à zéro des délais d’action et des couleurs des postes à la reprise.
- Ajout de scénarios navigateur pour une perte de focus répétée, la réouverture du panneau d’irrigation et le déclenchement automatique de la transition après huit secondes.
- Ces nouveaux scénarios navigateur ne sont pas encore validés : Chromium local ne peut pas démarrer (socket interdit); le navigateur distant n’a pas pu rejoindre le serveur de test et sa politique a ensuite bloqué le rechargement. Les 22 résultats ci-dessus sont ceux de la validation précédente, pas une validation de cette révision.
