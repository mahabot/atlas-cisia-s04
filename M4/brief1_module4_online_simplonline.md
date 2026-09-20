# M4 - Brief 1 online - Concevoir une IA simple pour un nouveau besoin

**Compétences visées**

- C1. Identifier un jeu de données — **niveau 2, adapter**
- C2. Identifier les risques éthiques et sociétaux — **niveau 3, transposer**
- C4. Choisir un modèle IA — **niveau 1, imiter**

## Description

DiagOps doit répondre à un nouveau besoin, et la question n'est pas de savoir quel modèle est à la mode, mais lequel est justifiable. Votre mission : faire évoluer la conception de DiagOps depuis l'analyse métier jusqu'au choix argumenté d'un modèle, en couvrant explicitement C1, C2 et C4 du programme CampusAtlas. Recommander de rester sans modèle est une conclusion recevable si les preuves la soutiennent.

## Ressources

- `data_pack/2026-S1/` — sources disponibles du corpus DiagOps
- `data_pack/SCHEMA.md`, `MANIFEST.yaml`, `DATA_CARD.md` — description, droits et limites
- `data_pack/2026-S1/reference_runs/m3_for_m4/` — état de référence M3
- `M4/starter/templates/dossier_conception_online.md` — gabarit du dossier
- `M4/RESOURCES.md` — ressources techniques du module

## Contexte du projet

Ce brief couvre le programme officiel CampusAtlas du module 4 : analyser le besoin, identifier les données nécessaires, comparer des familles de modèles, intégrer les contraintes opérationnelles et d'éco-conception, communiquer les risques et documenter les choix.

Il est autonome : il n'exige pas d'avoir terminé le brief présentiel et ne demande ni RAG, ni agent, ni base vectorielle. Les preuves de modernisation produites en présentiel ne remplacent pas les preuves C1 à C4 attendues ici.

## Modalités pédagogiques

Travail individuel. Durée estimée : 6 heures — 3 h en classe virtuelle pour le cadrage, la revue du protocole et la confrontation des choix, puis 3 h de travail autonome pour le dossier de conception et la recommandation finale.

Phases de travail :

1. Analyser le besoin : utilisateurs directs et indirects, décision assistée, résultats attendus, erreurs coûteuses, contraintes de délai, conditions de supervision humaine.
2. Identifier les données nécessaires : unité d'observation et cible, sources disponibles et manquantes, pertinence, cohérence et représentativité, accès, droits et confidentialité, volume minimal défendable, biais et périmètre de validité.
3. Comparer au moins trois familles de modèles — règles, supervisé, non supervisé, pré-entraîné — sur les données requises, l'explicabilité, la capacité de généralisation, le coût, la maintenance et les contraintes d'apprentissage.
4. Définir l'évaluation : métriques, jeux de calibration et de test, seuils d'acceptation, analyse ROC lorsque la cible s'y prête, mesure par segment, conditions de réévaluation.
5. Analyser les risques : impacts directs et indirects, données sensibles, biais, sécurité, éco-conception, cadre réglementaire, en distinguant obligations établies, interprétations et points à valider juridiquement.
6. Recommander : choisir un modèle ou recommander de rester sans modèle, avec preuves, limites, mesures d'atténuation et informations manquantes susceptibles de changer la décision.

## Modalités d'évaluation

Le brief online compte pour 30 % du module. L'évaluation porte sur la qualité du raisonnement de conception, pas sur une implémentation.

Le formateur vérifie :
- Le besoin est formulé comme une décision observable.
- Les données sont reliées au besoin, et non simplement inventoriées.
- Le modèle est choisi contre des alternatives explicites.
- Les performances attendues sont mesurables et assorties de seuils.
- Les risques sont communiqués avec leurs atténuations et leurs limites.
- Chaque choix est documenté de façon transmissible.

## Livrables

- `dossier_conception_m4.md`.
- Tableau des données nécessaires.
- Comparaison des familles de modèles.
- Protocole d'évaluation.
- Registre des risques.
- Décision finale datée.
- Entrée dans le journal de bord.

## Critères de performance

- Le besoin est formulé comme une décision observable.
- Les données sont reliées au besoin et non simplement inventoriées.
- Le modèle est choisi contre des alternatives.
- Les performances attendues sont mesurables.
- Les risques sont communiqués avec leurs atténuations et limites.
- Chaque choix est documenté de façon transmissible.
