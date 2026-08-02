# Workflow Git — dépôt privé apprenant avec `upstream`

## Principe

- **`upstream`** : dépôt pédagogique S04, administré par le formateur et en
  lecture seule pour les apprenants ;
- **`origin`** : dépôt privé indépendant de l'apprenant ;
- **`main`** : branche principale du dépôt privé ; elle reçoit les publications
  de `upstream/main` et contient aussi les productions de l'apprenant ;
- **`work/MN/`** : production du module, suivie par Git dans le dépôt privé.

Le dépôt privé n'est pas un fork GitHub. Il reste donc isolé du réseau de forks
du dépôt pédagogique.

```text
upstream/main  ── publication du formateur ──►  origin/main
                                                   └── work/MN/ de l'apprenant
```

## Première installation

Créer d'abord un dépôt privé vide, sans README ni `.gitignore`, puis exécuter :

```bash
git clone <URL_DU_DEPOT_S04> diagops-s04
cd diagops-s04
git remote rename origin upstream
git remote add origin <URL_DU_DEPOT_PRIVE>
git push -u origin main
```

Vérifier la configuration :

```bash
git remote -v
```

Le résultat doit associer `upstream` au dépôt pédagogique et `origin` au dépôt
privé.

## Ouvrir un module

Sur `main` :

```bash
python tools/init_module.py M2
git add work/M2
git commit -m "Initialiser le travail M2"
git push origin main
```

Le script copie `M2/starter/` vers `work/M2/` et refuse toute réinitialisation
si le dossier existe déjà. Les briefs restent consultables dans `M2/` ; ils ne
sont pas copiés dans l'espace de travail.

## Récupérer une publication du formateur

Commencer avec un espace de travail propre (`git status`). Les modifications en
cours doivent être commitées avant la synchronisation. Puis exécuter :

```bash
git fetch upstream
git merge upstream/main
git push origin main
```

La fusion conserve les commits personnels et ajoute les nouvelles ressources
du formateur. L'option `--ff-only` n'est pas utilisée ici : dès que l'apprenant
a commité son travail, sa branche `main` et `upstream/main` peuvent avoir
divergé normalement.

## Travailler et sauvegarder

```bash
git status
git add work/M2
git commit -m "M2 : ajouter les contrôles de cohérence"
git push origin main
```

Les environnements Python et caches sont ignorés. Les sources, notebooks,
tests, rapports et livrables placés sous `work/` sont, eux, versionnables.

## Règles simples

1. Travailler sur `main` dans le dépôt privé de l'apprenant.
2. Ne jamais pousser vers `upstream`.
3. Ne pas modifier `data_pack/`, les briefs ou les starters de référence.
4. Développer uniquement dans `work/MN/`.
5. Committer avant de synchroniser une nouvelle publication.
6. En cas de conflit, ne rien supprimer : conserver les productions sous
   `work/` et demander de l'aide si la résolution n'est pas évidente.

## Formateur

Le formateur publie uniquement sur le dépôt central :

```bash
python tools/check_publication.py
git status
git add <fichiers publiables>
git commit -m "Publier M3"
git push origin main
git tag s04-m3-start
git push origin s04-m3-start
```

Les corrections et références de continuité ne doivent jamais être commitées
avant leur date d'ouverture, car l'historique Git resterait consultable.
