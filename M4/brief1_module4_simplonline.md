# M4 - Brief 1 - Prouver avant d'architecturer

**Compétences visées**

- C1. Identifier un jeu de données — **niveau 2, adapter**
- C2. Identifier les risques éthiques et sociétaux — **niveau 3, transposer**
- C4. Choisir un modèle IA — **niveau 1, imiter**

## Description

DiagOps dispose d'une pipeline multi-source, d'une baseline par règles et d'un corpus documentaire versionné. L'équipe souhaite ajouter un modèle simple et un assistant capable de consulter les procédures de maintenance. Un prototype qui produit une réponse plausible ne suffit pas. Votre mission : construire deux preuves de valeur reliées par un même dossier de conception — comparer la baseline M3 à des modèles simples sur une cible explicitement définie, et comparer une réponse sans contexte à plusieurs stratégies de retrieval, puis borner un agent à la décision de consulter ou de refuser. Ce brief établit ce qui fonctionne, sur quelles données, à quel coût et avec quelles limites.

## Ressources

- `data_pack/2026-S1/reference_runs/m3_for_m4/` — état de référence M3
- `data_pack/2026-S1/model_eval/` — `sensor_calibration.csv` et `sensor_test.csv` sans étiquette
- `data_pack/2026-S1/knowledge/` — manifeste documentaire et documents associés
- `data_pack/2026-S1/rag_eval/` — questions gelées, labels de test scellés
- `data_pack/SCHEMA.md` — contrat de sortie DiagOps
- `M4/starter/` — contrats, retrieval lexical, bornes de l'agent, tests de menaces, gabarits
- `veille_diagops/` dans votre dépôt — mission ouverte en M0, consolidée ici
- `M4/RESOURCES.md` — ressources techniques du module

N'ouvrez pas le module si le manifeste documentaire ne précise pas droits, sensibilité, révision et checksum, si les checksums ne sont pas valides, ou si les oracles de test ne sont pas scellés côté formateur.

## Contexte du projet

M4 ouvre la trajectoire RAG et agentique qui court jusqu'en M8. Deux décisions doivent être cadrées avant toute mesure.

Pour le modèle capteur, la cible ne se confond ni avec la provenance réelle ou fabriquée, ni avec l'anomalie de qualité, ni avec l'anomalie métier ou la panne future. Le lot actuel permet de travailler la provenance et certaines anomalies de qualité ; il ne prouve pas à lui seul la prédiction d'une panne future.

Pour le RAG, il faut définir les utilisateurs, les questions autorisées, les documents admissibles, les conséquences d'une mauvaise réponse et les cas où le refus est requis.

L'agent introduit ici reste à une seule étape, sans mémoire longue, sans boucle et sans outil d'écriture. Les extraits récupérés sont des données, jamais des instructions. Le formateur calcule les métriques finales sur l'oracle scellé après gel du candidat : seul ce résultat daté entre dans la décision de test.

## Modalités pédagogiques

Travail individuel. Durée estimée : 14 heures en présentiel, dont environ 1 heure consacrée à la consolidation de la veille réglementaire.

Phases de travail :

1. Cadrer les deux décisions : cible du modèle capteur sans confusion de nature, périmètre du RAG et cas de refus.
2. Geler le protocole : séparer calibration et test, utiliser `window_id` comme groupe indivisible, vérifier l'absence de fuite par équipement, conserver la baseline par règles M3 sans la réécrire, définir métriques et seuils, consigner versions, graines et environnement.
3. Comparer au moins deux modèles simples adaptés à la cible, chaque choix justifié contre une alternative : matrice de confusion, précision, rappel, F1, ROC-AUC, stabilité par segment, latence et mémoire, comparés aux règles M3.
4. Construire les baselines de retrieval : sans retrieval, lexical, vectoriel avec un modèle d'embeddings documenté, hybride seulement si les deux précédentes sont stables. Mesurer Recall@k ou hit rate documentaire, précision du contexte, latence et taille de l'index. Un index local reproductible suffit.
5. Générer avec preuves et abstention : citer des `document_id` présents au manifeste, distinguer preuve et interprétation, refuser quand `answerable=false` ou quand les preuves sont insuffisantes, signaler les conflits de révision.
6. Ajouter l'agent à une étape : `answer_without_tool`, `search_knowledge` ou `abstain`, avec un schéma structuré exposant le choix, sa justification, la requête et le résultat.
7. Tester les menaces : instruction malveillante dans un document, document obsolète bien classé, sources contradictoires, demande de donnée sensible, tentative de forcer l'agent, corpus incomplet. Pour chacune : attaque, détection, atténuation, résultat, risque résiduel.
8. Décider : matrice séparant qualité, robustesse, latence, mémoire, coût par réponse, complexité d'exploitation et réversibilité, puis conclusion — adopter, évaluer davantage, maintenir la baseline ou écarter.
9. Consolider la veille M0-M4 et ouvrir son prolongement M4-M8 : réviser les scénarios AI Act sur sources officielles datées, relier chaque décision à une exigence du threat model, de la matrice ou de l'architecture, ajouter l'entrée M4 et le passage de relais vers M5.

## Modalités d'évaluation

Le brief présentiel compte pour 35 % du module. Les dimensions notées au niveau du module sont : C1 jeux, splits, couverture et provenance 20 %, C2 menaces, atténuations et risques résiduels 20 %, C4 comparaison et décision 25 %, reproductibilité des évaluations 20 %, documentation et argumentation 15 %.

Le formateur vérifie :
- La cible métier n'est pas confondue avec la provenance ou la qualité.
- Les splits empêchent une fuite évidente entre fenêtres ou équipements.
- Les baselines sont gelées et comparables.
- Chaque citation se résout vers un document versionné.
- Les refus sont testés, pas seulement prévus.
- L'agent ne peut exécuter qu'une action et ne produit aucun effet externe.
- La veille M4 est datée, fondée sur des sources primaires et traduite en exigences vérifiables.
- Les risques résiduels et les conditions de non-déploiement sont explicites.

Une décision de non-déploiement est recevable et s'évalue comme telle.

## Livrables

- Notebook ou scripts d'évaluation rejouables.
- `docs/protocole_evaluation.md`.
- `docs/benchmark_modele.md`.
- `docs/benchmark_retrieval.md`.
- `docs/threat_model.md`.
- `docs/matrice_decision.md`.
- `docs/model_card.md`.
- Traces structurées de l'agent à une étape.
- Dossier `veille_diagops/` consolidé et passage de relais M5.
- Journal de bord.

## Critères de performance

- La cible métier n'est pas confondue avec la provenance ou la qualité.
- Les splits empêchent une fuite entre fenêtres ou équipements.
- Les baselines sont gelées et comparables.
- Chaque citation se résout vers un document versionné.
- Les refus sont testés.
- L'agent ne peut exécuter qu'une action, sans effet externe.
- La veille M4 est datée et traduite en exigences vérifiables.
- Les risques résiduels et les conditions de non-déploiement sont explicites.

## Hors périmètre

Déploiement de production et monitoring continu, traités en M5 ; outil métier à effet, interdit avant la revue M7 ; boucle agentique ouverte ; multi-agent ; conversion des tables et capteurs en faux documents RAG.
