# Module 0 — Integrer une IA sur etagere dans DiagOps

**Duree** : 17 heures (7 h presentiel + 3 h distanciel + 7 h autonomie)  
**Fil rouge** : DiagOps, plateforme d'assistance au diagnostic de maintenance industrielle  
**Donnees utilisees** : `data_pack/2026-S1/reports/reports.jsonl`

---

## Competence travaillee

| Competence | Intitule | Niveau vise |
|---|---|---|
| **C6** | Implementer un modele d'IA en integrant les briques technologiques dans l'environnement choisi | **Niveau 1** |

## Objectif du module

L'apprenant livre une premiere version fonctionnelle de DiagOps : une application qui prend en entree un rapport technicien et retourne un diagnostic structure.

Le module reste volontairement centre sur l'integration :

- modele IA sur etagere ;
- pas de fine-tuning ;
- API FastAPI ;
- interface Streamlit ou interface web simple ;
- contrat de sortie valide ;
- depot documente et testable.

## Contrat fonctionnel

L'application expose une route `POST /diagnose`.

Entree minimale :

```json
{
  "report_id": "RPT-0001",
  "technician_note": "La pompe P-204 vibre fortement depuis deux jours. Temperature anormale et bruit metallique au demarrage."
}
```

Sortie attendue :

```json
{
  "equipment_id": "EQ-0001",
  "symptom": "vibration anormale au demarrage",
  "severity": "low|medium|high|critical",
  "failure_hypothesis": "hypothese de defaillance",
  "recommended_action": "action recommandee",
  "confidence": 0.72,
  "evidence": ["rapport RPT-0001"],
  "requires_human_review": true
}
```

Le schema de reference est decrit dans `../data_pack/SCHEMA.md`.

## Briefs

### Brief 1 — Construire la premiere application DiagOps

| | |
|---|---|
| **Duree** | 7 h |
| **Objectif** | Integrer un modele sur etagere dans une API et une interface utilisateur |
| **Donnees** | `2026-S1/reports/reports.jsonl` |
| **Livrables** | API, interface, schema Pydantic, README initial |

L'apprenant met en place le depot, lit un rapport technicien, appelle un modele existant et retourne une reponse structuree.

### Brief 2 — Stabiliser, tester et documenter DiagOps

| | |
|---|---|
| **Duree** | 7 h |
| **Objectif** | Consolider la meme application et demontrer qu'elle est reutilisable |
| **Donnees** | memes rapports `2026-S1` |
| **Livrables** | tests, logs, justification du modele, README complet, limites connues |

L'apprenant conserve le meme artefact, ameliore la robustesse, documente les choix et prepare l'etat de projet pour la suite.

### Brief 3 — Mission de veille longitudinale

| | |
|---|---|
| **Duree** | 12 h reparties de M0 a M4, imputees au temps du module 0 |
| **Objectif** | Organiser une veille technique et reglementaire, puis traduire ses conclusions en recommandations pour l'architecture DiagOps |
| **Periode** | Lancement en M0, suivi en M1 a M3, consolidation et restitution en M4 |
| **Livrables** | sources qualifiees, journal, analyse AI Act, radar technologique, recommandations d'architecture M4 |

Cette mission complete les activites de M0 sans modifier les deux briefs deja realises. La veille active se termine en M4 ; ses conclusions deviennent des exigences pour le deploiement et l'amelioration continue.

## Distanciel

Les 3 h de distanciel servent a consolider le depot, corriger les blocages, verifier les livrables et produire l'etat de projet `acquis_m0.md`.

## Evaluation

L'evaluation porte sur la capacite a integrer une brique IA existante dans une application utilisable.

Critiques attendus :

- l'API demarre et repond a `POST /diagnose` ;
- le modele sur etagere est effectivement appele ou encapsule ;
- la sortie respecte le contrat JSON ;
- l'interface permet de soumettre un rapport et de lire le diagnostic ;
- le README permet de relancer le projet ;
- les limites du modele sont identifiees ;
- le depot contient des tests simples et un historique de travail coherent.

## Etat de sortie

A la fin du module, DiagOps dispose d'un premier socle applicatif :

- depot structure ;
- API fonctionnelle ;
- interface utilisateur ;
- modele sur etagere integre ;
- contrat JSON valide ;
- exemples de rapports traites ;
- README et tests initiaux.

Cet etat devient l'entree du module 1, ou le diagnostic sera specialise a partir d'un sous-ensemble annote.

La mission de veille ouverte en M0 se poursuit en parallele jusqu'a sa restitution en M4.
