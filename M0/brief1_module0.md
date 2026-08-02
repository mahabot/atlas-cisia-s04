# Brief 1 — Construire la premiere application DiagOps

## Mission

Vous rejoignez l'equipe DiagOps, qui developpe une application d'assistance au diagnostic de maintenance industrielle.

Votre premiere mission est de construire une application simple capable de lire un rapport technicien et de retourner un diagnostic structure.

Vous devez utiliser un modele IA existant, sans entrainement ni fine-tuning.

## Donnees disponibles

Vous utilisez uniquement :

```text
../data_pack/2026-S1/reports/reports.jsonl
```

Les champs et le format des donnees sont decrits dans :

```text
../data_pack/SCHEMA.md
../data_pack/DATA_CARD.md
```

## Fonction attendue

L'application doit permettre de soumettre un rapport technicien, par exemple :

```text
La pompe P-204 vibre fortement depuis deux jours. Temperature anormale et bruit metallique au demarrage.
```

Elle doit retourner une reponse structuree :

```json
{
  "equipment_id": "EQ-0001",
  "symptom": "vibration anormale au demarrage",
  "severity": "high",
  "failure_hypothesis": "roulement use ou desalignement",
  "recommended_action": "planifier une inspection prioritaire du palier",
  "confidence": 0.72,
  "evidence": ["rapport RPT-0001"],
  "requires_human_review": true
}
```

## Contraintes techniques

Votre solution doit contenir :

- une API **FastAPI** ;
- une route `POST /diagnose` ;
- des schemas **Pydantic** pour l'entree et la sortie ;
- une interface **Streamlit** ou une interface web simple ;
- un modele sur etagere issu de HuggingFace ou d'une API compatible ;
- un fichier `README.md`.

Le modele peut etre :

- un modele de classification zero-shot ;
- un modele instruction-following ;
- un modele d'extraction ou de generation structuree ;
- une combinaison simple modele + regles de post-traitement.

Le module ne demande pas d'entrainer un modele.

## Structure de depot attendue

Structure indicative :

```text
diagops-m0/
├── app/
│   ├── main.py
│   ├── schemas.py
│   └── model_client.py
├── ui/
│   └── streamlit_app.py
├── tests/
│   └── test_api.py
├── README.md
└── requirements.txt
```

Vous pouvez adapter cette structure si votre README explique clairement vos choix.

## Etapes de travail

1. Initialiser le depot et l'environnement Python.
2. Lire quelques rapports de `reports.jsonl`.
3. Definir les schemas Pydantic d'entree et de sortie.
4. Integrer un modele sur etagere.
5. Implementer `POST /diagnose`.
6. Ajouter une interface pour tester plusieurs rapports.
7. Documenter l'installation et le lancement.
8. Ajouter au moins un test simple sur l'API.

## Livrables

Vous livrez :

- un depot versionne ;
- une API fonctionnelle ;
- une interface utilisateur ;
- un modele sur etagere integre ;
- un README d'installation et d'utilisation ;
- au moins un exemple d'entree/sortie ;
- au moins un test automatisable.

## Criteres de reussite

- L'application demarre sans modification manuelle du code.
- `POST /diagnose` retourne une reponse JSON exploitable.
- La sortie respecte les champs attendus.
- Le choix du modele est explique simplement.
- L'interface permet a un utilisateur de tester un rapport.
- Le README permet a un autre apprenant de relancer le projet.
