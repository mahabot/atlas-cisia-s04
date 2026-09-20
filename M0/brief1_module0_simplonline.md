# M0 - Brief 1 - Construire la première application DiagOps

**Compétences visées**

- C6. Implémenter le modèle d'IA — **niveau 1, imiter**

## Description

Vous rejoignez l'équipe DiagOps, qui développe une application d'assistance au diagnostic de maintenance industrielle. Les techniciens saisissent chaque jour des rapports en texte libre — une pompe qui vibre, un four qui n'atteint pas sa consigne, un convoyeur qui s'arrête sans alarme — et personne ne transforme aujourd'hui ces textes en information exploitable. Votre mission : construire une application capable de lire un rapport technicien et de retourner un diagnostic structuré, en intégrant un modèle d'IA existant, sans entraînement ni fine-tuning. Ce brief pose le socle applicatif que tous les modules suivants reprendront.

## Ressources

- `data_pack/2026-S1/reports/` — rapports techniciens, seule source ouverte à ce stade
- `data_pack/SCHEMA.md` — champs, types et contrat de sortie DiagOps
- `data_pack/DATA_CARD.md` — origine, usages autorisés et limites du corpus
- `M0/brief1_module0.md` — énoncé complet
- `M0/module_0_synthese.md` — positionnement du module et état de sortie attendu

Les autres périodes et les autres sources du data pack restent fermées. Le data pack ne se copie pas dans le dépôt : il se référence.

## Contexte du projet

DiagOps est le fil rouge de la session : chaque module reprend l'état produit par le précédent. Le module 0 construit la première version fonctionnelle — une application qui prend en entrée un rapport technicien et retourne un diagnostic structuré.

Le module reste volontairement centré sur l'intégration : modèle sur étagère, pas de fine-tuning, API FastAPI, interface Streamlit ou interface web simple, contrat de sortie valide, dépôt documenté et testable.

L'application expose une route `POST /diagnose`. Elle reçoit un `report_id` et un `technician_note`, et retourne le contrat DiagOps : `equipment_id`, `symptom`, `severity`, `failure_hypothesis`, `recommended_action`, `confidence`, `evidence` et `requires_human_review`. Ce contrat n'est pas un détail de format : il sera repris tel quel en M1 lors de la spécialisation du modèle, puis en M4, M5 et M6. Une application qui produit un diagnostic non conforme bloque la suite du parcours.

Le modèle peut être un classifieur zero-shot, un modèle instruction-following, un modèle d'extraction ou de génération structurée, ou une combinaison simple modèle plus règles de post-traitement.

## Modalités pédagogiques

Travail individuel. Durée estimée : 7 heures en présentiel.

Le formateur accompagne sur l'intégration du modèle sur étagère, les schémas Pydantic et le démarrage de l'API. La structure de dépôt proposée dans l'énoncé est indicative : une autre organisation est recevable si le `README.md` explique les choix.

Phases de travail :

1. Initialiser le dépôt et l'environnement Python.
2. Lire quelques rapports de `reports.jsonl` et repérer ce qui est exploitable.
3. Définir les schémas Pydantic d'entrée et de sortie à partir de `SCHEMA.md`.
4. Intégrer un modèle sur étagère, HuggingFace ou API compatible.
5. Implémenter la route `POST /diagnose`.
6. Ajouter une interface Streamlit ou web simple pour tester plusieurs rapports.
7. Documenter l'installation et le lancement dans le `README.md`.
8. Ajouter au moins un test automatisable sur l'API.

## Modalités d'évaluation

L'évaluation porte sur la capacité à intégrer une brique IA existante dans une application utilisable, pas sur la qualité des réponses du modèle sur étagère.

Le formateur vérifie :
- L'application démarre depuis le dépôt, sans modification manuelle du code.
- Le modèle sur étagère est effectivement appelé ou encapsulé.
- La sortie de `POST /diagnose` respecte le contrat JSON de `SCHEMA.md`.
- L'interface permet de soumettre un rapport et de lire le diagnostic.
- Le `README.md` permet à une autre personne de relancer le projet.
- Le dépôt contient au moins un test et un historique de travail cohérent.

## Livrables

- Dépôt versionné contenant l'API, l'interface et les schémas Pydantic.
- API fonctionnelle exposant `POST /diagnose`.
- Interface utilisateur permettant de soumettre un rapport.
- Modèle sur étagère intégré ou encapsulé.
- `README.md` d'installation et d'utilisation, incluant le choix du modèle.
- Au moins un exemple d'entrée et de sortie.
- Au moins un test automatisable et sa commande de lancement.

## Critères de performance

- L'application démarre sans modification manuelle du code.
- `POST /diagnose` retourne une réponse JSON exploitable.
- La sortie respecte tous les champs du contrat DiagOps.
- Le choix du modèle est expliqué simplement.
- L'interface permet à un utilisateur de tester un rapport de bout en bout.
- Le `README.md` permet à un autre apprenant de relancer le projet.
- Le test se lance par une commande documentée.
