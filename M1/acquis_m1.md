# Etat du projet DiagOps — fin du module 1

## Resume

DiagOps dispose d'une baseline commune et d'un cycle d'experimentation
reproductible pour la specialisation LoRA de `Qwen/Qwen3-0.6B`.

La decision retenue est l'une des suivantes :

- **promu** : les garde-fous sont satisfaits ;
- **non promu** : les preuves montrent une regression ou un gain insuffisant ;
- **experimentation a prolonger** : une hypothese et un prochain protocole sont
  explicites.

## Donnees utilisees

```text
data_pack/2026-S1/annotations/diagops_train.jsonl
data_pack/2026-S1/annotations/diagops_test.jsonl
```

Le protocole conserve la separation suivante :

- 320 exemples d'entrainement ;
- 80 exemples de validation ;
- 100 exemples de test final.

## Etat experimental attendu

Le depot contient :

- baseline `Qwen/Qwen3-0.6B` evaluee ;
- run LoRA de reference ;
- deux variations controlees ;
- au moins une iteration issue d'une revue ;
- protocole et hypotheses versionnes ;
- predictions et metriques exportees ;
- analyse des erreurs ;
- suite de robustesse ;
- mesures de latence, debit et memoire ;
- preuve de reproduction distancielle ;
- note de decision.

## Etat modele

Si un candidat est conserve, `model_final/` contient :

- adaptateur LoRA ;
- `adapter_config.json` ;
- tokenizer et chat template utilises ;
- identifiant et revision du modele de base ;
- parametres de generation ;
- model card ;
- resultats d'evaluation ;
- decision de promotion.

Si aucun candidat n'est promu, le depot conserve les memes preuves et un
fichier expliquant pourquoi la baseline reste active.

## Etat applicatif

- `POST /diagnose` conserve le contrat M0 ;
- baseline et LoRA utilisent une interface commune ;
- le fournisseur de modele est choisi par configuration ;
- les erreurs de chargement et d'inference sont gerees ;
- les tests couvrent les deux chemins ;
- le lancement local Mac/PC et le lancement conteneurise de l'API sont
  documentes.

## Contributions individuelles

Pour chaque membre du groupe, le depot identifie :

- une hypothese ou configuration prise en charge ;
- un run execute ou reproduit ;
- deux erreurs analysees ;
- une objection traitee ;
- une recommandation argumentee ;
- un test d'integration effectue.

## Competences transversales acquises

- protocole experimental fige avant observation des resultats ;
- recherche methodique d'une configuration pertinente ;
- comparaison equitable de plusieurs options ;
- reproduction et revue croisee ;
- partage d'une documentation exploitable par un tiers ;
- restitution et defense d'une decision technique.

## Entrees pour le module 2

Le module 2 repart de :

- l'application DiagOps et son contrat stable ;
- la baseline et, s'il est promu, l'adaptateur LoRA ;
- les 40 rapports bruts de M0 et les 500 exemples annotes utilises en M1 ;
- le protocole d'evaluation et la matrice d'erreurs ;
- les limites documentees du corpus et du modele ;
- les artefacts de tracabilite produits en M1.

Le prochain travail portera sur l'audit du corpus, les donnees personnelles,
les biais, la preparation et la version exploitable par la suite du parcours.
