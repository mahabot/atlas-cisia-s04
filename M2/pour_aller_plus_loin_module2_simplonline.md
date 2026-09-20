# M2 - Pour aller plus loin - Industrialiser la qualification des données DiagOps

**Compétences visées**

- C1. Identifier un jeu de données — approfondissement du niveau 1
- C2. Identifier les risques éthiques et sociétaux — approfondissement du niveau 1
- C3. Préparer les données — approfondissement du niveau 1

Complément facultatif : il ne modifie ni la charge obligatoire de M2, fixée à 20 h, ni les acquis attendus pour commencer M3.

## Description

L'audit réalisé en M2 a permis de comprendre et de préparer les premières données DiagOps. Une nouvelle livraison est maintenant disponible, et l'équipe ne veut pas reprendre l'audit à la main à chaque arrivée de fichiers. Votre mission : qualifier cette livraison candidate et transformer votre travail M2 en dispositif réutilisable, puis l'exécuter dans votre dépôt GitHub privé pour que les contrôles ne dépendent plus de votre poste. Le résultat attendu n'est pas une liste d'anomalies trouvées à la main : une autre personne doit pouvoir appliquer le même dispositif à la prochaine livraison.

## Ressources

- `data_pack/2026-S1/` — données M2 publiées
- `data_pack/2026-S1/m2_candidate_release/` — livraison candidate, notes de livraison et empreintes
- Votre audit, vos contrôles et vos décisions du brief présentiel
- `.github/workflows/` de votre dépôt privé — emplacement du workflow à créer
- `M2/RESOURCES.md` — ressources techniques du module

La livraison candidate ne doit pas être fusionnée automatiquement avec les données publiées. Ce complément n'ouvre pas les données capteurs.

## Contexte du projet

La livraison candidate contient des ajouts et des mises à jour. Elle peut aussi présenter des erreurs, des évolutions légitimes de schéma ou des valeurs nécessitant un avis métier : `equipment_update.csv` peut contenir de nouveaux équipements ou des mises à jour d'identifiants existants, `events_batch_02.csv` et `maintenance_batch_02.csv` des lignes à ajouter sans collision d'identifiant, ce dernier annonçant en plus une colonne facultative `source_system`.

La question posée est simple à énoncer et difficile à trancher : cette livraison peut-elle rejoindre le data pack sans dégrader la qualité du socle M2 ?

## Modalités pédagogiques

Travail individuel. Durée estimée : 20 heures — 14 h de qualification et 6 h de laboratoire GitHub Actions.

Phases de travail :

1. Réutilisabilité : vérifier si les contrôles M2 restent valables sur une nouvelle livraison et les rendre indépendants des anomalies déjà observées.
2. Comparaison : confronter le lot candidat aux données déjà publiées et quantifier les écarts.
3. Politique de qualification : distinguer erreurs, avertissements et évolutions acceptables ; définir des règles et des seuils modifiables sans réécrire la solution.
4. Reproductibilité et non-régression : rendre la qualification rejouable et vérifier qu'elle ne casse pas l'acquis M2.
5. Automatisation locale : produire un statut exploitable et un rapport compréhensible en une commande.
6. Laboratoire GitHub Actions : prise en main, application à DiagOps, comportement attendu du workflow, résultats et échecs, démonstration, sécurité minimale.
7. Décision : conclure sur l'intégration, avec conditions et incertitudes restantes.

## Modalités d'évaluation

L'évaluation porte sur la réutilisabilité du dispositif et sur la clarté de la décision, pas sur le nombre d'anomalies détectées. Le complément n'entre pas dans le barème obligatoire du module.

Le formateur vérifie :
- Les contrôles ne sont pas spécifiques aux anomalies déjà observées.
- Les données publiées restent intactes.
- Le lot historique et le lot candidat sont contrôlés avec une politique identifiable.
- Les écarts sont quantifiés et expliqués.
- Erreurs, avertissements et informations sont distingués.
- Les règles et seuils importants peuvent être modifiés sans réécrire la solution.
- Le workflow fonctionne depuis une copie propre du dépôt, sans dépendre de l'environnement local.
- Les résultats locaux et distants sont cohérents, les permissions minimales et aucun secret exposé.

## Livrables

- Les contrôles M2 adaptés à plusieurs livraisons.
- Une politique versionnée des règles et des seuils.
- Des vérifications couvrant les principaux cas de qualification.
- Un rapport comparant la version publiée et le lot candidat.
- Un manifeste d'exécution associant données, règles, résultats et décision.
- La preuve que la qualification peut être relancée automatiquement.
- Une note de décision répondant aux dix questions.
- Une entrée complémentaire dans le journal de bord.

Pour la partie GitHub Actions :

- Le workflow `.github/workflows/data-quality.yml` dans le dépôt privé.
- Une exécution réussie et une exécution démontrant un rejet.
- Un résumé de qualification visible dans GitHub et les rapports détaillés conservés comme artefacts.
- Une pull request interne montrant le résultat des contrôles.
- Les réponses aux questions 11 à 16 dans la note de décision ou le README.

## Critères de performance

- Les contrôles ne sont pas spécifiques aux anomalies déjà observées.
- Les données publiées restent intactes.
- Les deux lots sont contrôlés avec une politique identifiable.
- Les écarts sont quantifiés et expliqués.
- Erreurs, avertissements et informations sont distingués.
- Les règles et seuils peuvent être modifiés sans tout réécrire.
- La qualification produit un statut exploitable et un rapport compréhensible.
- Les résultats sont reproductibles, en local comme dans GitHub Actions.
- La décision finale correspond aux résultats et expose ses conditions.
