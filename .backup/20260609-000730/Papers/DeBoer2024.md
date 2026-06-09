---
id: DeBoer2024
titre: "Non-Gaussian normative modelling with hierarchical Bayesian regression"
auteur_principal: "Augustijn de Boer"
annee: 2024
journal: "Imaging Neuroscience"
doi: "10.1162/imag_a_00132"
date_ajout: 2026-06-05
statut: lu
theme:
  - "[[Mod. normative]]"
methode_cat:
  - "[[Stats classiques]]"
population:
  - "[[Les deux]]"
type_irm:
  - "[[Structurel]]"
  - "[[Fonctionnel]]"
interpretabilite: "[[Haute]]"
pertinence: 4
methode_detail:
  - "[[HBR]]"
  - "[[Warped BLR]]"
modalite_detail:
  - "[[sMRI]]"
  - "[[fMRI]]"
dataset:
  - "[[UK Biobank]]"
  - "[[ABCD]]"
application: []
niveau_score:
  - "[[Par région]]"
usage_score: []
tags_libres: ["SHASH", "federated learning", "MCMC"]
fichier_source: "de Boer et al., Imaging Neuroscience 2024 (préprint bioRxiv 2022.10.05.510988)"
---
![[DeBoer2024.svg|649]]

## TL;DR
Une extension du cadre HBR (régression bayésienne hiérarchique) pour la modélisation normative qui gère les phénotypes **non-gaussiens** (asymétrie et kurtosis) grâce à une vraisemblance SHASH reparamétrée (SHASH_b) adaptée à l'échantillonnage MCMC, à performance égale ou supérieure à la Warped BLR tout en offrant une inférence bayésienne complète.

## Contributions
1. Reparamétrisation **SHASH_b** qui supprime les corrélations entre paramètres et rend la distribution SHASH exploitable en MCMC. [Mod. normative]
2. Vraisemblance non-gaussienne (skew + kurtosis) intégrée au cadre **HBR** bayésien complet, avec postérieures sur tous les paramètres. [Mod. normative]
3. Comparaison étendue HBR-SHASH vs Warped BLR (baseline) sur un grand jeu multi-sites (58 834 contrôles, 82 scanners) : performances égales ou meilleures sur la gaussianité des z-scores. [Mod. normative]
4. Capacité à modéliser des distributions **hautement non-linéaires** (représentation latente IRMf de Zabihi et al.) impossibles à ajuster avec les méthodes existantes.
5. Extension open-source dans le PCNtoolkit, compatible apprentissage fédéré.

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Développe/valide une méthode de modélisation normative non-gaussienne. |
| Méthode | Stats classiques | HBR bayésien + vraisemblance SHASH, inférence MCMC ; pas d'apprentissage profond. |
| Population | Les deux | 58 834 contrôles + 2 925 patients (jeu Rutherford multi-sites). |
| Type IRM | Structurel (+ Fonctionnel) | Épaisseur corticale/volumes (T1w) ; 2ᵉ jeu = latent IRMf. |
| Interprétabilité | Haute | Postérieures complètes, z-scores/centiles paramétriques. |
| Pertinence (1–5) | 4 | Méthode de référence pour la modélisation normative non-gaussienne multi-sites. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : épaisseur corticale et volumes sous-corticaux (Freesurfer 6.0), par phénotype/région (IDP) ; phénotypes « durs » (ventricule latéral droit, hypointensités de matière blanche, cervelet) et « faciles » (ETICV, sulcus de Jensen, tronc cérébral). 2ᵉ jeu : représentation latente 2D (autoencodeur 100-d + UMAP) dérivée d'IRMf, n=20 781.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge, sexe (covariables) ; site (effet de batch / random effect) ; niveau sujet ; effet non-linéaire de l'âge via expansion de base.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : HBR avec vraisemblance **SHASH_b** (paramètres ε de skew, δ de kurtosis), inférence MCMC (2 chaînes × 1500, 500 de burn-in) ; variantes SHASH_b1 (ε, δ constants) et SHASH_b2 (ε, δ régressés sur les covariables). Baselines : Warped BLR et HBR-gaussien. Un modèle par phénotype ; 82 sites, 58 834 contrôles + 2 925 patients ; validation par 10-fold CV stratifiée (sites < 10 sujets/sexe exclus), convergence évaluée par Gelman-Rubin (R̂ < 1,1) ; z-scores estimés par MAP (MCMC marginalement meilleur).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : z-score = déviation par rapport au centile prédit, obtenu par transformation SHASH inverse ; calculé par phénotype et par sujet ; signé. Aucun seuillage clinique appliqué ici ; objectif méthodologique = que les z-scores des sujets sains suivent une N(0,1) (skew et kurtosis ≈ 0).

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : niveau **par région** (par phénotype). Usage **méthodologique** — aucune finalité clinique réalisée : (a) évaluation de la gaussianité des z-scores (3ᵉ/4ᵉ moments, QQ-plots) ; (b) suppression des effets de site mesurée par AUC de classification 1-contre-1 entre sites (≈ 0,5 = sites indistinguables). Stratification et transfert vers de nouveaux sites évoqués comme perspectives, non réalisés.

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : aucune — papier purement méthodologique. Les données patientes (n=2 925, transdiagnostique) servent uniquement à valider la méthode, sans analyse clinique en aval. Apprentissage fédéré et transfert décrits comme perspectives.

## Mes réflexions
*(à compléter par moi)*
