---
id: Bethlehem2020
titre: A normative modelling approach reveals age-atypical cortical thickness in a subgroup of males with autism spectrum disorder
auteur_principal: Bethlehem
annee: 2020
journal: Communications Biology
doi: 10.1038/s42003-020-01212-9
date_ajout: 2026-06-03
statut: lu
theme:
  - "[[Mod. normative]]"
  - "[[Biomarqueurs]]"
methode_cat:
  - "[[Stats classiques]]"
population:
  - "[[Les deux]]"
type_irm:
  - "[[Structurel]]"
interpretabilite: "[[Haute]]"
pertinence: 5
methode_detail:
  - "[[LOESS]]"
  - "[[Centiles]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[ABIDE]]"
application:
  - "[[Autisme]]"
niveau_score:
  - "[[Par région]]"
  - "[[Global par sujet]]"
usage_score:
  - "[[Localisation]]"
  - "[[Comparaison de groupes]]"
  - "[[Détection d'atypies]]"
  - "[[Association au phénotype]]"
tags_libres: []
fichier_source: 
---
![[Bethlehem2020.png]]
## TL;DR
La modélisation normative liée à l'âge révèle que les faibles différences cas-témoins d'épaisseur corticale en autisme sont surtout portées par un petit sous-groupe d'individus très atypiques pour leur âge — déplaçant l'inférence du niveau groupe vers le niveau individuel.

## Contributions
1. Convertit l'épaisseur corticale en w-score individuel d'atypicité par rapport aux normes TD liées à l'âge. [Mod. normative]
2. Les petites différences cas-témoins de CT sont surtout dues à un petit sous-groupe très atypique, non à un effet moyen généralisé. [Biomarqueurs]
3. Isole ce sous-groupe : ~7,6 % de sujets atypiques par région (médiane), concentrés entre 6 et 20 ans. [Scores-méd. personnalisée]
4. w-scores corrélés au phénotype (SRS, ADOS) dans des régions distinctes de l'analyse cas-témoins. [Biomarqueurs]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Construit et applique un modèle normatif d'âge sur la CT. |
| Méthode | Stats classiques | LOESS, modèles mixtes, z-scores ; pas de ML. |
| Population | Les deux | Normes sur TD, atypies évaluées chez ASD. |
| Type IRM | Structurel | Épaisseur corticale (sMRI). |
| Interprétabilité | Haute | w-score = z-score simple, directement lisible. |
| Pertinence (1–5) | 5 | Cœur du projet (normatif + scores de déviation, sMRI). |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : épaisseur corticale (CT) ; par région sur 308 parcelles (~500 mm²) ; échantillon final n=699 ASD et n=624 TD (n=870/groupe avant sélection). Volume, surface area et gyrification traités en supplémentaire.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge (5–40 ans), modélisé de façon non-linéaire par LOESS ; sexe géré en restreignant aux hommes ; site, mouvement (déplacement cadre-à-cadre) et indice d'Euler inclus comme covariables dans l'analyse cas-témoins.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : LOESS (régression polynomiale locale) avec largeur de noyau optimisée par la méthode de Brent (5–100 % de la plage d'âge) ; norme estimée par bin d'âge d'un an, par région et par sexe, à partir du groupe TD masculin ; validation par bootstrap (1000 rééchantillonnages) et par scoring en centiles (PyNM) — forte cohérence des sorties.

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : w-score = (CT_région − μ_norm) / σ_norm, analogue à un z-score, calculé par région et par individu ; signé (déviations positives et négatives) ; seuil d'atypicité |w| > 2 SD (hors bornes de confiance à 95 %). Un ratio global gW = Σ|w>2| / Σ|w<2| (seuil >0,5) identifie les sujets globalement atypiques.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : **Par région** → localisation (cartes de prévalence, ~7,6 % de sujets atypiques par région en médiane), comparaison de groupes (cartes w testées contre 0, FDR — aucune région significative ; nettoyage des effets cas-témoins par retrait des outliers), détection d'atypies (outliers >2 SD), association au phénotype (Spearman entre w et ADOS / SRS). **Global par sujet** → détection d'atypies (n=14 sujets à cortex globalement plus mince, probablement artefact de qualité d'image).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : identification d'un sous-groupe ASD à CT âge-atypique (surtout 6–20 ans, prévalence décroissante après 20 ans) ; topographies w–symptômes distinctes (SRS en frontal/pariétal latéral, ADOS en temporal latéral/inférieur) ; piste vers une médecine de précision et des mécanismes biologiques fortement pénétrants, comme alternative aux analyses cas-témoins.

## Mes réflexions
*(à compléter par moi)*
