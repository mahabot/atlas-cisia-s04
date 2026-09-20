# M0 - Brief 3 - Maintenir la veille technologique et réglementaire de DiagOps

**Compétences visées**

- C2. Identifier les risques éthiques et sociétaux — mobilisée, sans niveau attribué
- C4. Choisir un modèle IA — mobilisée, sans niveau attribué
- C7. Contribuer à l'architecture cible — mobilisée, sans niveau attribué

Les transversales CT4, CT5 et CT6 servent de grille d'observation pédagogique et ne confèrent pas de statut certificatif.

## Description

Vous rejoignez l'équipe DiagOps comme référent de veille. Le projet avance vite, le cadre réglementaire et l'état de l'art bougent pendant la formation, et l'équipe doit décider sur des informations fiables, datées et vérifiables. Votre mission : maintenir de M0 à M4 un dossier de veille qui ne compile pas des liens, mais répond pour chaque information à trois questions — la source est-elle fiable et autoritative, qu'est-ce qui a changé et à quelle date, quelle décision DiagOps faut-il maintenir, évaluer, modifier ou écarter. Ce brief court en parallèle des autres modules et se restitue en M4.

## Ressources

- `M0/brief3_module0_veille_ai_act.md` — énoncé complet de la mission
- `M0/templates/` — gabarits `sources_veille.md`, `journal_veille.md`, `ai_act_diagops.md`, `radar_technologique.md`
- `veille_diagops/` dans votre dépôt — dossier à créer et à tenir de M0 à M4
- `M4/brief3_module4_veille_reglementaire.md` — prolongement par checkpoints jusqu'en M8

Sources officielles de départ : EUR-Lex règlement (UE) 2024/1689, cadre réglementaire de l'IA de la Commission européenne, AI Act Service Desk, CNIL. Un outil d'aide à la qualification peut être utilisé : son résultat n'est ni une source primaire, ni un avis juridique.

## Contexte du projet

La veille est ouverte en M0 et court jusqu'à sa restitution en M4. Ce n'est pas un exercice parallèle : ses conclusions deviennent des exigences pour le choix des modèles, l'analyse des risques et le dossier d'architecture M4, puis sont transmises aux modules de déploiement et d'amélioration continue sous forme de contrôles à implémenter et à mesurer.

L'analyse AI Act porte sur deux scénarios, sans qualification donnée à l'avance. Scénario A, aide au diagnostic : DiagOps formule une recommandation destinée à un technicien, ne contrôle aucun équipement, ne déclenche aucune intervention et impose une revue humaine. Scénario B, fonction liée à la sécurité : DiagOps détecte une situation susceptible de causer un dommage, peut déterminer la nécessité d'une intervention, contribuer à provoquer ou empêcher une action industrielle, et être intégré à un équipement ou une infrastructure sensible.

Le cadre réglementaire évolue pendant la formation. Chaque affirmation porte donc sa date de consultation, la date du texte, son statut — en vigueur, applicable, ligne directrice, projet, consultation ou analyse secondaire — le lien vers la source primaire et les limites de l'interprétation. Le calendrier d'application, y compris l'échéance générale annoncée pour le 2 août 2026, se vérifie sur les sources officielles : une date ne se recopie pas sans vérifier les exceptions.

À partir de M4, la mission se prolonge par un checkpoint d'environ 1 heure inclus dans chaque module jusqu'en M8.

## Modalités pédagogiques

Travail individuel. Durée estimée : 12 heures réparties de M0 à M4, imputées au temps du module 0.

Phases de travail :

1. Initialisation en M0, 4 h : méthode de veille, cartographie et qualification des sources, première entrée du journal.
2. Suivi de M1 à M3, 3 h : une entrée substantielle par module — modèles et licences en M1, données et gouvernance en M2, architectures et dépendances en M3.
3. Consolidation en M4, 3 h : analyse AI Act appliquée à DiagOps et radar technologique.
4. Restitution en fin de M4, 2 h : recommandations intégrées au dossier d'architecture, puis présentation de 10 minutes suivie de questions.

Au moins une entrée du journal doit être révisée avant la fin de M4 à partir d'une source plus récente ou plus autoritative, en expliquant ce qui a changé dans le raisonnement.

## Modalités d'évaluation

L'évaluation porte sur la qualité des sources, la rigueur du raisonnement et l'impact réel sur les décisions DiagOps. Le barème ci-dessous est proposé et doit être confirmé par le formateur avant notation : qualification et diversité des sources 20 %, régularité et qualité du journal 20 %, analyse AI Act 30 %, radar et décisions argumentées 15 %, recommandations d'architecture et restitution 15 %.

Le formateur vérifie :
- Les cinq livrables sont présents et cohérents entre eux.
- Les sources sont diversifiées, datées, qualifiées et majoritairement primaires.
- Le journal comporte au moins quatre entrées substantielles, réparties dans le temps.
- Chaque conclusion réglementaire distingue le fait vérifié, l'hypothèse et l'incertitude.
- Une position initiale a été révisée et la révision est argumentée.
- Les recommandations M4 sont exploitables par les modules suivants.
- La restitution permet de défendre les choix et de répondre aux objections.

Critères éliminatoires proposés : affirmation importante sans source ; confusion non corrigée entre date de publication, entrée en vigueur et date d'application ; source secondaire utilisée comme seule preuve alors qu'une source officielle existe ; qualification juridique catégorique sans hypothèses ni limites ; journal constitué uniquement en fin de parcours ; absence d'impact concret sur une décision DiagOps ; contenu généré ou recopié sans vérification des sources citées.

## Livrables

Le dossier `veille_diagops/` contient cinq fichiers.

- `sources_veille.md` — au moins 15 sources qualifiées, réparties entre textes réglementaires, publications scientifiques, documentation technique primaire, model cards et notes de version, presse spécialisée ; pour chacune : organisme, URL, nature primaire ou secondaire, domaine, fréquence, niveau d'autorité, moyen de suivi, limites et biais possibles.
- `journal_veille.md` — au moins quatre entrées substantielles, datées, citant une source primaire, distinguant le fait de l'interprétation, précisant les incertitudes, formulant un impact sur DiagOps et concluant par `maintenir`, `évaluer`, `modifier` ou `écarter`.
- `ai_act_diagops.md` — analyse des deux scénarios : finalité, acteurs et rôles, supervision humaine, données personnelles, transparence et journalisation, robustesse et cybersécurité, qualification de risque envisagée et hypothèses, obligations possibles, points exigeant une validation juridique.
- `radar_technologique.md` — technologies classées en `adopter`, `évaluer`, `surveiller`, `écarter`, chaque position justifiée par ses sources, ses critères, son impact technique et réglementaire.
- `recommandations_architecture_m4.md` — trois évolutions importantes, une décision confirmée, une décision révisée, un risque réglementaire prioritaire, une recommandation de modèle, une recommandation d'architecture, les métriques à surveiller, les événements à journaliser, les conditions de revue humaine, les seuils d'alerte et les points à valider juridiquement.

Restitution orale de 10 minutes en fin de M4, suivie de questions.

## Critères de performance

- Les cinq livrables sont présents et cohérents entre eux.
- Les sources sont diversifiées, datées et qualifiées.
- Le journal comporte au moins quatre entrées substantielles.
- Chaque conclusion réglementaire distingue les faits, les hypothèses et les incertitudes, et reste conditionnelle.
- Une position initiale a été révisée et la révision est argumentée.
- Le radar conduit à des décisions concrètes, pas à un classement.
- Les recommandations M4 sont exploitables par les modules suivants.
- La restitution permet de défendre les choix et de répondre aux objections.
