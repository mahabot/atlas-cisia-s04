# Distanciel — Reproduire et contester une experience

**Duree : 3 h**

## Mission

Vous devez reproduire individuellement une experience realisee par un autre
apprenant. Votre travail doit permettre de verifier si le resultat est
reproductible et si la conclusion resiste a une lecture contradictoire.

## Regle

Vous ne modifiez pas la configuration recue avant d'avoir tente sa
reproduction. Vous n'utilisez pas le jeu de test final.

## Deroule

| Temps | Travail | Preuve |
|---|---|---|
| 00:00–00:30 | Recevoir une configuration, verifier les chemins et relever l'environnement | fiche de reprise |
| 00:30–01:15 | Reproduire le run ou son evaluation sur la validation | logs + metriques reproduites |
| 01:15–01:45 | Comparer les resultats avec l'original | tableau des ecarts |
| 01:45–02:15 | Formuler une objection methodologique et chercher sa preuve | objection documentee |
| 02:15–02:45 | Corriger une erreur, une ambiguite ou une faiblesse | commit ou configuration corrigee |
| 02:45–03:00 | Rediger la conclusion individuelle | synthese courte |

## Questions obligatoires

1. La configuration suffit-elle a reproduire le run ?
2. Les versions, la seed et le prompt sont-ils identifies ?
3. Les ecarts observes sont-ils compatibles avec l'aleatoire attendu ?
4. La comparaison avec la baseline est-elle equitable ?
5. Quelle faiblesse pourrait changer la decision ?
6. Quelle correction a ete apportee ?

## Livrable

Remplissez `starter/templates/peer_review.md` et joignez :

- la configuration recue ;
- le diagnostic d'environnement ;
- les metriques originales et reproduites ;
- les ecarts commentes ;
- l'objection ;
- la correction ;
- votre conclusion individuelle.

## Validation

Le travail est valide si :

- la tentative de reproduction est executable ;
- un ecart eventuel est explique, pas masque ;
- l'objection repose sur une preuve ;
- la correction est observable ;
- la conclusion distingue resultat technique et decision de promotion.
