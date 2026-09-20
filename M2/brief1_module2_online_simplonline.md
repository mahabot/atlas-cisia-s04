# M2 - Brief 1 online - Explorer les données de maintenance avec Pandas et Seaborn

**Compétences visées**

- C1. Identifier un jeu de données — **niveau 1, imiter**
- C3. Préparer les données — **niveau 1, imiter**

## Description

Le responsable maintenance souhaite comprendre les données disponibles avant de lancer une étude prédictive. Votre mission : produire un notebook qui décrit le parc, les événements et les interventions, contrôle les jointures, examine la qualité des valeurs et recommande les variables utilisables pour une future modélisation. Les fichiers contiennent volontairement des valeurs manquantes, des doublons et des valeurs atypiques : il faut les observer et les interpréter avant de décider d'un traitement.

## Ressources

- `data_pack/2026-S1/equipment/` — équipements et caractéristiques du parc
- `data_pack/2026-S1/events/` — incidents, observations et alertes
- `data_pack/2026-S1/maintenance/` — interventions, durées d'arrêt, temps de travail, coûts de pièces
- `M2/starter/notebooks/m2_statistiques_atlas.ipynb` — notebook de départ
- `M2/RESOURCES.md` — ressources techniques du module

## Contexte du projet

Ce brief couvre le socle Atlas du module 2 : statistiques descriptives, valeurs atypiques, corrélations, transformations usuelles, Pandas et Seaborn. Il est autonome et ne dépend pas des productions du brief présentiel, mais il porte sur les mêmes fichiers : les deux briefs traitent la même question — que valent ces données — par deux moyens différents.

Le notebook se structure en quatre parties : chargement et compréhension, description statistique, qualité et relations entre variables, recommandation.

## Modalités pédagogiques

Travail individuel, chacun dans son environnement, à partir du même notebook de départ. Durée estimée : 6 heures — 3 h en classe virtuelle et 3 h de travail autonome. L'ordre des analyses n'est pas imposé. La classe virtuelle sert à clarifier les notions, vérifier les jointures et comparer les interprétations.

Phases de travail :

1. Chargement et compréhension : charger et inspecter les trois tables, expliquer ce que représente une ligne, identifier colonnes, types et clés, réaliser les jointures utiles et contrôler le nombre de lignes avant et après chacune.
2. Description statistique : effectifs et fréquences, mode, moyenne et médiane, quartiles, déciles et centiles, variance, écart-type et distance interquartile, comparaison d'au moins deux populations.
3. Qualité et relations : valeurs manquantes et doublons, valeurs atypiques repérées par l'IQR et l'écart à la moyenne, matrice de corrélation de Pearson, vérification visuelle des relations, effet d'une valeur extrême sur au moins un résultat, comparaison normalisation / standardisation sur deux variables, encodage d'une variable catégorielle justifié.
4. Recommandation : classer les variables en utilisables en l'état, à nettoyer ou mieux documenter, à écarter provisoirement, en justifiant à partir des calculs et des graphiques.

Le notebook contient au moins un histogramme, un boxplot, un graphique de comparaison de catégories, un nuage de points et une matrice de corrélation. Chaque graphique répond à une question, porte un titre et est suivi d'une courte interprétation.

## Modalités d'évaluation

Le brief online compte pour 30 % du module. L'évaluation porte sur la justesse des calculs Atlas et sur la qualité des interprétations, pas sur le nombre de graphiques.

Le notebook doit répondre à seize questions, réparties en cinq blocs : comprendre les fichiers et les jointures, décrire le parc et les interventions, examiner la qualité, étudier les relations entre variables, préparer une utilisation future.

Le formateur vérifie :
- Les trois tables et leurs clés sont comprises.
- Les jointures sont contrôlées avant et après.
- Les notions Atlas demandées sont calculées correctement.
- Les graphiques sont lisibles et interprétés.
- Les valeurs manquantes, doublons et valeurs atypiques font l'objet d'une décision argumentée.
- Corrélation et causalité ne sont pas confondues.
- Normalisation et standardisation sont comparées.
- Le notebook s'exécute de bout en bout depuis les fichiers reçus.

Critères bloquants : notebook non exécutable ; suppression de lignes sans justification ni état avant/après ; jointure dont l'effet sur le nombre de lignes n'est pas contrôlé ; corrélation présentée comme une causalité ; graphique sans interprétation ; conclusion sans lien avec les calculs.

## Livrables

- Notebook `m2_statistiques_atlas.ipynb` complété, exécutable de bout en bout avec des chemins relatifs ou configurables.
- Export HTML du notebook.
- Entrée M2 dans le journal de bord.

La conclusion se trouve dans le notebook : aucun rapport séparé n'est demandé.

## Critères de performance

- Les trois tables et leurs clés sont comprises.
- Les jointures sont contrôlées.
- Les notions Atlas demandées sont calculées correctement.
- Les graphiques sont lisibles et interprétés.
- Les valeurs manquantes, doublons et valeurs atypiques font l'objet d'une décision argumentée.
- Corrélation et causalité ne sont pas confondues.
- Normalisation et standardisation sont comparées.
- La recommandation finale est reliée aux résultats obtenus.
- Le notebook est lisible et exécutable.
