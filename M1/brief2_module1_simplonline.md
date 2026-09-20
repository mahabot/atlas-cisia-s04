# M1 - Brief 2 - Qualifier et intégrer le candidat DiagOps

**Compétences visées**

- C5. Entraîner le modèle d'IA — **niveau 1, imiter**
- C6. Implémenter le modèle d'IA — **niveau 2, adapter**

## Description

Le candidat retenu après la revue distancielle est gelé. Votre mission : ouvrir le jeu de test final, qualifier la robustesse et le coût du candidat, puis l'intégrer à DiagOps sans modifier le contrat public `POST /diagnose`. Le test final se consulte une seule fois, après le gel : aucun hyperparamètre n'est ajusté à partir de ses résultats. Votre décision finale est l'une des trois suivantes — promouvoir, ne pas promouvoir, prolonger l'expérimentation avec une hypothèse et une prochaine étape précises.

## Ressources

- Votre application DiagOps issue de M0 — contrat `POST /diagnose` à préserver
- `data_pack/2026-S1/annotations/diagops_test.jsonl` — 100 exemples, ouverts une seule fois
- Résultats du brief 1 et de la revue distancielle — candidat gelé et objections traitées
- `M1/starter/` — entraînement, évaluation, conteneurisation
- `M1/starter/templates/model_card.md` et `individual_evidence.md` — gabarits de rendu

## Contexte du projet

M1 clôt la question de la spécialisation et transmet à M2 un état de projet où le modèle est soit promu, soit explicitement écarté — dans les deux cas avec des mesures.

L'intégration doit rester réversible : l'adaptateur est chargé séparément du modèle de base et le choix baseline ou LoRA se fait par configuration. Le schéma Pydantic reste celui de M0, le contrat public `/diagnose` n'est pas modifié, les erreurs de chargement et d'inférence sont gérées, les tests couvrent baseline et LoRA, la procédure locale est documentée pour Mac et PC, et la conteneurisation de l'API est reproductible sans exiger de GPU dans Docker.

Les modules suivants repartent de cette API : une rupture du contrat public à ce stade se paierait en M4, M5 et M6.

## Modalités pédagogiques

Travail en autonomie, avec une preuve individuelle obligatoire. Durée estimée : 7 heures.

Les 20 perturbations de robustesse sont dérivées de rapports du test sans modifier leur sens attendu. Elles couvrent au moins : fautes de frappe ou abréviations, ordre des phrases modifié, information secondaire ajoutée, équipement placé en fin de rapport, formulation plus courte, symptômes multiples, absence d'identifiant d'équipement, rapport ambigu nécessitant une revue humaine. Pour chaque famille, la plausibilité et la vérification de la stabilité du sens sont expliquées.

Phases de travail :

1. 00:00–00:45 — Reproduire le candidat depuis un environnement propre : hash de configuration et journal de reprise.
2. 00:45–01:30 — Exécuter baseline et candidat sur les 100 tests : prédictions et métriques finales gelées.
3. 01:30–02:30 — Concevoir les 20 perturbations de robustesse : `robustness_cases.jsonl`.
4. 02:30–03:30 — Exécuter la comparaison A/B sur la robustesse.
5. 03:30–04:30 — Analyser les résultats par champ, sévérité et type d'échec.
6. 04:30–05:15 — Mesurer latence, débit et mémoire sur la plateforme commune.
7. 05:15–06:00 — Intégrer baseline et LoRA derrière la même interface, avec tests de non-régression de `/diagnose`.
8. 06:00–07:00 — Rédiger la model card et défendre la décision en 8 minutes.

## Modalités d'évaluation

L'évaluation porte sur la qualification du candidat et sur la qualité de l'intégration, pas sur la promotion elle-même.

Seuils conditionnant la promotion, et non la réussite du module : JSON brut parseable au moins 95 %, schéma valide 100 %, exactitude `equipment_id` au moins 95 %, macro-F1 `severity` au moins 0,80, exactitude `requires_human_review` au moins 95 %, score lexical moyen des champs textuels au moins 0,65, régression de latence p95 inférieure ou égale à 20 % sauf justification, gain de 10 points sur le score composite face à la baseline ou autre bénéfice mesurable explicitement défendu.

Le formateur vérifie :
- Un tiers peut reproduire le candidat sans explication orale.
- Le test final n'a servi à aucun ajustement.
- La comparaison A/B est équitable et auditable.
- La robustesse est testée sur des transformations justifiées, de sens stable.
- Les coûts opérationnels sont mesurés, pas estimés.
- L'API reste compatible avec M0.
- La décision respecte les seuils et reconnaît ses limites.
- Chaque apprenant remet sa fiche individuelle et démontre sa compréhension.

## Livrables

- Adaptateur LoRA et configuration PEFT.
- Référence exacte du modèle de base et du tokenizer.
- Prédictions et métriques finales gelées.
- `robustness_cases.jsonl` — 20 perturbations motivées.
- Analyse des erreurs par champ, sévérité et type d'échec.
- Rapport de performance : latence, débit, mémoire.
- Application DiagOps mise à jour, baseline et LoRA derrière la même interface.
- Tests de non-régression de `/diagnose` et commandes de lancement.
- Procédure locale documentée pour Mac et PC.
- Model card et note de décision.
- Fiche individuelle : configuration exécutée ou reproduite, deux erreurs analysées personnellement, une objection traitée, recommandation, preuve de chargement du candidat et d'appel de `/diagnose`.
- Restitution de 8 minutes et réponses aux questions.

## Critères de performance

- Un tiers peut reproduire le candidat sans explication orale.
- Le test final n'a servi à aucun ajustement.
- La comparaison A/B est équitable et auditable.
- La robustesse est testée sur des transformations justifiées.
- Les coûts opérationnels sont mesurés.
- L'API reste compatible avec M0.
- La décision respecte les seuils et reconnaît les limites.
- Chaque apprenant démontre sa contribution et sa compréhension.
