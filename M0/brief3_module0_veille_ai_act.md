# Brief 3 — Maintenir la veille technologique et reglementaire de DiagOps

## Mission

Vous rejoignez l'equipe DiagOps comme referent de veille.

Votre mission est de maintenir, de M0 a M4, un dossier permettant a l'equipe de prendre des decisions techniques et reglementaires a partir de sources fiables, datees et verifiables.

Le travail ne consiste pas a compiler des liens. Pour chaque information retenue, vous devez repondre a trois questions :

1. La source est-elle suffisamment fiable et autoritative ?
2. Qu'est-ce qui a reellement change, et a quelle date ?
3. Quelle decision DiagOps faut-il maintenir, evaluer, modifier ou ecarter ?

La veille active se termine en M4. Ses conclusions alimentent le choix des modeles, l'analyse des risques et le dossier d'architecture de DiagOps.

## Duree et calendrier

Cette mission represente **12 heures**, reparties sur M0 a M4.

| Phase | Periode | Duree | Production attendue |
|---|---|---:|---|
| Initialisation | M0 | 4 h | methode de veille, cartographie et qualification des sources, premiere entree du journal |
| Suivi | M1 a M3 | 3 h | une entree substantielle par module |
| Consolidation | M4 | 3 h | analyse AI Act appliquee a DiagOps et radar technologique |
| Restitution | fin M4 | 2 h | recommandations integrees au dossier d'architecture M4 |
| **Total** | M0 a M4 | **12 h** | dossier de veille complet et exploitable |

## Organisation du dossier

Creez le dossier suivant dans votre depot DiagOps :

```text
veille_diagops/
├── sources_veille.md
├── journal_veille.md
├── ai_act_diagops.md
├── radar_technologique.md
└── recommandations_architecture_m4.md
```

Les quatre gabarits fournis dans `templates/` peuvent etre copies dans ce dossier. Le fichier `recommandations_architecture_m4.md` est construit en M4 a partir de vos quatre autres livrables et du dossier d'architecture du module.

## Livrable 1 — Cartographie des sources

Le fichier `sources_veille.md` contient au moins **15 sources qualifiees**, reparties entre :

- textes reglementaires et autorites publiques ;
- publications scientifiques et actes de conferences ;
- documentation technique primaire ;
- model cards, depots et notes de version des fournisseurs ;
- presse specialisee et analyses secondaires.

Pour chaque source, documentez :

- l'organisme ou l'auteur ;
- l'URL ;
- la nature primaire ou secondaire ;
- le domaine couvert ;
- la frequence de publication ;
- le niveau d'autorite ;
- le moyen de suivi : RSS, newsletter, depot, alerte ou consultation periodique ;
- les limites, interets commerciaux ou biais possibles.

Une source secondaire ne remplace pas une source primaire lorsqu'un texte officiel, une documentation originale ou une publication scientifique est disponible.

## Livrable 2 — Journal de veille

Le fichier `journal_veille.md` contient au moins **quatre entrees substantielles** :

- une entree initiale en M0 ;
- une entree en M1 sur les modeles, licences, techniques d'adaptation ou contraintes de calcul ;
- une entree en M2 sur les donnees, la conformite, les biais ou la gouvernance ;
- une entree en M3 sur les architectures, l'integration multi-source ou les dependances.

Chaque entree doit :

- etre datee ;
- citer au moins une source primaire ;
- distinguer le fait verifie de votre interpretation ;
- preciser les incertitudes ;
- formuler un impact possible sur DiagOps ;
- aboutir a une decision : `maintenir`, `evaluer`, `modifier` ou `ecarter`.

Au moins une entree doit etre revisee avant la fin de M4 a partir d'une source plus recente ou plus autoritative. La revision doit expliquer ce qui a change dans votre raisonnement.

## Livrable 3 — Analyse AI Act appliquee a DiagOps

Le fichier `ai_act_diagops.md` analyse deux scenarios. Aucune qualification juridique n'est donnee a l'avance.

### Scenario A — Aide au diagnostic

DiagOps :

- formule une recommandation a destination d'un technicien ;
- ne controle pas directement un equipement ;
- ne declenche pas automatiquement une intervention ;
- impose une revue humaine avant toute decision.

### Scenario B — Fonction liee a la securite

DiagOps :

- detecte une situation susceptible de causer un dommage ;
- peut determiner la necessite d'une intervention ;
- peut contribuer a provoquer ou empecher une action industrielle ;
- peut etre integre a un equipement, un produit ou une infrastructure sensible.

Pour chaque scenario, analysez :

- la finalite prevue du systeme ;
- les acteurs et leurs roles : fournisseur, deployeur, fournisseur du modele amont ;
- la place de la supervision humaine ;
- les donnees personnelles eventuellement traitees ;
- les besoins de transparence, de tracabilite et de journalisation ;
- la robustesse et la cybersecurite attendues ;
- la qualification de risque envisagee et les hypotheses qui la conditionnent ;
- les obligations possibles ;
- les points qui exigent une validation juridique.

Votre conclusion doit rester conditionnelle : elle decrit une analyse de formation, pas un avis juridique.

## Temporalite reglementaire

Le cadre reglementaire evolue pendant la formation. Chaque affirmation concernant l'AI Act doit donc comporter :

- la date de consultation ;
- la date du texte ou de la publication ;
- son statut : `en vigueur`, `applicable`, `ligne directrice`, `projet`, `consultation` ou `analyse secondaire` ;
- le lien vers la source primaire ;
- les limites de votre interpretation.

Au demarrage de la mission, verifiez notamment sur les sources officielles le calendrier d'application du reglement, y compris l'echeance generale annoncee pour le **2 aout 2026** et les dispositions deja applicables. Ne recopiez pas une date sans verifier les exceptions et les calendriers specifiques.

Sources officielles de depart :

- [EUR-Lex — Reglement (UE) 2024/1689](https://eur-lex.europa.eu/eli/reg/2024/1689/oj/fra)
- [Commission europeenne — Cadre reglementaire de l'IA](https://digital-strategy.ec.europa.eu/fr/policies/regulatory-framework-ai)
- [AI Act Service Desk](https://ai-act-service-desk.ec.europa.eu/)
- [CNIL — Intelligence artificielle](https://www.cnil.fr/fr/intelligence-artificielle)

Vous pouvez utiliser un outil d'aide a la qualification, mais son resultat ne constitue ni une source primaire ni un avis juridique.

## Livrable 4 — Radar technologique

Le fichier `radar_technologique.md` classe les technologies et pratiques observees dans quatre categories :

| Categorie | Sens pour DiagOps |
|---|---|
| **Adopter** | suffisamment stable, utile et compatible avec les contraintes du projet |
| **Evaluer** | merite un prototype, un benchmark ou une etude complementaire |
| **Surveiller** | prometteur mais encore incertain, immature ou mal documente |
| **Ecarter** | inadapte au besoin, au risque, au cout ou a l'architecture retenue |

Chaque position du radar doit etre justifiee par :

- les sources utilisees ;
- les criteres de decision ;
- l'impact technique ;
- l'impact reglementaire eventuel ;
- la recommandation pour DiagOps.

## Livrable 5 — Recommandations d'architecture M4

Le fichier `recommandations_architecture_m4.md` transforme la veille en decisions exploitables.

Il doit contenir au minimum :

- trois evolutions importantes observees ;
- une decision DiagOps confirmee ;
- une decision DiagOps revisee ;
- un risque reglementaire prioritaire ;
- une recommandation sur le choix de modele ;
- une recommandation d'architecture ;
- les metriques a surveiller en production ;
- les evenements a journaliser ;
- les conditions de revue humaine ;
- les seuils ou situations d'alerte ;
- les points qui necessitent une validation juridique.

Ces recommandations sont reprises dans le dossier d'architecture M4, puis transmises aux modules suivants comme exigences a implementer et a mesurer.

## Competences mobilisees

| Competence | Preuve attendue |
|---|---|
| **C2** | analyse des risques, du cadre reglementaire et de la supervision humaine |
| **C4** | recherche, comparaison et justification des choix de modele ou de technologie |
| **C7** | traduction des conclusions en contraintes et decisions d'architecture |
| **CT4** | recherche methodique de pistes et verification des sources |
| **CT5** | documentation partageable des resultats et des decisions |
| **CT6** | restitution synthetique et defense des choix devant le commanditaire |

Le mapping CT4, CT5 et CT6 est utilise comme grille d'observation pedagogique. Sa source et ses modalites d'evaluation restent a documenter ; leur observation dans cette mission ne leur attribue pas, a elle seule, un statut certificatif distinct.

## Restitution finale

En fin de M4, vous presentez en **10 minutes** :

1. l'evolution la plus importante observee ;
2. une hypothese initiale corrigee par la veille ;
3. votre qualification conditionnelle des deux scenarios AI Act ;
4. une decision technique ou architecturale pour DiagOps ;
5. les exigences a transmettre a l'equipe de deploiement et d'amelioration continue.

La restitution est suivie de questions permettant de verifier la qualite des sources, le raisonnement et la defense des choix.

## Evaluation — proposition a valider

Le bareme ci-dessous est propose pour l'evaluation de la mission. Il doit etre confirme par le formateur avant notation.

| Dimension | Poids propose |
|---|---:|
| Qualification et diversite des sources | 20 % |
| Regularite et qualite du journal | 20 % |
| Analyse AI Act appliquee a DiagOps | 30 % |
| Radar et decisions argumentees | 15 % |
| Recommandations d'architecture et restitution | 15 % |

### Criteres eliminatoires proposes

- affirmation importante sans source ;
- confusion non corrigee entre date de publication, entree en vigueur et date d'application ;
- source secondaire utilisee comme seule preuve alors qu'une source officielle existe ;
- qualification juridique categorique sans hypotheses ni limites ;
- journal constitue uniquement en fin de parcours ;
- absence d'impact concret sur une decision DiagOps ;
- contenu genere ou recopie sans verification des sources citees.

## Criteres de reussite

- Les cinq livrables sont presents et coherents entre eux.
- Les sources sont diversifiees, datees et qualifiees.
- Le journal comporte au moins quatre entrees substantielles.
- Chaque conclusion reglementaire distingue les faits, les hypotheses et les incertitudes.
- Une position initiale a ete revisee et la revision est argumentee.
- Le radar conduit a des decisions concretes.
- Les recommandations M4 sont exploitables par les modules suivants.
- La restitution permet de defendre les choix et de repondre aux objections.
