# Etat du projet DiagOps — fin du module 0

## Resume

DiagOps dispose d'une premiere application fonctionnelle permettant de soumettre un rapport technicien et d'obtenir un diagnostic structure.

## Donnees utilisees

Source utilisee pendant le module :

```text
data_pack/2026-S1/reports/reports.jsonl
```

Aucune autre source du data pack n'est necessaire a ce stade.

## Etat applicatif attendu

Le depot contient :

- une API FastAPI ;
- une route `POST /diagnose` ;
- des schemas Pydantic d'entree et de sortie ;
- une interface Streamlit ou web simple ;
- un client ou wrapper pour le modele sur etagere ;
- des tests API simples ;
- un README complet ;
- des exemples d'entree/sortie.

## Contrat de sortie

La reponse de diagnostic respecte le schema suivant :

```json
{
  "equipment_id": "string|null",
  "symptom": "string",
  "severity": "low|medium|high|critical",
  "failure_hypothesis": "string",
  "recommended_action": "string",
  "confidence": 0.0,
  "evidence": ["string"],
  "requires_human_review": true
}
```

## Choix documentes

Le README indique :

- le modele sur etagere retenu ;
- la raison du choix ;
- les alternatives considerees ;
- les limites observees ;
- la procedure d'installation ;
- les commandes de lancement ;
- les commandes de test.

## Limites connues

A ce stade :

- le modele n'est pas specialise sur les rapports DiagOps ;
- les diagnostics peuvent etre incomplets ou instables ;
- la confiance indiquee reste indicative ;
- la validation humaine reste obligatoire ;
- les donnees capteurs, historiques, feedback et images ne sont pas encore utilisees.

## Entree pour le module 1

Le module 1 repart de cet etat :

- depot applicatif fonctionnel ;
- route `POST /diagnose` disponible ;
- contrat JSON stabilise ;
- exemples de rapports traites ;
- limites du modele sur etagere identifiees.

Le module 1 ajoutera un sous-ensemble annote du data pack pour entrainer un adaptateur LoRA et comparer le modele specialise au modele sur etagere du module 0.

La mission de veille technique et reglementaire ouverte en M0 reste active. Elle est alimentee en M1, M2 et M3, puis consolidee et restituee en M4 afin d'eclairer les choix de modele, de risque et d'architecture.
