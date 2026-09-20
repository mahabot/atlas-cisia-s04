# M4 - Brief 3 - Poursuivre la veille réglementaire de DiagOps jusqu'en M8

**Compétences visées**

- C2. Identifier les risques éthiques et sociétaux — contribue au **niveau 3, transposer**
- C7. Contribuer à l'architecture cible — mobilisée, sans niveau attribué

## Description

Le brief de veille ouvert en M0 est consolidé et restitué en M4. Votre mission : prolonger cette veille jusqu'en M8, pour que les décisions prises sur le RAG, le déploiement et l'agent restent compatibles avec l'évolution du cadre réglementaire. Il ne s'agit ni de produire un avis juridique, ni de recopier des textes : à chaque module, vous vérifiez ce qui a changé, vous mesurez l'impact sur DiagOps et vous prenez une décision traçable. Une absence d'évolution est un résultat recevable, à condition que la vérification soit datée.

## Ressources

- `veille_diagops/` dans votre dépôt — dossier longitudinal ouvert en M0
- `M0/brief3_module0_veille_ai_act.md` — mission initiale et gabarits
- `M0/templates/` — gabarits de sources, journal, analyse AI Act et radar
- Livrables du module en cours — registres de risques, ADR, runbooks, gates, traces
- Sources officielles : EUR-Lex, Commission européenne, AI Act Service Desk, CNIL

## Contexte du projet

Le dossier `veille_diagops/` reste la source de référence. Les cinq livrables initiaux sont conservés et mis à jour sans effacer leur historique ni antidater une conclusion ; `synthese_veille_m8.md` est créé en M8.

La progression est fixée module par module. En M5 : le déploiement, les fournisseurs, la journalisation, la rétention et le traitement des incidents créent-ils de nouvelles obligations ou preuves ? En M6 : l'ajout d'outils, de feedback et d'une autonomie bornée modifie-t-il la qualification, la supervision ou les exigences de traçabilité ? En M7 : l'architecture cible, les dépendances, la souveraineté, la réversibilité et l'outil à effet simulé modifient-ils les risques et responsabilités ? En M8 : le nouveau besoin relève-t-il des mêmes hypothèses, et quelles exigences suivre après la formation ?

Une décision réglementaire importante qui n'est reliée à aucun artefact technique ou organisationnel est considérée comme non traitée.

## Modalités pédagogiques

Travail individuel, continu. La consolidation et la restitution M4 sont déjà prévues par le brief M0. De M5 à M8, un checkpoint d'environ 1 heure par module est inclus dans les 14 h du brief présentiel : aucune heure ne s'ajoute au quota de 40 h par module, et le checkpoint réutilise les analyses, registres, ADR, runbooks et preuves déjà produits.

Chaque entrée M4-M8 comporte :

1. La date de consultation et la date du texte ou de la publication.
2. Le statut de la source : texte applicable, ligne directrice, projet, consultation ou analyse secondaire.
3. Au moins une source officielle primaire lorsqu'elle existe.
4. La distinction entre fait vérifié, interprétation et incertitude.
5. Les rôles concernés et l'étape du cycle de vie touchée.
6. L'impact sur les données, le modèle, le RAG, l'agent, l'exploitation ou la supervision humaine.
7. Une décision : `maintenir`, `évaluer`, `modifier` ou `écarter`.
8. Le livrable du module modifié par cette décision, ou la justification datée de l'absence de changement.

Le passage de relais vers le module suivant transmet la dernière entrée datée, les sources ajoutées, retirées ou requalifiées, les décisions confirmées ou révisées, les exigences devenues test, gate, métrique, règle de supervision ou point de validation juridique, ainsi que le responsable et l'échéance des questions ouvertes.

## Modalités d'évaluation

L'évaluation est continue et intégrée à chaque module : le checkpoint de veille fait partie du gate de sortie de M5, M6, M7 et M8.

Le formateur vérifie :
- Une entrée substantielle et datée existe pour chaque module de M4 à M8.
- Chaque entrée s'appuie sur une source primaire lorsqu'elle existe.
- Les changements réglementaires sont distingués des changements techniques.
- Chaque décision produit un impact vérifiable dans un livrable du module, ou une absence d'impact justifiée et sourcée.
- Les passages de relais permettent de reconstituer l'évolution des décisions.
- La synthèse M8 ne formule aucune qualification juridique catégorique sans hypothèses, limites et point de validation compétente.

## Livrables

- `veille_diagops/journal_veille.md` — une entrée datée par module, de M4 à M8.
- `veille_diagops/sources_veille.md` — sources ajoutées, retirées ou requalifiées.
- `veille_diagops/ai_act_diagops.md` — scénarios et rôles révisés à chaque évolution.
- `veille_diagops/radar_technologique.md` — positions mises à jour.
- `veille_diagops/recommandations_architecture_m4.md` — recommandations consolidées en M4.
- Le passage de relais explicite vers le module suivant, avec responsable et échéance.
- `veille_diagops/synthese_veille_m8.md`, créé en M8 : chronologie des évolutions de M0 à M8, hypothèses M4 confirmées, corrigées ou caduques, décisions ayant modifié le RAG, l'agent ou l'architecture, preuves disponibles pour la traçabilité, la supervision, la robustesse et les incidents, écarts restant à traiter, sources à maintenir avec fréquence et responsable, critères imposant une réévaluation après M8.

## Critères de performance

- Une entrée substantielle et datée existe pour chaque module M4-M8.
- Chaque entrée s'appuie sur une source primaire lorsque celle-ci existe.
- Les changements réglementaires sont distingués des changements techniques.
- Chaque décision produit un impact vérifiable ou une absence d'impact justifiée.
- Les passages de relais permettent de reconstituer l'évolution des décisions.
- La synthèse M8 reste conditionnelle et nomme ses points de validation.
