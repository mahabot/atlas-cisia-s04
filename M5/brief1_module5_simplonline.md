# M5 - Brief 1 - Mettre le RAG sous contrôle opérationnel

**Compétences visées**

- C6. Implémenter le modèle d'IA — **niveau 3, transposer**
- C8. Mesurer la performance et les impacts — **niveau 1, imiter**
- C9. Adopter une démarche d'amélioration continue — **niveau 1, imiter**

## Description

M4 a livré des baselines et une décision. L'équipe veut maintenant exploiter le système dans un environnement reproductible. Le risque principal n'est plus seulement une mauvaise réponse : c'est un changement de modèle, de corpus, d'index ou de prompt impossible à relier au comportement observé. Votre mission : construire la chaîne de livraison et d'observation de DiagOps, puis prouver qu'une version dégradée peut être détectée et restaurée. Ce brief marque le passage d'un prototype prouvé à un service opérable.

## Ressources

- `data_pack/2026-S1/reference_runs/m4_for_m5/` — référence `diagops-m4-reference-r1`
- Jeux d'évaluation M4 gelés, contrats de citation, refus et agent à une étape
- `data_pack/2026-S2/` — période supplémentaire, seulement lorsqu'elle est publiée et qualifiée
- `M5/starter/` — API instrumentée, constructeur d'index atomique, gate de livraison, promotion réversible, modèles de preuve du game day
- `tools/check_m5_release.py` — vérification d'intégrité avant démarrage
- `veille_diagops/` dans votre dépôt — dossier transmis par M4
- `M5/RESOURCES.md` — ressources techniques du module

L'intégrité de la référence est vérifiée avant le démarrage du module.

## Contexte du projet

Une réponse produite en exploitation doit être attribuable à des versions identifiées : code, configuration, modèle, corpus, manifeste, stratégie de chunking, modèle d'embeddings, index, prompts et jeu d'évaluation.

L'ingestion doit devenir idempotente : valider manifeste, droits, sensibilité et checksum, détecter ajout, modification, retrait et conflit de révision, produire un nouvel index sans écraser l'index sain, ne publier qu'après évaluation, conserver une procédure de retour arrière.

L'observation porte sur trois plans distincts — service, retrieval et réponse — et les traces ne contiennent ni document sensible complet, ni prompt portant une donnée personnelle ; leur rétention et leurs accès sont définis.

L'autonomie de l'agent n'augmente pas en M5 : l'agent reste à une étape. Les outils arrivent en M6.

## Modalités pédagogiques

Travail individuel. Durée estimée : 14 heures en présentiel, dont environ 1 heure de checkpoint réglementaire incluse dans le quota.

Phases de travail :

1. Identifier les unités versionnées : attribuer version et checksum à chaque unité, de façon qu'un run de production permette de toutes les retrouver.
2. Conteneuriser les composants : séparer au minimum API, retrieval/index et observabilité, même sur une seule machine ; ajouter health checks, timeouts, limites de ressources et configuration hors code.
3. Rendre l'ingestion idempotente, avec publication d'index différée à l'évaluation et retour arrière conservé.
4. Construire les gates de CI : tests unitaires et contrats API, intégrité du manifeste, évaluation retrieval réduite, citations résolubles et refus attendus, régressions de latence et mémoire, cas de prompt injection indirecte, absence de secret et d'actif restreint dans les artefacts.
5. Observer trois plans : service — disponibilité, erreurs, débit, latence, ressources ; retrieval — documents sans résultat, top-k, versions, index, filtres ; réponse — refus, citations, validation de schéma, revue humaine, coût.
6. Tester une livraison et un rollback : déployer un candidat en préproduction, exécuter les gates, injecter une régression contrôlée, puis démontrer détection, alerte, décision, restauration et vérification après rollback.
7. Documenter l'exploitation : runbook couvrant démarrage, arrêt, réindexation, incident, rollback, rotation des secrets, sauvegarde et responsable de chaque décision.
8. Exécuter le checkpoint réglementaire M5 : vérifier sur sources officielles datées les exigences liées au déploiement, aux fournisseurs, aux traces, à la rétention, à la supervision et aux incidents ; consigner l'entrée M5 ; traduire la décision dans le runbook, les gates, les accès aux traces ou les alertes ; transmettre à M6 les questions ouvertes avec responsable et échéance.

## Modalités d'évaluation

Le brief présentiel compte pour 35 % du module. Les dimensions notées au niveau du module sont : C6 intégration et exploitation 30 %, C9 chaîne contrôlée et rollback 25 %, C8 observabilité multi-plan 20 %, reproductibilité et sécurité de livraison 15 %, documentation 10 %.

Le formateur vérifie :
- Toute réponse est attribuable à des versions identifiées.
- La réindexation est idempotente et atomique du point de vue du service.
- Une régression bloque effectivement la promotion.
- Les métriques distinguent service, retrieval et réponse.
- Le rollback est exécuté, pas seulement décrit.
- La décision réglementaire M5 est reliée à au moins un contrôle d'exploitation, ou son absence d'impact est justifiée.
- L'autonomie de l'agent n'a pas augmenté.

## Livrables

- Configuration de conteneurisation.
- Pipeline d'ingestion et publication d'index.
- CI d'évaluation avec ses gates.
- Configuration de métriques et tableaux de bord.
- `docs/contrat_versions.md`.
- `docs/runbook.md`.
- `docs/rapport_rollback.md`.
- Entrée M5 et passage de relais dans `veille_diagops/`.
- Journal de bord.

## Critères de performance

- Toute réponse est attribuable à des versions identifiées.
- La réindexation est idempotente et atomique du point de vue du service.
- Une régression bloque la promotion.
- Les métriques distinguent service, retrieval et réponse.
- Le rollback est exécuté, pas seulement décrit.
- La décision réglementaire M5 est reliée à un contrôle d'exploitation.
- L'autonomie de l'agent n'augmente pas en M5.

## Hors périmètre

Nouvel outil agentique, traité en M6 ; réentraînement automatique sans décision humaine ; outil à effet ; orchestration multi-agent.
