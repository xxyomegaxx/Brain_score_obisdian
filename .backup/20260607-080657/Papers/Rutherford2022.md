---
id: Rutherford2022
titre: "Charting brain growth and aging at high spatial precision"
auteur_principal: "Saige Rutherford"
annee: 2022
journal: "eLife"
doi: "10.7554/eLife.72904"
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
  - "[[Warped BLR]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[UK Biobank]]"
  - "[[ABCD]]"
  - "[[HCP]]"
  - "[[CamCAN]]"
  - "[[ABIDE]]"
application:
  - "[[Vieillissement]]"
  - "[[Neurodéveloppement]]"
  - "[[Schizophrénie]]"
  - "[[Autisme]]"
  - "[[TDAH]]"
niveau_score:
  - "[[Par région]]"
usage_score:
  - "[[Localisation]]"
  - "[[Comparaison de groupes]]"
  - "[[Détection d'atypies]]"
tags_libres: []
fichier_source: "Rutherford et al. eLife 2022;11:e72904"
---
![[Rutherford2022.svg|649]]

## TL;DR
Un modèle normatif de référence du cerveau (épaisseur corticale + volumes sous-corticaux) couvrant la vie entière et 188 régions, qui permet de situer chaque individu par rapport à une grande population et d'obtenir des cartes de déviation utiles en clinique.

## Contributions
1. Modèle de référence lifespan (2–100 ans) sur 58 836 IRM / 82 sites. [Mod. normative]
2. Haute résolution spatiale (188 régions) → empreintes de déviation individuelles. [Biomarqueurs]
3. Les comparaisons cas-témoins sur scores Z surpassent souvent les données brutes (N=1985). [Biomarqueurs]
4. Diffusion libre des modèles pré-entraînés, du code et d'un jeu de transfert vers de nouveaux sites.
5. Variance expliquée jusqu'à 80 % hors-échantillon, validée sur sous-ensemble QC manuel (N=24 354).

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Construit/valide un modèle normatif lifespan. |
| Méthode | Stats classiques | BLR bayésienne avec warping, sans apprentissage profond. |
| Population | Les deux | Cohorte saine + échantillon clinique transdiagnostique. |
| Type IRM | Structurel | Épaisseur corticale + volumes sous-corticaux (T1w). |
| Interprétabilité | Haute | Centiles et Z-scores paramétriques interprétables. |
| Pertinence (1–5) | 5 | Référence fondatrice pour biomarqueurs/brainscore. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : épaisseur corticale et volumes sous-corticaux ; par parcelle de l'atlas Destrieux (188 régions) ; extraites via Freesurfer v6.0.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge, sexe, site (effets fixes) ; niveau sujet ; effet non-linéaire de l'âge modélisé par B-spline cubique à 5 nœuds.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : Warped Bayesian Linear Regression (warping sinarcsinh / SHASH pour la non-gaussianité), implémentée dans PCNtoolkit v0.20 ; un modèle par région ; N=58 836 sur 82 sites (âges 2–100), entraînement/test stratifiés par site ; validation hors-échantillon, rééchantillonnage du test (×10), et sous-ensemble contrôlé manuellement (N=24 354) ; variance expliquée jusqu'à 80 %.

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : Z-score (éq. 2) = (y − ŷ) / √(σ²_d + σ²*_d), combinant erreur de prédiction et incertitude du modèle ; calculé par région et par sujet ; signé (positif = plus épais/grand) ; déviations extrêmes définies par Z>2 (positif) et Z<−2 (négatif).

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : niveau **par région** (188 ROI). Finalités : (a) **localisation** des régions atypiques propres à chaque groupe clinique ; (b) **comparaison de groupes** par tests cas-témoins sur les Z vs données brutes, seuillés à un FDR p<0,05, les effets étant souvent plus forts sur les Z ; (c) **détection d'atypies** par comptage des déviations extrêmes (proportion de sujets déviants par région et par groupe). La stratification et la prédiction d'issues cliniques ne sont évoquées que comme motivation, non réalisées ici.

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : appliqué à un échantillon transdiagnostique (N=1985, 24 sites) couvrant TDAH, autisme (ASD), trouble bipolaire, psychose précoce, dépression (MDD) et schizophrénie ; chaque trouble présente des patterns de déviation distincts ; objectif affiché : aller vers une décision clinique personnalisée. La portée clinique détaillée est annoncée comme traitée séparément.

## Mes réflexions
*(à compléter par moi)*
