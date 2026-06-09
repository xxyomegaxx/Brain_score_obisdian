---
id: Fraza2021
titre: Warped Bayesian Linear Regression for Normative Modelling of Big Data
auteur_principal: Charlotte J. Fraza
annee: 2021
journal: NeuroImage
doi: 10.1101/2021.04.05.438429
date_ajout: 2026-06-03
statut: lu
theme:
  - "[[Mod. normative]]"
  - "[[Biomarqueurs]]"
  - "[[Scores-méd. personnalisée]]"
methode_cat:
  - "[[Hybride]]"
population:
  - "[[Saine]]"
type_irm:
  - "[[Structurel]]"
  - "[[Fonctionnel]]"
  - "[[Diffusion]]"
interpretabilite: "[[Haute]]"
pertinence: 5
methode_detail:
  - "[[Warped BLR]]"
  - "[[BLR]]"
  - "[[GPR]]"
modalite_detail:
  - "[[sMRI]]"
  - "[[dMRI]]"
  - "[[fMRI]]"
dataset:
  - "[[UK Biobank]]"
application:
  - "[[Vieillissement]]"
niveau_score:
  - "[[Par région]]"
  - "[[Global par sujet]]"
usage_score:
  - "[[Association au phénotype]]"
  - "[[Comparaison de groupes]]"
  - "[[Détection d'atypies]]"
tags_libres: []
fichier_source: 
---
![[Fraza2021.png]]
## TL;DR
Remplacer le processus gaussien par une régression linéaire bayésienne « warpée » (SinhArcsinh) permet de faire de la modélisation normative sur des dizaines de milliers de sujets tout en estimant correctement les centiles non-gaussiens — clé pour des scores de déviation fiables aux extrêmes.

## Contributions
1. Cadre normatif scalable au big data : BLR (B-splines) au lieu du GPR. [Mod. normative]
2. Warping de la vraisemblance pour modéliser le non-gaussien et les centiles extrêmes. [Mod. normative]
3. Démonstration multimodale sur UK Biobank (IDPs, WMH, DTI voxel-wise). [Biomarqueurs]
4. Z-scores de déviation corrélés aux phénotypes cognitifs et au facteur g. [Scores-méd. personnalisée]
5. Sélection de modèle en forme close (BIC via vraisemblance marginale), sans validation croisée.

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Nouveau cadre normatif (warped BLR) pour grandes cohortes. |
| Méthode | Hybride | Régression B-splines + inférence bayésienne / warping appris. |
| Population | Saine | UK Biobank 40–80 ans, vieillissement normal. |
| Type IRM | Structurel · Fonctionnel · Diffusion | IDPs des trois modalités ; WMH et FA/MD détaillés. |
| Interprétabilité | Haute | Modèle paramétrique, vraisemblance marginale explicite. |
| Pertinence (1–5) | 5 | Méthode fondatrice scalable pour brainscore/biomarqueurs. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : 819 IDPs UK Biobank + 150 mesures FreeSurfer ; FA et MD voxel-wise (cerveau entier, analyse TBSS) ; niveau par IDP/région et par voxel ; ~10 000 sujets (release 2017) + ~5 000 longitudinaux (release 2020), ~47 % d'hommes, 40–80 ans ; ~10 000 sujets dMRI après QC.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge, sexe (binaire), site (codé en dummy) ; expansion B-spline cubique sur l'âge (3 nœuds dans les expériences IDP ; méthodo décrit aussi 5 nœuds régulièrement espacés).

## Étape 2 — Modélisation normative
Méthode · granularité · validation : Warped BLR avec warping SinhArcsinh (affine et Box-Cox aussi testés, SinhArcsinh retenu), comparée à BLR standard, B-spline BLR et GPR ; bruit de précision par site, intercepts par site ; hyper-paramètres par empirical Bayes (Type II ML) optimisés par la méthode de Powell ; modèle univarié par IDP/voxel ; split 50/50 train/test pour les IDPs, 80/20 pour le DTI cerveau entier ; sélection par EV, MSLL et BIC (pas de validation croisée).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : Z-score = (y − ŷ)/√(σ² + σ*²), avec σ² la variance de bruit estimée et σ*² l'incertitude du modèle ; calculé dans l'espace warpé (gaussien) ; forme signée (Z) et absolue (|Z|) ; résumé global par la loi des valeurs extrêmes (GEV) ajustée au top 1 % des |Z| par sujet ; seuil de contraste longitudinal ΔZ > 0,5 (½ écart-type).

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : 
- Par région → association au phénotype : Z des WMH corrélés (Spearman) à la mémoire numérique (ρ = −0,033, p = 0,026). 
- Par région → comparaison de groupes : test de Wilcoxon (rank-sum) contrastant ΔZ > 0,5 vs non sur le longitudinal — temps de réaction W = 5,5641 (p < 0,001) et Trail Making Test W = 8,3105 (p < 0,001). 
- Global par sujet → détection d'atypies puis association au phénotype : valeurs extrêmes (top 1 %, GEV) corrélées au 1er composant principal cognitif (≈ facteur g, expliquant 29 % de variance) : ρ = 0,158, p < 0,001.

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : les déviations corrèlent avec la cognition (mémoire, temps de réaction, facteur g) ; l'augmentation de la charge en WMH est associée au déclin cognitif longitudinal. Cadre présenté comme extensible à des marqueurs de troubles psychiatriques (perspective, non réalisé ici).

## Mes réflexions
*(à compléter par moi)*
