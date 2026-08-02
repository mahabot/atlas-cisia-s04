# Brief 2 — Stabiliser et documenter DiagOps

## Mission

Vous reprenez la premiere version de votre application DiagOps.

Votre objectif est de la rendre plus fiable, plus lisible et plus facile a reprendre par un autre membre de l'equipe.

Vous travaillez sur le meme depot et les memes donnees que dans le premier brief.

## Donnees disponibles

Vous utilisez uniquement :

```text
../data_pack/2026-S1/reports/reports.jsonl
```

Vous ne devez pas utiliser les donnees des autres periodes ou des autres sources.

## Travail attendu

Vous devez consolider l'application sur quatre axes :

1. **Robustesse** : gerer les entrees vides, les rapports ambigus et les erreurs du modele.
2. **Validation** : verifier que la sortie respecte le schema attendu.
3. **Evaluation simple** : comparer plusieurs rapports et observer les limites du modele.
4. **Documentation** : expliquer le choix du modele, le lancement, les routes API et les limites.

## Ameliorations minimales

Votre depot doit contenir :

- schemas Pydantic complets ;
- route `POST /diagnose` documentee ;
- interface permettant de tester au moins 3 rapports ;
- gestion propre des erreurs ;
- logs applicatifs simples ;
- tests API avec au moins un cas nominal et un cas d'erreur ;
- README complet.

## Justification du modele

Ajoutez dans le README une section `Choix du modele`.

Elle doit expliquer :

- le modele choisi ;
- pourquoi il convient a ce cas d'usage ;
- ses limites ;
- les alternatives considerees ;
- les conditions d'utilisation eventuelles : licence, taille, dependances, acces API.

## Evaluation attendue

Testez votre application sur au moins 5 rapports.

Pour chaque rapport, notez dans le README ou dans un fichier `evaluation_m0.md` :

- le `report_id` ;
- le symptome extrait ;
- la severite proposee ;
- l'hypothese de panne ;
- une limite observee, si elle existe.

Il ne s'agit pas de prouver que le modele est parfait. Il s'agit de montrer que vous savez l'integrer, observer son comportement et documenter ses limites.

## Livrables

Vous livrez :

- le depot complete ;
- l'API et l'interface ;
- les tests ;
- le README final ;
- un court fichier `evaluation_m0.md` ou une section equivalente dans le README ;
- les commandes permettant de relancer le projet.

## Criteres de reussite

- Le depot est comprehensible sans explication orale.
- L'application fonctionne de bout en bout.
- Les erreurs courantes sont gerees.
- Le contrat JSON est respecte.
- Le modele choisi est justifie.
- Les limites sont explicites.
- Les tests peuvent etre lances par une commande documentee.
