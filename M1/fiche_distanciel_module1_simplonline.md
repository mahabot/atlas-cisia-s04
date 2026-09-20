# M1 - Distanciel - Reproduire et contester une expérience

**Compétences visées**

- C5. Entraîner le modèle d'IA — mobilisée en reproduction, sans niveau distinct

## Description

Un résultat qui ne se reproduit pas n'est pas un résultat. Vous recevez la configuration d'une expérience réalisée par un autre apprenant. Votre mission : établir si elle est reproductible et si sa conclusion résiste à une lecture contradictoire, puis formuler une objection méthodologique appuyée sur une preuve. Vous ne modifiez pas la configuration reçue avant d'avoir tenté sa reproduction : corriger avant de reproduire supprime la preuve recherchée.

## Ressources

- Configuration et preuves reçues d'un pair — objet de la reproduction
- `M1/starter/` — même environnement d'exécution et d'évaluation
- `M1/starter/templates/peer_review.md` — gabarit de la revue à remettre
- `data_pack/2026-S1/annotations/diagops_train.jsonl` — partage 320 / 80, validation uniquement

Le jeu de test final n'est pas utilisé.

## Contexte du projet

Le distanciel s'intercale entre le brief 1, qui produit des candidats et une décision intermédiaire, et le brief 2, qui gèle un candidat et ouvre le test final. Ce que vous validez ou invalidez ici conditionne le candidat qui sera qualifié en brief 2.

Six questions structurent le travail : la configuration suffit-elle à reproduire le run, les versions, la seed et le prompt sont-ils identifiés, les écarts observés sont-ils compatibles avec l'aléatoire attendu, la comparaison avec la baseline est-elle équitable, quelle faiblesse pourrait changer la décision, quelle correction a été apportée.

## Modalités pédagogiques

Travail strictement individuel, à distance. Durée estimée : 3 heures.

Phases de travail :

1. 00:00–00:30 — Recevoir une configuration, vérifier les chemins et relever l'environnement.
2. 00:30–01:15 — Reproduire le run ou son évaluation sur la validation.
3. 01:15–01:45 — Comparer les résultats avec l'original et produire le tableau des écarts.
4. 01:45–02:15 — Formuler une objection méthodologique et chercher sa preuve.
5. 02:15–02:45 — Corriger une erreur, une ambiguïté ou une faiblesse.
6. 02:45–03:00 — Rédiger la conclusion individuelle.

## Modalités d'évaluation

L'évaluation porte sur la tentative de reproduction et sur la qualité de l'objection. Un écart non reproduit n'est pas disqualifiant ; un écart masqué l'est.

Le formateur vérifie :
- La tentative de reproduction est exécutable.
- Un écart éventuel est expliqué, pas masqué.
- L'objection repose sur une preuve, pas sur une impression.
- La correction est observable dans un commit ou une configuration corrigée.
- La conclusion distingue le résultat technique de la décision de promotion.

## Livrables

`starter/templates/peer_review.md` complété, accompagné de :

- La configuration reçue.
- Le diagnostic d'environnement.
- Les métriques originales et les métriques reproduites.
- Le tableau des écarts, commentés.
- L'objection méthodologique et sa preuve.
- La correction apportée, sous forme de commit ou de configuration corrigée.
- La conclusion individuelle.

## Critères de performance

- La tentative de reproduction est exécutable.
- Un écart éventuel est expliqué, pas masqué.
- L'objection repose sur une preuve.
- La correction est observable.
- La conclusion distingue résultat technique et décision de promotion.
