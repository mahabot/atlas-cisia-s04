# M3 - Brief 1 - Étendre la pipeline DiagOps aux mesures capteurs

**Compétences visées**

- C1. Identifier un jeu de données — **niveau 1, imiter** (consolidé sur une source d'un type nouveau)
- C2. Identifier les risques éthiques et sociétaux — **niveau 2, adapter**
- C3. Préparer les données — **niveau 2, adapter**

## Description

Les trois tables ouvertes en M2 décrivent un parc, des événements et des interventions. Elles ne disent rien de ce qui se passe entre deux interventions. L'exploitation ouvre aujourd'hui l'export de sa supervision, `sensor_readings.csv` : une source temporelle volumineuse, sans identifiant de ligne, dont l'horodatage n'est pas homogène, les unités ne sont pas garanties et la couverture est partielle. Votre mission : intégrer cette source à la pipeline DiagOps, la relier aux événements existants, faire évoluer les règles sans casser l'acquis de M2, et décider ce qui peut être transmis à M4. Ce brief marque le passage d'un contrôle table par table à une pipeline multi-source dont l'évolution est tracée.

## Ressources

- `data_pack/2026-S1/sensors/` — mesures capteurs, ouvertes en M3
- `data_pack/2026-S1/equipment/`, `events/`, `maintenance/` — tables reçues en M2
- `data_pack/2026-S1/reference_runs/m2_for_m3/` — état préparé de référence : tables préparées, quarantaine, registre des règles, rapport de validation, décision
- `data_pack/SCHEMA.md`, `MANIFEST.yaml`, `DATA_CARD.md` — description des données
- `M3/starter/` — chargement des quatre sources, utilitaires temporels, registre de règles, quarantaine unifiée
- `M3/RESOURCES.md` — ressources techniques du module

Vous pouvez repartir de votre propre préparation M2 ou de la référence fournie : indiquez laquelle et pourquoi. Les fichiers reçus restent inchangés.

## Contexte du projet

Le fichier reçu ne déclare aucune clé primaire : la clé logique `equipment_id + timestamp + sensor_name` est une hypothèse à vérifier, pas une propriété acquise. Le parc instrumenté est un sous-ensemble du parc décrit par `equipment.csv` : la couverture est partielle par construction.

La pipeline doit désormais porter deux familles de règles, celles héritées de M2 et celles introduites pour le temporel. Les premières ne disparaissent pas : chacune reçoit un statut explicite — conservée, modifiée, étendue ou abandonnée — et la non-régression sur les tables M2 se démontre, elle ne s'affirme pas.

Une mesure et un événement ne partagent aucune clé : seul le couple équipement et temps les rapproche, au moyen d'une fenêtre d'observation que vous choisissez et justifiez.

La volumétrie reste modeste mais approche trente fois celle de la plus grande table de M2 : surveillez le temps d'exécution et signalez ce qui deviendrait impraticable sur un parc entièrement instrumenté ou sur plusieurs périodes.

## Modalités pédagogiques

Travail individuel, chacun dans son environnement, avec échanges et revues possibles en séance. Durée estimée : 14 heures — 7 h encadrées et 7 h de prolongement autonome.

La forme est libre : notebook, scripts en pipeline ou combinaison ; Pandas, Polars, Pandera, Pydantic ou contrôles explicites ; Pytest ou cas documentés équivalents. Le starter est un point de départ possible, non obligatoire.

Phases de travail :

1. Cadrer la source avant de la traiter : grain, clé, séries présentes, période réellement couverte, pas d'échantillonnage observé, volumétrie, conditions d'existence, de livraison et d'accès, et solution de remplacement pour les équipements non couverts.
2. Établir un diagnostic propre au temporel : unicité de la clé logique et distinction doublon strict / doublon de clé, homogénéité d'horodatage et fuseau, alignement sur une grille, continuité et interruptions, cohérence `sensor_name` / `unit` / ordre de grandeur, plages physiques et sentinelles, capteur figé, dérive, saut, mesures orphelines.
3. Distinguer une erreur d'une mesure réelle : pour au moins trois observations atypiques de nature différente, expliquer ce qui fait conclure à une erreur, à une mesure réelle ou à un cas indécidable, en s'appuyant notamment sur `events.csv` et `maintenance_history.csv`.
4. Faire évoluer les règles sans casser l'acquis : statuer chaque règle M2, ajouter les règles capteurs avec identifiant stable, démontrer la non-régression, unifier la quarantaine.
5. Relier les mesures aux événements : fenêtre documentée, contrôle de cardinalité, mesures non appariées, au moins un jeu d'agrégats à un grain défini, et ce que ce grain fait perdre.
6. Documenter le flux de traitement et le cycle de vie du jeu de données, et mettre à jour la description du jeu ; indiquer à qui ces documents s'adressent.
7. Examiner la couverture instrumentale et les risques : traçabilité indirecte de l'activité humaine, règle de conservation proportionnée, périmètre de validité des constats.
8. Rendre une décision : `utilisable`, `utilisable sous conditions` ou `non utilisable en l'état`.

## Modalités d'évaluation

Le brief présentiel compte pour 45 % du module. Les dimensions notées au niveau du module sont : C1 cadrage de la source et couverture 18 %, C2 risques, minimisation et périmètre de validité 18 %, C3 évolution de la pipeline sans rupture 27 %, provenance et capacité du jeu de données 12 %, reproductibilité et qualité des sorties 15 %, journal de bord et argumentation 10 %.

Le diagnostic répond à douze questions, du grain de la source jusqu'au coût de rejeu de la pipeline.

Le formateur vérifie :
- La source est décrite avant d'être traitée : grain, clé, période, pas, séries, volumétrie.
- L'existence, la disponibilité et l'accès sont vérifiés, et l'absence de couverture donne lieu à une solution de remplacement examinée.
- La clé logique est reconstruite et son unicité contrôlée.
- Les défauts temporels sont quantifiés, pas seulement cités.
- Erreurs et mesures réelles sont distinguées avec des arguments.
- Le registre rend visible ce qui vient de M2 et ce qui est nouveau, et la non-régression est démontrée.
- Le rapprochement temporel est explicite : fenêtre, sens, cardinalité, lignes non appariées.
- Le flux et le cycle de vie sont documentés et adressés à un destinataire identifié.
- La couverture instrumentale est chiffrée et son effet sur les conclusions énoncé.

Critères bloquants : modification des données reçues ; suppression ou correction silencieuse, en particulier d'une valeur atypique ; doublon de clé résolu sans arbitrage tracé ; horodatages normalisés sans hypothèse de fuseau ; règle M2 modifiée ou abandonnée sans justification ; rapprochement sans fenêtre ni cardinalité ; conclusion tirée du parc instrumenté présentée comme valable pour tout le parc ; traitements impossibles à rejouer ; décision sans résultat vérifiable.

## Livrables

- Un registre de règles versionné : identifiant, source M2 ou M3, statut, justification.
- La pipeline multi-source sous une forme rejouable.
- La table de mesures préparée.
- Au moins une table d'agrégats et une table de rapprochement mesures ↔ événements, à un grain documenté.
- Une quarantaine unifiée couvrant les quatre sources, au format `source_file`, `row_identifier`, `rule_id`, `column`, `observed_value`, `reason`, `decision`.
- Des cas de vérification valides et invalides, dont au moins un cas temporel et une non-régression sur les tables M2.
- Une documentation du flux de traitement et du cycle de vie, avec la description du jeu mise à jour.
- Un diagnostic répondant aux douze questions et portant la décision finale.
- Une note de couverture et de risques.
- L'entrée M3 du journal de bord.

## Critères de performance

- La nouvelle source est décrite avant d'être traitée.
- La clé logique est reconstruite et son unicité contrôlée.
- Les défauts temporels sont recherchés et quantifiés.
- Erreurs et mesures réelles sont distinguées avec des arguments.
- Le registre de règles rend visible l'héritage M2 et les ajouts M3.
- La non-régression sur les tables M2 est démontrée.
- La quarantaine est unifiée et chaque rejet reste compréhensible.
- Le rapprochement temporel est explicite et contrôlé.
- Le flux et le cycle de vie sont documentés et tenus à jour.
- La couverture instrumentale est chiffrée et ses effets énoncés.
- Les risques liés aux personnes et à la conservation sont traités de manière proportionnée.
- La décision finale s'appuie sur les résultats et expose ses limites.
