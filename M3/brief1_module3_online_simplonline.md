# M3 - Brief 1 online - Persister les données DiagOps avec SQLAlchemy et Alembic

**Compétences visées**

- C1. Identifier un jeu de données — **niveau 1, imiter** (consolidé)
- C3. Préparer les données — **niveau 2, adapter**

## Description

Les données DiagOps circulent aujourd'hui sous forme de fichiers : chaque module les relit, les contrôle et les recharge. L'arrivée des mesures capteurs rend cette organisation coûteuse — le fichier est volumineux, les jointures sont refaites à chaque exécution et rien ne garantit qu'une même mesure ne soit pas chargée deux fois. Votre mission : modéliser les données DiagOps dans une base relationnelle, y charger les tables déjà préparées, puis faire évoluer le schéma par migration pour accueillir la nouvelle source, sans détruire ce qui existe.

## Ressources

- `data_pack/2026-S1/reference_runs/m2_for_m3/processed/` — tables préparées de référence, chargement initial
- `data_pack/2026-S1/sensors/` — nouvelle source à intégrer par migration
- `data_pack/SCHEMA.md` — entités, champs et identifiants
- `M3/starter/` — modèles, session, migrations et notebook de démonstration
- `M3/RESOURCES.md` — ressources techniques du module

Vos propres tables préparées sont utilisables, à condition d'indiquer lesquelles vous chargez. Le moteur par défaut est SQLite, sans installation ; PostgreSQL est possible, les livrables sont identiques. Le fichier de base de données n'est pas un livrable : il doit pouvoir être reconstruit à partir du code.

## Contexte du projet

Ce brief couvre le socle Atlas du module 3 : choix et documentation du modèle de stockage, modèle relationnel, ORM SQLAlchemy, migrations Alembic et import d'un nouveau jeu de données. Il est autonome et ne dépend pas du brief présentiel, mais il traite la même question par un autre moyen : comment accueillir une nouvelle source sans repartir de zéro — le registre de règles d'un côté, la migration de schéma de l'autre.

Les mesures capteurs sont un cas de stockage discutable : volumétrie élevée, schéma stable, écritures en lot, lectures par plage de temps et par équipement. Une base documentaire, un stockage en fichiers colonnes ou une base orientée séries temporelles sont des alternatives défendables. Les trois tables héritées de M2 ne posent pas la même question : identifiants stables, relations obligatoires, volumétrie faible. Un même projet peut retenir deux modèles pour deux familles de données, à condition de le dire.

## Modalités pédagogiques

Travail individuel, chacun dans son environnement. Durée estimée : 6 heures — 3 h en classe virtuelle et 3 h de travail autonome. La classe virtuelle sert à clarifier le modèle relationnel, vérifier les migrations et comparer les stratégies d'import.

Phases de travail :

1. Justifier le modèle de stockage : comparer au moins deux modèles sur des critères explicites — requêtes attendues, contraintes d'intégrité, volumétrie et croissance, coût d'exploitation — puis justifier celui retenu.
2. Modéliser et créer la base : modèles SQLAlchemy de `equipment`, `events` et `maintenance_history`, types justifiés, clés primaires, clés étrangères et colonnes obligatoires ; création par une première migration Alembic, jamais par création directe des tables.
3. Charger les tables préparées : import respectant l'ordre des clés étrangères, traitement explicite des lignes refusées, comptage des lignes lues, insérées et rejetées avec explication de l'écart.
4. Faire évoluer le schéma : migration ajoutant la table des mesures sans recréer la base, clé logique `equipment_id + timestamp + sensor_name` exprimée par une contrainte d'unicité, clé étrangère vers `equipment` et sort des mesures orphelines, au moins un index justifié par une requête réellement exécutée, `upgrade` et `downgrade` tous deux vérifiés, import de mesures idempotent.
5. Interroger et vérifier : écrire et exécuter cinq requêtes au moins, en SQL ou via l'API SQLAlchemy, et conserver leurs résultats.

## Modalités d'évaluation

Le brief online 1 compte pour 20 % du module. L'évaluation porte sur la réversibilité des migrations et l'idempotence de l'import, pas sur la richesse du modèle.

Le rendu répond à seize questions réparties en cinq blocs : stockage et modèle, chargement, migration, import incrémental, exploitation.

Le formateur vérifie :
- Le choix du modèle de stockage est justifié contre au moins une alternative, sur des critères explicites.
- Le modèle reprend les entités, leurs clés et leurs relations, avec des types justifiés.
- La base est créée et modifiée par migration, jamais par recréation.
- `upgrade` et `downgrade` sont tous les deux exécutables, et ce que `downgrade` détruit est documenté.
- La clé logique des mesures est exprimée par une contrainte, et son effet observé sur une ligne en violation.
- L'import est idempotent et le démontre par deux exécutions successives.
- Les lignes rejetées sont comptées et expliquées.
- L'index ajouté répond à une requête réelle et son effet est observé.

Critères bloquants : base recréée à chaque exécution ou tables créées hors migration ; migration sans `downgrade` exécutable ; import non idempotent présenté comme incrémental ; modèle de stockage retenu sans comparaison ni critère ; clés étrangères absentes ; lignes rejetées silencieusement ; requêtes non exécutables ; conclusion sur l'apport de la base sans mesure.

## Livrables

- La justification du modèle de stockage retenu, comparée à une alternative.
- Le code des modèles et de la session.
- Un fichier de configuration Alembic et un dossier de versions contenant deux migrations : schéma initial, puis ajout des mesures.
- Une contrainte d'unicité et au moins un index explicites.
- Le ou les scripts d'import, dont un import rejouable des mesures.
- Un notebook ou un `README` de démonstration montrant la séquence complète : migration, chargement, migration, import, requêtes.
- Les résultats des cinq requêtes exécutées, sous forme de tableau ou d'export.
- L'entrée M3 du journal de bord.

## Critères de performance

- Le choix du modèle de stockage est justifié contre au moins une alternative.
- Le modèle reprend les entités, leurs clés et leurs relations.
- Les types choisis sont justifiés.
- La base est créée et modifiée par migration.
- `upgrade` et `downgrade` sont tous les deux exécutables.
- La clé logique des mesures est exprimée par une contrainte.
- L'import est idempotent et le démontre.
- Les lignes rejetées sont comptées et expliquées.
- L'index ajouté répond à une requête réelle et son effet est observé.
- Les requêtes répondent aux questions posées et sont reproductibles.
- L'apport et le coût de la base sont discutés avec des éléments concrets.
