# M2 - Brief 1 - Auditer et préparer les données DiagOps

**Compétences visées**

- C1. Identifier un jeu de données — **niveau 1, imiter**
- C2. Identifier les risques éthiques et sociétaux — **niveau 1, imiter**
- C3. Préparer les données — **niveau 1, imiter**

## Description

DiagOps doit intégrer trois nouvelles sources décrivant le parc industriel, les événements et les interventions de maintenance. Ces fichiers peuvent comporter des identifiants dupliqués, des références inexistantes, des dates incohérentes, des valeurs impossibles ou des informations relatives à des personnes dans les notes ; certaines catégories peuvent aussi être trop peu représentées pour permettre une analyse fiable. Votre responsable vous confie cette mission : auditer les données DiagOps, préparer une version exploitable et rendre une décision argumentée avant leur transmission à M3. Ce brief marque le passage d'un projet centré modèle à un projet où la donnée est contrôlée.

## Ressources

- `data_pack/2026-S1/equipment/` — inventaire des équipements
- `data_pack/2026-S1/events/` — événements associés aux équipements
- `data_pack/2026-S1/maintenance/` — historique des interventions
- `data_pack/SCHEMA.md`, `MANIFEST.yaml`, `DATA_CARD.md` — description des données
- `data_pack/2026-S1/reference_runs/m1_for_m2/` — état de référence M1 : prédictions, métriques, matrice d'erreurs
- `M2/starter/` — pipeline de départ, contrats et notebook d'audit
- `M2/RESOURCES.md` — ressources techniques du module

Les données capteurs restent réservées à M3. Les fichiers reçus ne sont jamais modifiés.

## Contexte du projet

Le module 2 ouvre les trois premières tables structurées du corpus DiagOps. Avant d'ouvrir les capteurs en M3, l'équipe doit comprendre ce que contiennent ces fichiers, vérifier leur qualité et décider des traitements nécessaires.

Les relations à examiner sont explicites : `events.equipment_id` et `maintenance_history.equipment_id` renvoient vers `equipment.equipment_id`, et `maintenance_history.event_id` renvoie vers `events.event_id`.

La référence M1 fournie dans le data pack garantit que le travail peut commencer même si vos productions antérieures ne sont pas terminées. Elle sert à rechercher si certaines erreurs historiques semblent plus fréquentes dans certaines catégories : des comptages et des taux simples suffisent, un effectif trop faible se signale et n'autorise aucune conclusion catégorique. M2 statue sur l'état des données, pas sur la promotion du modèle M1.

Le développement est un moyen de rendre le travail vérifiable : la mission ne consiste pas à reproduire une architecture logicielle imposée.

## Modalités pédagogiques

Travail individuel, chacun dans son environnement, avec échanges et revues possibles en séance. Durée estimée : 14 heures — 7 h encadrées et 7 h de prolongement autonome.

La forme est libre : notebook complété par des fonctions Python, scripts organisés en pipeline, ou combinaison des deux ; Pandera, Pydantic ou contrôles Python explicites ; Pytest ou cas de vérification documentés équivalents. Le starter fournit une commande et une structure comme point de départ possible, sans obligation. Quelle que soit la solution, une autre personne doit pouvoir comprendre les règles, rejouer les traitements et retrouver les résultats annoncés.

Phases de travail :

1. Comprendre les données : expliquer ce que représente une ligne dans chaque fichier, identifier colonnes, clés et relations, vérifier la lisibilité des sources, préciser les limites connues.
2. Établir un diagnostic de qualité : colonnes obligatoires et types, identifiants manquants ou dupliqués, références absentes, catégories non prévues, dates incohérentes, valeurs impossibles, valeurs manquantes. Toute règle ajoutée est nommée et justifiée.
3. Examiner les risques et la couverture : rechercher noms, adresses électroniques et numéros de téléphone dans les notes, notamment `work_order_note`, les distinguer des identifiants techniques, puis justifier conservation, masquage ou mise à l'écart ; examiner les effectifs par site, type, criticité et sévérité.
4. Préparer une version exploitable : formaliser les contrôles, appliquer uniquement les corrections justifiables, isoler en quarantaine ce qui nécessite un examen, conserver les fichiers reçus intacts, rendre les traitements rejouables.
5. Rendre une décision : `utilisables`, `utilisables sous conditions` ou `non utilisables en l'état`, en distinguant ce qui a été vérifié, transformé, et ce qui reste incertain.

La quarantaine permet de retrouver au minimum `source_file`, `row_identifier`, `rule_id`, `column`, `observed_value`, `reason` et `decision`.

## Modalités d'évaluation

Le brief présentiel compte pour 70 % du module, le brief online pour 30 %. Les dimensions notées sont : C1 compréhension des données et des relations 20 %, C2 informations personnelles, couverture et risques 20 %, C3 préparation reproductible et vérifications 35 %, reproductibilité et qualité des sorties 15 %, journal de bord et argumentation 10 %.

Le diagnostic doit répondre à dix questions : que représente chaque fichier et comment les sources sont-elles reliées ; les données nécessaires sont-elles présentes et lisibles ; quels problèmes d'identifiants, de doublons ou de relations ; quelles règles métier ne sont pas respectées ; quelles anomalies sont corrigibles de façon certaine ; lesquelles doivent être écartées ou examinées ; les notes contiennent-elles des informations relatives à des personnes et quelle décision ; certaines catégories sont-elles peu représentées ; les erreurs historiques M1 semblent-elles plus fréquentes dans certaines catégories et avec quelles limites ; les données peuvent-elles être transmises à M3 et sous quelles conditions.

Le formateur vérifie :
- Le rôle des sources, des clés et des relations est expliqué.
- Les principaux problèmes de qualité sont recherchés et quantifiés.
- Les fichiers reçus restent inchangés.
- Les corrections sont justifiées et les exclusions traçables.
- Les contrôles et transformations peuvent être rejoués.
- Des cas valides et invalides vérifient les règles importantes.
- Le diagnostic répond aux dix questions et la décision expose ses limites.

Critères bloquants : modification des données reçues ; suppression ou correction silencieuse ; traitements impossibles à rejouer ; rupture de relation non signalée ; quarantaine sans motif compréhensible ; conclusion sur M1 présentée comme une causalité démontrée ; décision finale sans résultat vérifiable.

## Livrables

- Support d'audit présentant observations et résultats : notebook, rapport ou combinaison des deux.
- Contrôles et transformations sous une forme rejouable.
- Cas de vérification valides et invalides.
- Les trois tables préparées.
- Une quarantaine expliquant chaque anomalie écartée ou laissée à examiner.
- Un diagnostic répondant aux dix questions et portant la décision finale.
- L'entrée M2 du journal de bord.

## Critères de performance

- Le rôle des sources, des clés et des relations est expliqué.
- Les principaux problèmes de qualité sont recherchés et quantifiés.
- Les fichiers reçus restent inchangés.
- Les corrections sont justifiées et les exclusions sont traçables.
- Les contrôles et transformations peuvent être rejoués.
- Des cas valides et invalides vérifient les règles importantes.
- Les informations relatives à des personnes et les défauts de couverture sont examinés avec un niveau d'analyse adapté.
- Le diagnostic répond aux dix questions.
- La décision finale s'appuie sur les résultats obtenus et expose ses limites.
