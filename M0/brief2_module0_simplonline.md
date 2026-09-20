# M0 - Brief 2 - Stabiliser, tester et documenter DiagOps

**Compétences visées**

- C6. Implémenter le modèle d'IA — **niveau 1, imiter**

## Description

La première version de DiagOps fonctionne, mais elle n'a été éprouvée que par vous, sur quelques rapports choisis. Un collègue doit pouvoir reprendre le dépôt, le lancer et comprendre ce que fait l'application sans explication orale. Votre mission : reprendre le même dépôt et les mêmes données, rendre l'application plus fiable et plus lisible, observer le comportement du modèle sur plusieurs rapports et documenter ce que vous constatez, limites comprises. Ce brief transforme un prototype en artefact reprenable.

## Ressources

- Votre dépôt DiagOps issu du brief 1 — artefact repris, jamais recommencé
- `data_pack/2026-S1/reports/` — mêmes rapports que le brief 1
- `data_pack/SCHEMA.md` — contrat de sortie à valider
- `M0/brief2_module0.md` — énoncé complet
- `M0/acquis_m0.md` — état de projet à produire en fin de module

Les autres périodes et les autres sources du data pack restent fermées.

## Contexte du projet

Le module 0 se termine par un état de projet transmis à M1, où le diagnostic sera spécialisé à partir d'un sous-ensemble annoté. M1 part de votre API : si le contrat de sortie n'est pas stable et si le dépôt n'est pas relançable, l'intégration de l'adaptateur en M1 devient impossible à mesurer.

La consolidation porte sur quatre axes : la robustesse, en gérant les entrées vides, les rapports ambigus et les erreurs du modèle ; la validation, en vérifiant que la sortie respecte le schéma attendu ; l'évaluation simple, en comparant plusieurs rapports et en observant les limites du modèle ; la documentation, en expliquant le choix du modèle, le lancement, les routes et les limites.

Documenter les limites du modèle sur étagère n'est pas un aveu d'échec : c'est la baseline que la spécialisation devra battre en M1.

## Modalités pédagogiques

Travail individuel sur le dépôt du brief 1. Durée estimée : 7 heures en autonomie, prolongées par 3 heures de distanciel consacrées à la levée des blocages, à la vérification des livrables et à la production de l'état de projet.

Phases de travail :

1. Robustesse : gérer les entrées vides, les rapports ambigus et les erreurs du modèle.
2. Validation : vérifier que chaque sortie respecte le schéma attendu.
3. Tests : ajouter des tests API couvrant au moins un cas nominal et un cas d'erreur.
4. Observabilité : ajouter des logs applicatifs simples.
5. Évaluation : tester l'application sur au moins 5 rapports et consigner pour chacun le `report_id`, le symptôme extrait, la sévérité proposée, l'hypothèse de panne et la limite observée.
6. Documentation : compléter le `README.md`, dont une section `Choix du modèle` — modèle retenu, adéquation au cas d'usage, limites, alternatives considérées, conditions d'utilisation (licence, taille, dépendances, accès API).

## Modalités d'évaluation

L'évaluation porte sur la fiabilité et la reprenabilité de l'application, pas sur la qualité du modèle sur étagère.

Le formateur vérifie :
- Le dépôt est compréhensible sans explication orale.
- L'application fonctionne de bout en bout.
- Les entrées vides, les rapports ambigus et les erreurs du modèle sont gérés sans interruption du service.
- Le contrat JSON est respecté et effectivement vérifié.
- Le choix du modèle est justifié et ses alternatives sont citées.
- Les limites observées sont rattachées à des rapports précis.
- Les tests se lancent par une commande documentée.

## Livrables

- Dépôt complété, avec l'API et l'interface.
- Gestion explicite des erreurs et logs applicatifs simples.
- Tests API avec au moins un cas nominal et un cas d'erreur.
- `README.md` complet, incluant la section `Choix du modèle`.
- `evaluation_m0.md`, ou section équivalente du README, portant sur au moins 5 rapports.
- Commandes permettant de relancer le projet et les tests.
- `acquis_m0.md` — état de projet transmis à M1.

## Critères de performance

- Le dépôt est compréhensible sans explication orale.
- L'application fonctionne de bout en bout.
- Les erreurs courantes sont gérées.
- Le contrat JSON est respecté.
- Le modèle choisi est justifié.
- Les limites sont explicites et documentées.
- Les tests peuvent être lancés par une commande documentée.
