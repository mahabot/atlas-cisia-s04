# Brief 1 — Construire et contester l'experience LoRA

**Duree : 7 h en presentiel**

## Mission

L'equipe DiagOps envisage de specialiser `Qwen/Qwen3-0.6B` pour transformer un
rapport technicien en diagnostic JSON. Vous devez etablir si cette adaptation
apporte un benefice mesurable par rapport au modele brut.

Vous travaillez en groupe de deux ou trois sur un depot commun. Le code
repetitif est fourni. Votre responsabilite porte sur le protocole, les
configurations, les mesures, l'analyse et la decision.

## Donnees autorisees

```text
../data_pack/2026-S1/annotations/diagops_train.jsonl
../data_pack/SCHEMA.md
```

Le starter cree un partage stable avec la seed `42` :

- 320 exemples pour l'entrainement ;
- 80 exemples pour la validation.

Le fichier `diagops_test.jsonl` est reserve au Brief 2. Il ne doit etre ni
charge, ni explore, ni utilise pour choisir une configuration pendant ce
brief.

## Systeme compare

- baseline : `Qwen/Qwen3-0.6B` brut, sans adaptateur ;
- candidats : le meme modele avec trois configurations LoRA ;
- generation : meme prompt, meme template de chat et memes parametres ;
- sortie : contrat JSON DiagOps complet ;
- modele : `Qwen/Qwen3-0.6B` ;
- revision Hugging Face :
  `c1899de289a04d12100db370d81485cdf75e47ca`.

## Environnement commun

- Le depot et l'analyse peuvent etre utilises depuis macOS, Linux ou Windows.
- Les runs de reference sont executes sur l'environnement GPU commun.
- Le diagnostic de plateforme doit relever le backend, l'accelerateur, la
  memoire disponible, les versions logicielles et la duree du run.
- Docker n'est pas requis pour l'entrainement.

## Roles tournants

Pour chaque run, attribuez puis faites tourner les roles :

- **pilote experimental** : formule l'hypothese et choisit la variable ;
- **operateur** : controle la configuration, lance le run et conserve les logs ;
- **analyste** : verifie les exports et interprete les resultats.

Chaque apprenant doit etre responsable d'au moins un run ou d'une analyse
identifiable.

## Deroule contraint

| Temps | Travail | Preuve produite |
|---|---|---|
| 00:00–00:45 | Prendre en main le starter, verifier les donnees et l'environnement | `environment.json` + controle des volumes |
| 00:45–01:30 | Formuler les hypotheses et figer le protocole | `protocol_m1.md` versionne |
| 01:30–02:15 | Mesurer la baseline sur les 80 exemples de validation | predictions + metriques baseline |
| 02:15–03:00 | Entrainer et evaluer le LoRA de reference | configuration + logs + metriques |
| 03:00–04:00 | Realiser deux variations controlees | deux configurations + resultats |
| 04:00–05:00 | Comparer les quatre systemes et analyser au moins 12 erreurs | `metrics_m1.csv` + `error_analysis.md` |
| 05:00–05:45 | Revue contradictoire entre groupes | `peer_review.md` |
| 05:45–06:30 | Corriger une faiblesse ou relancer un essai cible | preuve avant/apres |
| 06:30–07:00 | Restituer la decision intermediaire | synthese de 5 minutes + decision versionnee |

Les heures sont consacrees aux preuves. Une attente de GPU ne remplace aucune
activite : pendant un run, le groupe prepare l'analyse, controle les donnees ou
verifie la reproductibilite.

## Configuration de reference

| Parametre | Valeur |
|---|---|
| modele | `Qwen/Qwen3-0.6B` |
| methode | LoRA / PEFT |
| modules | `q_proj`, `k_proj`, `v_proj`, `o_proj` |
| rang | 16 |
| alpha | 32 |
| dropout | 0.05 |
| longueur maximale | 512 |
| batch | 4 |
| accumulation | 4 |
| epochs | 3 |
| learning rate | `2e-4` |
| scheduler | cosine |
| warmup | 0.1 |
| seed | 42 |

Le run de reference doit rester intact. Chaque variation modifie une seule
variable et porte une hypothese ecrite avant l'execution.

## Metriques obligatoires

- JSON brut parseable ;
- conformite au schema apres validation ;
- exactitude `equipment_id` ;
- macro-F1 de `severity` ;
- exactitude de `requires_human_review` ;
- score lexical normalise des champs textuels ;
- latence mediane et p95 ;
- debit ;
- memoire maximale de l'accelerateur ;
- sorties vides ou en erreur.

Une capture d'ecran seule n'est pas une preuve. Les predictions, les metriques,
la configuration et l'environnement doivent etre exportes.

## Revue contradictoire

Le groupe relecteur doit tenter d'invalider au moins un point :

- fuite entre entrainement et validation ;
- prompts ou parametres differents entre les candidats ;
- variable non controlee entre deux runs ;
- metrique mal definie ;
- moyenne masquant une classe faible ;
- mesure de performance non comparable ;
- conclusion non soutenue par les resultats.

L'objection, sa preuve et la reponse apportee sont tracees.

## Livrables

- depot ou notebook reproductible ;
- `environment.json` ;
- `protocol_m1.md` ;
- configurations de la baseline et des trois runs LoRA ;
- predictions et `metrics_m1.csv` ou JSON equivalent ;
- `error_analysis.md` ;
- `peer_review.md` ;
- preuve d'une correction ou d'une relance ;
- decision intermediaire : candidat retenu, rejete ou a reexperimenter.

## Criteres de reussite

- le test final n'a pas ete consulte ;
- les quatre systemes sont compares dans les memes conditions ;
- chaque variation repond a une hypothese formulee a l'avance ;
- au moins 12 erreurs sont classees et interpretees ;
- chaque membre laisse une preuve individuelle ;
- une objection de revue produit une reponse observable ;
- la decision cite des resultats precis, y compris en cas de non-promotion.
