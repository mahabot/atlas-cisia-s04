# M5 - Brief 1 online - Déployer, monitorer et intégrer l'évaluation

**Compétences visées**

- C6. Implémenter le modèle d'IA — **niveau 3, transposer**
- C8. Mesurer la performance et les impacts — **niveau 1, imiter**
- C9. Adopter une démarche d'amélioration continue — **niveau 1, imiter**

## Description

Un modèle qui fonctionne sur un poste n'est pas une solution exploitable. Votre mission : déployer une solution IA existante dans une chaîne de livraison continue, identifier les métriques utiles et intégrer son évaluation au processus MLOps, jusqu'à démontrer une livraison candidate et sa restauration. Le brief est autonome et peut s'appuyer sur un modèle simple fourni par le formateur.

## Ressources

- Artefact modèle fourni par le formateur, ou votre propre artefact M4
- `data_pack/2026-S1/reference_runs/m4_for_m5/` — versions liées et résultats de référence
- `M5/starter/deploy/` — Dockerfile, Compose et configuration Prometheus
- `M5/starter/pipelines/` — construction d'index, évaluation, promotion, rollback
- `M5/starter/monitoring/` — contrat de métriques et tableaux de bord
- `M5/RESOURCES.md` — ressources techniques du module

## Contexte du projet

Ce brief couvre le programme officiel CampusAtlas du module 5 : conteneurisation, versionnement du modèle et des données, CI/CD, métriques, tableaux de bord et documentation du cycle de vie. Il reste autonome du RAG traité en présentiel et peut s'appuyer sur un service simple.

La distinction entre préproduction et production est structurante : la CI publie vers la préproduction, la production reste soumise à une décision explicite.

## Modalités pédagogiques

Travail individuel. Durée estimée : 6 heures — 3 h en classe virtuelle sur l'architecture de livraison, les métriques et la revue des déclencheurs, puis 3 h en autonomie pour l'implémentation, le test et la documentation.

Phases de travail :

1. Comprendre l'artefact : documenter entrées, sorties, paramètres, dépendances, version et résultats de référence du modèle fourni.
2. Conteneuriser : image reproductible, configuration externe, health check et commande de test de fumée.
3. Versionner : relier versions du code, du modèle, des données et des résultats ; expliquer ce qui déclenche une nouvelle version et ce qui peut rester inchangé.
4. Automatiser la validation : la CI exécute tests, évaluation minimale, construction de l'artefact et publication en préproduction.
5. Monitorer : définir les métriques de santé système, de stabilité des données, de performance du modèle et d'usage ; pour chacune, fixer source, fréquence, seuil, destinataire et action attendue.
6. Tester et documenter : exécuter une livraison candidate, conserver les preuves et documenter une procédure de restauration.

## Modalités d'évaluation

Le brief online compte pour 30 % du module. L'évaluation porte sur la chaîne de livraison et sur le lien entre métrique et décision, pas sur la performance du modèle fourni.

Le formateur vérifie :
- L'artefact est reconstruisible depuis le dépôt.
- L'évaluation est un gate de la livraison, pas un rapport annexe.
- Chaque métrique est reliée à un seuil, un destinataire et une action.
- Le modèle et les données sont versionnés et reliés aux résultats.
- Préproduction et production sont distinguées, la mise en production reste décidée.
- La restauration est vérifiable, pas seulement décrite.

## Livrables

- Conteneur et configuration externe.
- Workflow CI/CD.
- Registre de versions reliant code, modèle, données et résultats.
- Tableau des métriques et des déclencheurs : source, fréquence, seuil, destinataire, action.
- Tableau de bord ou export équivalent.
- Rapport de livraison candidate avec ses preuves.
- Procédure de rollback.
- Journal de bord.

## Critères de performance

- L'artefact est reconstruisible.
- L'évaluation est un gate de la livraison.
- Les métriques sont reliées à une décision.
- Modèle et données sont versionnés.
- Préproduction et production sont distinguées.
- La restauration est vérifiable.
