# M4 - Brief 2 - Répliquer, attaquer et corriger la preuve

**Compétences visées**

- C1. Identifier un jeu de données — **niveau 2, adapter** (consolidé)
- C2. Identifier les risques éthiques et sociétaux — **niveau 3, transposer** (consolidé)
- C4. Choisir un modèle IA — **niveau 1, imiter** (consolidé)

## Description

Le brief 1 a produit un modèle simple, un pipeline RAG et une première décision. Cette décision reste fragile tant qu'elle dépend d'un seul corpus, d'un seul jeu d'évaluation et de l'interprétation de son auteur. Votre mission : soumettre les résultats M4 à un lot inédit et à une reproduction indépendante, puis corriger le système et la décision à partir des écarts observés. Ce brief transforme un résultat en preuve.

## Ressources

- État M4 produit au brief 1, ou référence formateur équivalente
- Protocole, configurations et résultats gelés
- Second corpus ou révision documentaire qualifiée
- Lot d'évaluation caché, révélé après le gel du candidat
- `M4/starter/approfondissement/` — grilles de reproduction, remédiation et défense
- `M4/starter/templates/grille_reproduction.md` — grille commune

Le formateur remet le paquet de contradiction dans un canal daté, après le gel : lot capteur inédit, livraison documentaire incrémentale et questions sans labels. Les oracles restent hors du dépôt apprenant.

## Contexte du projet

M4 franchit son gate renforcé quand les résultats essentiels sont reproduits par un tiers et que la décision résiste au nouveau lot, ou est explicitement révisée.

La contradiction est organisée, pas improvisée : un autre apprenant reçoit le dépôt, le protocole et la grille, sans explication orale préalable. Pendant cette phase, l'auteur ne corrige pas.

## Modalités pédagogiques

Travail individuel, avec une phase de contradiction croisée. Durée estimée : 20 heures — 12 h de réalisation, 4 h de contradiction, 4 h de remédiation et défense.

Phases de travail :

1. Réalisation, 12 h — Auditer la transmissibilité : vérifier qu'un tiers peut reconstruire environnement, features, index, prompts, modèle et métriques, et lister les informations manquantes avant de modifier quoi que ce soit.
2. Qualifier le nouveau lot : couverture, révisions, droits, sensibilité, questions non répondables, différences de distribution. Le lot caché ne sert pas à régler les seuils.
3. Rejouer les baselines sans modification : règles M3, modèle M4, retrieval lexical, retrieval vectoriel, génération citée, agent à une étape ; conserver toutes les versions et tous les écarts.
4. Étendre la campagne de menaces : document prioritaire malveillant, instruction indirecte, révision obsolète, conflit entre sources, citation inexistante, question hors périmètre, tentative d'obtenir une donnée restreinte.
5. Formuler une seule correction principale, fondée sur un échec observé — filtre, chunking, modèle, seuil, contrat de citation, règle de refus ou politique de l'agent — en annonçant le gain attendu et les régressions possibles.
6. Contradiction, 4 h — Un pair reconstruit un run principal, vérifie un échantillon de citations, rejoue au moins trois menaces, recherche une fuite de test ou une hypothèse implicite, et produit un rapport distinguant `reproduit`, `écart`, `bloqué` et `non testé`.
7. Remédiation et défense, 4 h — Traiter chaque écart, rejouer les tests concernés, mettre à jour model card, threat model et matrice de décision, conserver les résultats avant et après, défendre la décision finale et le meilleur argument contraire.

## Modalités d'évaluation

Le brief 2 compte pour 35 % du module. L'évaluation porte sur la solidité de la preuve sous contradiction, pas sur le score obtenu.

Le formateur vérifie :
- Le lot caché est resté fermé jusqu'au gel.
- La reproduction ne dépend pas d'une aide orale de l'auteur.
- Les écarts sont conservés, pas effacés.
- Une seule correction principale est attribuable aux résultats observés.
- Les citations et les refus restent vérifiables après correction.
- L'agent reste sans boucle libre ni effet externe.
- La décision révisée est datée et peut rester négative.

Gate renforcé M4 : les résultats essentiels sont reproduits par un tiers et la décision résiste au nouveau lot ou est explicitement révisée.

## Livrables

- Rapport de qualification du nouveau lot.
- Résultats bruts avant correction.
- Campagne de menaces étendue.
- Rapport indépendant signé et daté, distinguant `reproduit`, `écart`, `bloqué`, `non testé`.
- Correction et tests de non-régression.
- Comparaison avant / après.
- Décision M4 révisée.
- Support de défense.
- Journal de bord.

## Critères de performance

- Le lot caché reste fermé jusqu'au gel.
- La reproduction ne dépend pas d'une aide orale.
- Les écarts sont conservés, pas effacés.
- Une seule correction principale est attribuable aux résultats.
- Citations et refus restent vérifiables.
- L'agent reste sans boucle libre ni effet externe.
- La décision peut rester négative, à condition d'être argumentée.
