# M5 - Brief 2 - Conduire un game day de la stack RAG

**Compétences visées**

- C6. Implémenter le modèle d'IA — **niveau 3, transposer** (consolidé)
- C8. Mesurer la performance et les impacts — **niveau 1, imiter** (consolidé)
- C9. Adopter une démarche d'amélioration continue — **niveau 1, imiter** (consolidé)

## Description

Le brief 1 a produit une stack déployable, observable et restaurable sur un parcours nominal. Il faut maintenant vérifier son comportement lorsqu'une nouvelle version et une panne réelle se combinent. Votre mission : préparer une livraison candidate, mesurer sa capacité, subir un incident contrôlé, puis restaurer le service et corriger le dispositif opérationnel. Un runbook qui n'a jamais servi pendant un incident n'est pas un runbook.

## Ressources

- État M5 du brief 1, ou référence formateur équivalente
- Version saine identifiée et restaurable
- Nouvelle révision de corpus ou configuration candidate
- Scénarios d'incident remis par le formateur
- `M5/starter/game_day/` — plan, chronologie, post-incident, remédiation
- `M5/starter/docs/` — runbook, contrat de versions, rapport de rollback

Les objectifs formateur communs fixent une détection en moins de 2 minutes, une décision en moins de 5 minutes, une restauration en moins de 10 minutes et aucune perte de données. L'équipe peut annoncer des objectifs plus exigeants avant l'injection.

## Contexte du projet

Le game day est un exercice, pas une évaluation individuelle de faute : le rapport post-incident distingue cause, facteurs aggravants et symptômes, sans recherche de responsable.

L'incident est injecté par le formateur ou un pair, parmi : index partiellement corrompu, corpus candidat dégradant les citations, serveur de génération indisponible, latence du retrieval multipliée, configuration incompatible, alerte manquante ou trop bruyante. L'équipe observe, qualifie, décide, restaure et chronomètre, sans effacer ni traces ni état initial avant la fin de l'exercice.

## Modalités pédagogiques

Travail individuel pour la préparation, puis exercice contradictoire. Durée estimée : 20 heures — 12 h de préparation, 4 h d'incident contradictoire, 4 h de remédiation et défense.

Phases de travail :

1. Préparation, 12 h — Construire la livraison candidate : versionner code, modèle, corpus, index, prompts et évaluation, produire l'index hors du chemin actif, exécuter les gates, préparer une promotion réversible.
2. Tester la capacité : définir un profil réaliste, mesurer débit, latence p50 et p95, erreurs, mémoire, stockage et coût, identifier le premier point de saturation sans jamais tester un service externe ou de production.
3. Vérifier l'observabilité : chaque panne envisagée doit produire un signal attribuable ; contrôler alertes, seuils, liens vers les versions, rétention et absence de données sensibles dans les traces.
4. Préparer le game day : rôles, canal de décision, conditions d'arrêt, procédure de sauvegarde, rollback, reconstruction et vérification après reprise.
5. Incident, 4 h — Observer, qualifier, décider, restaurer, chronométrer.
6. Remédiation et défense, 4 h — Construire la chronologie, distinguer cause, facteurs aggravants et symptômes, corriger test, alerte, runbook ou architecture, rejouer le scénario ou un test équivalent, vérifier la version saine après restauration, défendre les arbitrages de coût, disponibilité et qualité.

## Modalités d'évaluation

Le brief 2 compte pour 35 % du module. L'évaluation porte sur la conduite de l'incident et la qualité de la remédiation, pas sur l'absence d'incident.

Le formateur vérifie :
- Le candidat ne remplace pas la version saine avant les gates.
- La capacité est mesurée sur un profil annoncé à l'avance.
- L'incident est détecté par le système, et pas seulement signalé par l'animateur.
- Le rollback est exécuté.
- Le rapport évite la recherche de faute individuelle.
- Une remédiation est vérifiée par un rejeu.
- Les objectifs non atteints restent visibles dans le rapport.

Gate renforcé M5 : la stack détecte un incident contrôlé, restaure une version saine et démontre la correction dans les objectifs de reprise annoncés, ou documente leur échec.

## Livrables

- Manifeste de livraison candidate.
- Rapport de capacité, avec profil, mesures et point de saturation.
- Plan et rôles du game day.
- Chronologie et preuves de l'incident.
- Preuve de rollback ou de reconstruction.
- Rapport post-incident.
- Correctif et test de non-régression.
- Runbook révisé.
- Support de défense.

## Critères de performance

- Le candidat ne remplace pas la version saine avant les gates.
- La capacité est mesurée sur un profil annoncé.
- L'incident est détecté par le système.
- Le rollback est exécuté.
- Le rapport évite la recherche de faute individuelle.
- Une remédiation est vérifiée.
- Les objectifs non atteints restent visibles.
