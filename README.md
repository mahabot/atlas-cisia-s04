# DiagOps — cursus Atlas/CISIA — session S04

Ce dépôt est la **source pédagogique commune** de la session S04. Le formateur
publie progressivement les briefs, starters, données et références de
continuité sur `main`. Les apprenants le configurent comme remote `upstream`
et conservent leurs productions dans un dépôt privé indépendant (`origin`).

## État du cursus

| Module | État | Supports |
|---|---|---|
| M0 | passé | briefs, synthèse, acquis et modèles |
| M1 | passé | briefs, synthèse, acquis et starter |
| M2 | ouvert | présentiel 14 h, online 6 h, starter et référence de continuité |

Les données distribuées sont centralisées dans [`data_pack/`](data_pack/).
Un module peut les utiliser, mais ne doit pas en conserver de copie.

## Organisation du dépôt

```text
S04/
├── M0/ ... M8/          # supports publiés progressivement
├── data_pack/           # source unique des données apprenant
├── tools/               # initialisation et contrôle de publication
├── work/                # productions propres à l'apprenant
├── GIT_WORKFLOW.md      # configuration origin/upstream
└── _conception/         # local et ignoré, jamais publié
```

Le dépôt pédagogique ne publie aucun travail dans `work/MN/`. Chaque apprenant
peut donc y versionner sa production sans conflit avec les mises à jour de
`upstream/main`.

## Démarrer M2

Après avoir configuré les remotes comme indiqué dans
[`GIT_WORKFLOW.md`](GIT_WORKFLOW.md) :

```bash
python tools/init_module.py M2
cd work/M2
python -m venv .venv
```

Le script refuse d'écraser un dossier existant. Les notebooks et utilitaires
retrouvent automatiquement les données sous `data_pack/2026-S1/`.

## Règles de publication

- dans le dépôt pédagogique, `upstream/main` contient uniquement le matériel
  distribué aux apprenants ; dans chaque dépôt privé, `origin/main` contient
  aussi les productions placées sous `work/` ;
- `_conception/`, les environnements, checkpoints et runs locaux sont exclus ;
- les données d'un module futur ne sont ajoutées qu'au moment de son ouverture ;
- avant toute publication, exécuter :

```bash
python tools/check_publication.py
```

Ce contrôle inspecte les fichiers suivis ou candidats au commit et bloque les
contenus privés, les copies de données par module et les fichiers trop lourds.
