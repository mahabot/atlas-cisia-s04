# Module 1 — Specialiser Qwen3-0.6B et decider de sa mise en service

**Duree : 17 heures — 7 h presentiel + 3 h distanciel + 7 h autonomie**

## Mission

DiagOps dispose d'une premiere application et d'un contrat JSON stable. Le
modele sur etagere utilise en M0 n'est toutefois pas specialise sur les rapports
de maintenance.

Le module 1 consiste a determiner, par l'experience, si un adaptateur LoRA
applique a `Qwen/Qwen3-0.6B` apporte un benefice mesurable. Le but n'est pas de
promouvoir le modele a tout prix. Une decision de non-promotion est recevable
si les mesures la justifient.

## Question directrice

> La specialisation LoRA ameliore-t-elle suffisamment DiagOps pour justifier
> son integration ?

## Competences travaillees

| Competence | Resultat attendu | Niveau vise |
|---|---|---|
| **C5** | Entrainer un modele supervise, comparer plusieurs experiences et verifier la pertinence du resultat | Niveau 1 |
| **C6** | Integrer l'adaptateur retenu dans l'application existante sans rompre le contrat API | Niveau 2 |

La demarche attendue mobilise aussi la recherche methodique, le partage d'une
documentation reproductible et la restitution argumentee des choix.

## Entrees

- l'application DiagOps issue de M0 ;
- le contrat de sortie de `data_pack/SCHEMA.md` ;
- `data_pack/2026-S1/annotations/diagops_train.jsonl` — 400 paires ;
- `data_pack/2026-S1/annotations/diagops_test.jsonl` — 100 paires ;
- la baseline commune `Qwen/Qwen3-0.6B`, sans adaptateur ;
- le starter kit M1.

Les 400 paires sont partagees de facon reproductible en :

- **320 exemples d'entrainement** ;
- **80 exemples de validation**.

Les 100 exemples de test restent fermes pendant le Brief 1. Ils ne sont
consultes qu'une fois, dans le Brief 2, apres le choix du candidat.

## Environnement de travail

Un seul parcours est utilise :

- le depot, les configurations, l'analyse et l'integration sont realises depuis
  le poste local, Mac ou PC ;
- les entrainements de reference sont executes sur l'environnement GPU commun ;
- tous utilisent les memes versions, la meme revision du modele et les memes
  scripts ;
- Docker est utilise pour l'API, pas pour acceder au GPU d'un Mac.

Le starter kit fournit le code repetitif. Chaque apprenant reste responsable de
son hypothese, de sa configuration, de l'execution d'au moins un run, de
l'analyse des resultats et de la decision finale.

## Organisation

### Brief 1 — 7 h presentiel

Construire le protocole, mesurer la baseline sur la validation, entrainer trois
configurations LoRA comparables, analyser les erreurs, faire revoir le
protocole puis iterer.

### Distanciel — 3 h

Reproduire individuellement une experience d'un pair, verifier les preuves,
formuler une objection methodologique et corriger un point du protocole.

### Brief 2 — 7 h autonomie

Geler le candidat, ouvrir le test final, qualifier sa robustesse et son cout,
puis l'integrer dans l'API M0 sans changer `POST /diagnose`.

## Assistance graduee

Tous les apprenants visent les memes resultats et remettent les memes preuves.
Le niveau d'assistance peut varier :

| Parcours d'assistance | Appui disponible |
|---|---|
| **Guide** | notebook sequentiel, commandes pretes, parametres commentes et checklist |
| **Standard** | scripts fonctionnels et configurations a modifier |
| **Approfondissement** | quantification, metriques semantiques ou comparaison d'un backend local |

Les approfondissements ne remplacent aucun livrable obligatoire.

## Preuves individuelles

Chaque apprenant doit pouvoir identifier dans le depot :

- son hypothese ;
- la configuration dont il est responsable ;
- le journal et les resultats de son run ;
- au moins deux erreurs qu'il a analysees ;
- sa reponse a une objection de revue ;
- sa recommandation finale ;
- une preuve de chargement du candidat et de test de `/diagnose`.

## Preuves collectives

- protocole fige avant comparaison ;
- baseline et trois runs LoRA tracables ;
- metriques exportees en CSV ou JSON ;
- matrice d'analyse des erreurs ;
- revue suivie d'une iteration ;
- adaptateur et configuration reproductibles ;
- API DiagOps compatible avec M0 ;
- model card ;
- decision argumentee et restitution courte.

## Critere central

Le module n'est pas valide par la seule existence d'un adaptateur. Il est
valide par la capacite a **configurer, executer, mesurer, comparer, interpreter,
reproduire et arbitrer** sur des preuves auditables.
