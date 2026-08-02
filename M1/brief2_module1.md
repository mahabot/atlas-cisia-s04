# Brief 2 — Qualifier et integrer le candidat DiagOps

**Duree : 7 h en autonomie**

## Mission

Vous reprenez le candidat choisi apres la revue distancielle. Sa configuration
est maintenant gelee. Vous devez ouvrir le jeu de test final, qualifier sa
robustesse et son cout, puis l'integrer a DiagOps sans modifier le contrat
`POST /diagnose`.

Votre decision finale doit etre l'une des suivantes :

- **promouvoir** ;
- **ne pas promouvoir** ;
- **prolonger l'experimentation**, avec une hypothese et une prochaine etape
  precises.

## Entrees

- application et contrat API issus de M0 ;
- baseline commune ;
- candidat et configuration geles ;
- resultats du Brief 1 et de la revue distancielle ;
- `data_pack/2026-S1/annotations/diagops_test.jsonl` — 100 exemples ;
- starter kit M1.

Le test final est consulte une seule fois apres le gel du candidat. Aucun
hyperparametre n'est ajuste a partir de ses resultats.

## Deroule contraint

| Temps | Travail | Preuve produite |
|---|---|---|
| 00:00–00:45 | Reproduire le candidat depuis un environnement propre | hash de configuration + journal de reprise |
| 00:45–01:30 | Executer baseline et candidat sur les 100 tests | predictions et metriques finales gelees |
| 01:30–02:30 | Concevoir 20 perturbations de robustesse motivees | `robustness_cases.jsonl` |
| 02:30–03:30 | Executer la comparaison A/B sur la robustesse | exports complets et comparables |
| 03:30–04:30 | Analyser les resultats par champ, severite et type d'echec | matrice d'erreurs consolidee |
| 04:30–05:15 | Mesurer latence, debit et memoire sur la plateforme commune | rapport de performance |
| 05:15–06:00 | Integrer baseline et LoRA derriere la meme interface | tests de non-regression de `/diagnose` |
| 06:00–07:00 | Rediger la model card et defendre la decision | dossier final + restitution de 8 minutes |

## Suite de robustesse

Les 20 perturbations sont derivees de rapports du test sans modifier leur sens
attendu. Elles couvrent au moins :

- fautes de frappe ou abreviations ;
- ordre des phrases modifie ;
- information secondaire ajoutee ;
- equipement place en fin de rapport ;
- formulation plus courte ;
- symptomes multiples ;
- absence d'identifiant d'equipement ;
- rapport ambigu necessitant une revue humaine.

Pour chaque famille, expliquez sa plausibilite et la facon dont vous avez
verifie la stabilite du sens attendu.

## Seuils de promotion

Le candidat ne peut etre propose a la promotion que s'il satisfait tous les
garde-fous :

- JSON brut parseable : **au moins 95 %** ;
- schema valide apres validation : **100 %** ;
- exactitude `equipment_id` : **au moins 95 %** ;
- macro-F1 `severity` : **au moins 0.80** ;
- exactitude `requires_human_review` : **au moins 95 %** ;
- score lexical moyen des champs textuels : **au moins 0.65** ;
- regression de latence p95 inferieure ou egale a **20 %**, sauf justification ;
- gain de **10 points** sur le score composite face a la baseline, ou autre
  benefice mesurable explicitement defendu.

Ces seuils conditionnent la promotion, pas la reussite du module. Si les
preuves sont insuffisantes, la bonne decision est la non-promotion ou la
prolongation.

## Integration attendue

- meme schema Pydantic qu'en M0 ;
- choix baseline ou LoRA par configuration ;
- aucune modification du contrat public `/diagnose` ;
- adaptateur charge separement du modele de base ;
- erreurs de chargement et d'inference gerees ;
- tests sur baseline et LoRA ;
- procedure locale documentee pour Mac et PC ;
- conteneurisation de l'API reproductible, sans exigence de GPU dans Docker.

## Preuve individuelle

Chaque apprenant remet une fiche courte contenant :

- la configuration qu'il a executee ou reproduite ;
- deux erreurs analysees personnellement ;
- une objection traitee ;
- sa recommandation ;
- une preuve de chargement du candidat et d'appel de `/diagnose`.

Cette fiche est obligatoire meme lorsque le depot applicatif est collectif.

## Livrables

- adaptateur LoRA et configuration PEFT ;
- reference exacte du modele de base et du tokenizer ;
- predictions et metriques finales ;
- `robustness_cases.jsonl` ;
- analyse des erreurs ;
- rapport de performance ;
- application DiagOps mise a jour ;
- tests et commandes de lancement ;
- model card ;
- note de decision ;
- fiche individuelle ;
- restitution de 8 minutes et reponses aux questions.

## Criteres de reussite

- un tiers peut reproduire le candidat sans explication orale ;
- le test final n'a servi a aucun ajustement ;
- la comparaison A/B est equitable et auditable ;
- la robustesse est testee sur des transformations justifiees ;
- les couts operationnels sont mesures ;
- l'API reste compatible avec M0 ;
- la decision respecte les seuils et reconnait les limites ;
- chaque apprenant demontre sa contribution et sa comprehension.
