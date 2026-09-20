# M3 - Brief 2 online - Ce que ce jeu de données permet, et ce qu'il faut fabriquer pour la suite

**Compétences visées**

- C1. Identifier un jeu de données — **niveau 2, adapter** (amorcé)
- C2. Identifier les risques éthiques et sociétaux — **niveau 2, adapter** (consolidé)
- C3. Préparer les données — **niveau 2, adapter** (consolidé)

## Description

À la fin du brief 1, la pipeline DiagOps absorbe quatre sources, trace l'évolution de ses règles et rend une décision de transmission. Cette décision porte sur la qualité des données ; elle ne dit rien de leur capacité. Or M4 va concevoir, et concevoir suppose que les situations à traiter soient présentes, en nombre suffisant, sur un périmètre défendable : trente-six équipements instrumentés sur quatre cent vingt, aucun capteur sur SITE-OUEST, et les événements les plus graves sont les plus rares. Votre mission : établir ce que ce jeu de données ne permet pas, fabriquer ce qui manque en assumant les compromis, détecter le fabriqué dans un lot de contrôle, protéger une publication agrégée, et décider ce qui part en M4. Une pipeline irréprochable peut livrer un jeu de données incapable.

## Ressources

- `data_pack/2026-S1/reference_runs/m2_for_m3/processed/` — tables préparées de référence
- `data_pack/2026-S1/sensors/` — mesures capteurs
- `data_pack/2026-S1/sensors_control/` — lot de contrôle : `control_batch.csv`, `control_sample.csv`, `RELEASE_NOTES.md`, `checksums.sha256`
- `tools/verify_synthetic.py` — détecteur de référence
- `data_pack/SCHEMA.md`, `MANIFEST.yaml`, `DATA_CARD.md`
- `M3/starter/` et `M3/RESOURCES.md`

Votre préparation issue du brief 1 est utilisable, à condition d'indiquer laquelle. Les bibliothèques du `requirements.lock` suffisent.

## Contexte du projet

Ce brief couvre le socle Atlas du module 3 sur les techniques de traitement de données — génération de données synthétiques, confidentialité différentielle, augmentation, segmentation, biais et risques résiduels — et s'en sert pour établir ce qui est transmis à M4.

Trois familles de techniques répondent au manque : augmenter les observations existantes, générer des observations nouvelles, protéger ce qui est publié lorsque les effectifs deviennent trop petits pour rester anonymes. Aucune ne crée d'information : toutes déplacent un compromis.

Deux artefacts remplacent la salle et font office de contradiction. Le détecteur de référence applique les contrôles issus de M2 et M3 à un fichier que vous lui soumettez et retourne des comptages par famille de règle, jamais la liste des lignes signalées ; chaque exécution se consigne au journal avec l'hypothèse qui l'a motivée. Le lot de contrôle contient des mesures dont une partie a été fabriquée, sans colonne de provenance : certaines fabrications sont grossières, d'autres construites pour passer des contrôles semblables aux vôtres. Vos verdicts seront comparés à l'oracle du lot, qui n'est pas distribué.

## Modalités pédagogiques

Travail strictement individuel, en distanciel. Durée estimée : 20 heures. Tous les apprenants reçoivent le même lot de contrôle et le même détecteur : une observation communiquée détruit l'exercice pour celui qui la reçoit. Le temps synchrone est organisé en points individuels portant sur les notions et les difficultés de mise en œuvre, jamais sur les résultats obtenus sur le lot.

Six parties, dans un ordre adaptable. Les parties 3 et 4 se nourrissent l'une l'autre : il est normal de revenir sur le générateur après avoir détecté, et sur les règles après avoir fabriqué.

Phases de travail :

1. Établir ce que le jeu de données ne permet pas : distributions et couverture mesurées avant toute transformation, segmentation exécutée avec son critère de choix.
2. Augmenter des séries existantes : deux techniques appliquées et comparées, chacune décrite par ce qu'elle préserve et par ce qu'elle détruit.
3. Générer des mesures pour un périmètre non couvert : deux méthodes, dont une interpolation entre voisins écrite à la main, avec traitement explicite des catégories.
4. Se confronter : soumettre au détecteur, produire deux états successifs du générateur avec leurs verdicts, puis rendre un verdict par ligne sur `control_batch.csv`, chaque verdict rattaché à une règle nommée.
5. Protéger une publication agrégée : mécanisme de Laplace appliqué avec au moins trois valeurs de `ε`, compromis utilité / protection observé sur des valeurs.
6. Décider ce qui est transmis à M4 : capacité, biais, risques résiduels, conditions, chaque ligne transmise portant sa provenance et son procédé.

## Modalités d'évaluation

Le brief 2 online compte pour 35 % du module. L'évaluation porte sur la lucidité du compromis assumé, pas sur la performance d'un générateur.

Le formateur vérifie :
- L'incapacité du jeu de données est chiffrée avant toute fabrication.
- La segmentation repose sur des variables justifiées et révèle autre chose que les comptages par site.
- Chaque augmentation est décrite par ce qu'elle préserve et par ce qu'elle détruit.
- La comparaison réel / fabriqué porte sur les relations, pas seulement sur les marginales.
- La confrontation au détecteur a produit au moins une correction argumentée, et l'absence de signalement est interprétée, pas revendiquée.
- Chaque verdict est rattaché à une règle nommée, et au moins une détection repose sur une incohérence entre sources.
- Les règles du brief 1 sont réévaluées, y compris celles qui n'ont rien attrapé.
- Le compromis utilité / protection est observé sur des valeurs, avec au moins trois valeurs de `ε`.
- Trois biais sont nommés, rattachés à des comptages, avec atténuation et risque résiduel.
- Toute ligne transmise porte sa provenance et son procédé, et l'ensemble est reproductible à graine fixe.

Critères bloquants : données fabriquées transmises sans provenance ; générateur non reproductible ; technique appliquée sans description de ce qu'elle détruit ; comparaison limitée aux moyennes ; interpolation utilisée comme boîte noire ; verdicts sans règle motivante ; lot classé majoritairement `indécidable` sans démarche ; exécutions du détecteur non consignées ou sans hypothèse ; absence de signalement présentée comme preuve de fidélité ; règle du brief 1 conservée alors que les résultats l'ont invalidée ; `ε` unique présenté comme un choix ; biais cités sans comptage ; décision sans comptage à l'appui ; échange de code, de règles, de verdicts ou d'observations avec un autre apprenant.

## Livrables

- Un notebook exécutable de bout en bout, conclusion intégrée, et son export HTML.
- Le code des générateurs, des augmentations et des règles de détection, rejouable à graine fixe.
- Le tableau de comparaison réel / fabriqué, portant sur les marginales et sur au moins une relation.
- `verdicts_control_batch.csv` : une ligne par mesure, verdict et règle motivante.
- Le registre de règles mis à jour.
- Le jeu transmis à M4, avec sa colonne de provenance et le procédé associé.
- Une note de décision : capacité du jeu, biais, risques résiduels, conditions.
- La description du jeu de données et le cycle de vie mis à jour.
- Le journal de bord, incluant les exécutions du détecteur et leurs hypothèses.

Les fichiers de données générés ne sont pas des livrables : ils doivent pouvoir être reproduits à partir du code.

## Critères de performance

- L'incapacité du jeu de données est chiffrée avant toute fabrication.
- La segmentation est justifiée et révèle autre chose que les comptages par site.
- Chaque augmentation est décrite par ce qu'elle préserve et ce qu'elle détruit.
- L'interpolation entre voisins est écrite, le traitement des catégories est explicite.
- La comparaison réel / fabriqué porte sur les relations.
- La confrontation au détecteur a produit au moins une correction argumentée.
- Chaque verdict de détection est rattaché à une règle nommée.
- Au moins une détection repose sur une incohérence entre sources.
- Les règles du brief 1 sont réévaluées.
- Le compromis utilité / protection est observé sur des valeurs.
- Les biais sont rattachés à des comptages et le risque résiduel est énoncé.
- Toute ligne transmise porte sa provenance et son procédé.
- La décision distingue ce qui est corrigé de ce qui est masqué.
- L'ensemble est reproductible à graine fixe.
