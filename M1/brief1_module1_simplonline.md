# M1 - Brief 1 - Construire et contester l'expérience LoRA

**Compétences visées**

- C5. Entraîner le modèle d'IA — **niveau 1, imiter**

## Description

DiagOps dispose d'une application et d'un contrat JSON stable, mais le modèle sur étagère intégré en M0 n'a jamais vu un rapport de maintenance. L'équipe envisage de spécialiser `Qwen/Qwen3-0.6B` par un adaptateur LoRA. Votre mission : établir par l'expérience si cette adaptation apporte un bénéfice mesurable face au modèle brut, en construisant un protocole, en comparant quatre systèmes dans les mêmes conditions et en défendant votre décision devant un groupe qui cherchera à l'invalider. Le but n'est pas de promouvoir le modèle : une non-promotion argumentée est une réussite.

## Ressources

- `data_pack/2026-S1/annotations/diagops_train.jsonl` — 400 paires annotées, partagées 320 / 80 par le starter avec la seed `42`
- `data_pack/SCHEMA.md` — contrat de sortie DiagOps
- `M1/starter/` — code d'entraînement, d'évaluation et de diagnostic d'environnement
- `M1/starter/configs/` — configuration de référence et gabarits de variation
- `M1/starter/templates/` — `protocol_m1.md`, `error_analysis.md`, `peer_review.md`
- `M1/RESOURCES.md` — ressources techniques du module

`diagops_test.jsonl` est réservé au brief 2 : il n'est ni chargé, ni exploré, ni utilisé pour choisir une configuration pendant ce brief.

## Contexte du projet

M1 reprend l'application livrée en M0 et son contrat `POST /diagnose`. La question du module est directrice : la spécialisation LoRA améliore-t-elle suffisamment DiagOps pour justifier son intégration ?

Le modèle et sa révision sont imposés pour que les résultats soient comparables entre apprenants : `Qwen/Qwen3-0.6B`, révision Hugging Face `c1899de289a04d12100db370d81485cdf75e47ca`. Le système comparé est constitué de la baseline brute et de trois configurations LoRA, avec le même prompt, le même template de chat et les mêmes paramètres de génération.

La configuration de référence est fournie : LoRA sur `q_proj`, `k_proj`, `v_proj`, `o_proj`, rang 16, alpha 32, dropout 0.05, longueur maximale 512, batch 4, accumulation 4, trois epochs, learning rate `2e-4`, scheduler cosine, warmup 0.1, seed 42. Le run de référence reste intact ; chaque variation modifie une seule variable et porte une hypothèse écrite avant exécution.

Le dépôt et l'analyse s'utilisent depuis macOS, Linux ou Windows. Les runs de référence sont exécutés sur l'environnement GPU commun. Docker n'est pas requis pour l'entraînement.

## Modalités pédagogiques

Travail en groupe de deux ou trois sur un dépôt commun. Durée estimée : 7 heures en présentiel.

Les rôles tournent à chaque run : pilote expérimental, qui formule l'hypothèse et choisit la variable ; opérateur, qui contrôle la configuration, lance le run et conserve les logs ; analyste, qui vérifie les exports et interprète les résultats. Chaque apprenant est responsable d'au moins un run ou d'une analyse identifiable. Une attente de GPU ne remplace aucune activité : pendant un run, le groupe prépare l'analyse, contrôle les données ou vérifie la reproductibilité.

Trois niveaux d'assistance sont disponibles — guidé, standard, approfondissement — sans modifier les livrables obligatoires.

Phases de travail :

1. 00:00–00:45 — Prendre en main le starter, vérifier les données et l'environnement : `environment.json` et contrôle des volumes.
2. 00:45–01:30 — Formuler les hypothèses et figer le protocole : `protocol_m1.md` versionné.
3. 01:30–02:15 — Mesurer la baseline sur les 80 exemples de validation.
4. 02:15–03:00 — Entraîner et évaluer le LoRA de référence.
5. 03:00–04:00 — Réaliser deux variations contrôlées, une variable chacune.
6. 04:00–05:00 — Comparer les quatre systèmes et analyser au moins 12 erreurs : `metrics_m1.csv` et `error_analysis.md`.
7. 05:00–05:45 — Revue contradictoire entre groupes : `peer_review.md`.
8. 05:45–07:00 — Corriger une faiblesse ou relancer un essai ciblé, puis restituer la décision intermédiaire en 5 minutes.

## Modalités d'évaluation

L'évaluation porte sur la qualité du protocole et la solidité de la décision, pas sur le score obtenu. Une capture d'écran n'est pas une preuve : les prédictions, les métriques, les configurations et l'environnement sont exportés.

Métriques obligatoires : JSON brut parseable, conformité au schéma après validation, exactitude `equipment_id`, macro-F1 de `severity`, exactitude de `requires_human_review`, score lexical normalisé des champs textuels, latence médiane et p95, débit, mémoire maximale de l'accélérateur, sorties vides ou en erreur.

Le formateur vérifie :
- Le test final n'a pas été consulté.
- Les quatre systèmes sont comparés dans les mêmes conditions.
- Chaque variation répond à une hypothèse formulée avant l'exécution.
- Au moins 12 erreurs sont classées et interprétées.
- Chaque membre du groupe laisse une preuve individuelle.
- Le groupe relecteur a tenté d'invalider un point — fuite entre entraînement et validation, paramètres divergents, variable non contrôlée, métrique mal définie, moyenne masquant une classe faible, conclusion non soutenue — et l'objection a produit une réponse observable.

## Livrables

- Dépôt ou notebook reproductible.
- `environment.json` — backend, accélérateur, mémoire disponible, versions logicielles, durée du run.
- `protocol_m1.md` versionné.
- Configurations de la baseline et des trois runs LoRA.
- Prédictions et `metrics_m1.csv` ou équivalent JSON.
- `error_analysis.md` portant sur au moins 12 erreurs classées.
- `peer_review.md` — objection reçue, preuve et réponse apportée.
- Preuve d'une correction ou d'une relance ciblée, avant et après.
- Décision intermédiaire : candidat retenu, rejeté ou à réexpérimenter.

## Critères de performance

- Le test final n'a pas été consulté.
- Les quatre systèmes sont comparés dans les mêmes conditions.
- Chaque variation répond à une hypothèse formulée à l'avance.
- Au moins 12 erreurs sont classées et interprétées.
- Chaque membre laisse une preuve individuelle.
- Une objection de revue produit une réponse observable.
- La décision cite des résultats précis, y compris en cas de non-promotion.
