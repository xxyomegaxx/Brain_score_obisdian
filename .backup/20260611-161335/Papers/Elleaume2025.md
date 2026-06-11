---
id: Elleaume2025
titre: "Toward Robust Neuroanatomical Normative Models: Influence of Sample Size and Covariates Distributions"
auteur_principal: "Camille Elleaume"
annee: 2025
journal: "eLife (reviewed preprint) / bioRxiv"
doi: "10.1101/2025.08.26.672402"
date_ajout: 2026-06-06
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
pertinence: 4
biomarqueur: "Non"
methode_detail:
  - "[[Warped BLR]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[UK Biobank]]"
  - "[[OASIS-3]]"
  - "[[AIBL]]"
application:
  - "[[Alzheimer]]"
  - "[[Vieillissement]]"
niveau_score:
  - "[[Par région]]"
  - "[[Global par sujet]]"
usage_score:
  - "[[Localisation]]"
  - "[[Détection d'atypies]]"
  - "[[Comparaison de groupes]]"
  - "[[Prédiction]]"
tags_libres: ["taille d'échantillon", "covariables", "transfer learning", "OASIS-3", "AIBL"]
fichier_source: "Elleaume et al., eLife reviewed preprint / bioRxiv 2025.08.26.672402"
---
![[Elleaume2025.svg|649]]

## TL;DR
Une étude systématique de l'effet de la **taille d'échantillon** et de la **distribution des covariables** (âge, sexe) sur la robustesse des modèles normatifs (Warped BLR) appliqués au vieillissement/Alzheimer : ~100–200 contrôles bien caractérisés suffisent pour des cartes de déviation cliniquement robustes, et un déséquilibre d'âge (surtout vers les jeunes) dégrade fortement les scores.

## Contributions
1. Quantifie l'effet de la taille d'échantillon : gains rapides jusqu'à n≈50, plateau après n≈200–300 (OASIS-3, répliqué sur AIBL). [Mod. normative]
2. Le déséquilibre de la distribution d'âge (surtout *left-skewed*/jeunes) dégrade fortement le fit et biaise les z-scores, bien plus que le déséquilibre de sexe. [Mod. normative]
3. Cartes de déviation AD cohérentes avec la pathologie (hippocampe, amygdale, cortex temporal) ; classification AD vs HC (AUC≈0,86) robuste dès ~15 sujets. [Biomarqueurs]
4. L'apprentissage par transfert depuis UK Biobank atteint la performance d'un modèle entraîné en cohorte avec ~4× moins de sujets (plateau n≈50 vs ~200).
5. Recommandations pratiques : ~200–300 contrôles comme base pragmatique pour la cartographie de déviation ; faire des courbes d'apprentissage par cohorte.

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Évalue systématiquement la robustesse des modèles normatifs. |
| Méthode | Stats classiques | Warped BLR (PCNtoolkit), pas d'apprentissage profond. |
| Population | Les deux | Contrôles sains + patients Alzheimer (OASIS-3, AIBL). |
| Type IRM | Structurel | Épaisseur corticale + volumes sous-corticaux (167 ROI, T1w). |
| Interprétabilité | Haute | Z-scores/centiles paramétriques interprétables. |
| Pertinence (1–5) | 4 | Guide pratique direct sur la taille d'échantillon en modélisation normative. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : épaisseur corticale + volumes sous-corticaux, 167 ROI ; niveau région ; OASIS-3 (n=692 HC à l'entraînement) + AD ; réplication sur AIBL.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge, sexe ; site (OASIS 1, AIBL 2, UKB 3) ; niveau sujet ; sous-échantillonnage manipulant les distributions d'âge (représentatif / left-skewed / right-skewed) et de sexe (1:1 → 1:10).

## Étape 2 — Modélisation normative
Méthode · granularité · validation : Warped Bayesian Linear Regression (PCNtoolkit), un modèle par ROI. Tailles d'échantillon de 5 à 692 (10 tirages chacune) ; comparaison entraînement direct en cohorte vs adaptation par transfer learning depuis UK Biobank pré-entraîné (n=42 747). Validation sur test set HC fixe (20%) + AD ; métriques MSLL, SMSE, EV, Rho, ICC + couverture des queues (2,5–97,5%) ; effets estimés par modèles mixtes linéaires.

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : Z-score par rapport au centile prédit, calculé par région et par sujet ; signé. Seuil outlier Z < −1,96 ; tOC (total outlier count) = nombre de régions outliers par sujet. Erreurs des z-scores quantifiées (MSE, MBE) relativement au modèle entraîné sur l'échantillon complet.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : niveaux **par région** (cartes de déviation) et **global par sujet** (tOC). Finalités réalisées : (a) **localisation** des régions atrophiées en AD (hippocampe 30,5 %, amygdale 28,1 %) ; (b) **détection d'atypies** via tOC (AD ≈14 vs HC ≈4 outliers/sujet) ; (c) **comparaison de groupes** AD vs HC ; (d) **prédiction** par classifieur SVC sur les z-scores (AUC≈0,86, robuste dès ~15 sujets).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : maladie d'Alzheimer / vieillissement. Les z-scores régionaux et le tOC distinguent l'AD des contrôles, avec des régions cohérentes avec la pathologie (hippocampe, amygdale, cortex entorhinal). Visée affichée : outil quantitatif interprétable d'aide à la décision en neuroradiologie.

## Biomarqueur identifié ?
**Verdict : Non**

Papier purement méthodologique : étude systématique de l'influence de la taille d'échantillon et de la composition en covariables du jeu de référence sur l'ajustement, les scores de déviation et les lectures cliniques en maladie d'Alzheimer (OASIS-3, AIBL, transfer learning depuis UK Biobank). Conclusion d'ordre méthodologique (~200 HC en interne, ~50 via adaptation). Aucun nouveau biomarqueur discriminatif proposé/validé : les lectures cliniques servent à évaluer la robustesse.

> « we systematically investigated how sample size and covariate composition of the reference cohort influence model fit, deviation estimates, and clinical readouts in Alzheimer's disease (AD). »

## Mes réflexions
*(à compléter par moi)*
