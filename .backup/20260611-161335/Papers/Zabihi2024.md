---
id: Zabihi2024
titre: "Nonlinear latent representations of high-dimensional task-fMRI data: Unveiling cognitive and behavioral insights in heterogeneous spatial maps"
auteur_principal: Mariam Zabihi
annee: 2024
journal: PLoS ONE
doi: 10.1371/journal.pone.0308329
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
  - "[[Fonctionnel]]"
interpretabilite: "[[Haute]]"
pertinence: 4
biomarqueur: "Candidat"
methode_detail:
  - "[[Autoencodeur 3D semi-supervisé]]"
  - "[[UMAP]]"
  - "[[HBR]]"
modalite_detail:
  - "[[fMRI]]"
dataset:
  - "[[HCP]]"
  - "[[UK Biobank]]"
application:
  - "[[Vieillissement]]"
niveau_score:
  - "[[Global par sujet]]"
usage_score:
  - "[[Association au phénotype]]"
tags_libres: []
fichier_source: 
---

## TL;DR
Un autoencodeur 3D semi-supervisé apprend une représentation latente non linéaire de la task-fMRI cerveau entier ; un modèle normatif (HBR) sur ce latent (réduit par UMAP) fournit un « latent index » individuel qui s'associe à de nombreux phénotypes, plus fortement que les méthodes linéaires (PCA/ICA/ROIs).

## Contributions
1. Représentation latente non linéaire de la task-fMRI cerveau entier, sans ROIs prédéfinies. [Mod. normative]
2. Apprentissage semi-supervisé (âge + sexe dans le coût) : latent interprétable et décodable vers l'espace voxel. [Biomarqueurs]
3. « Latent index » individuel = z-score de déviation au modèle normatif HBR sur les composantes UMAP. [Scores-méd. personnalisée]
4. Index associé à de nombreux nIDPs après contrôle âge/sexe, plus fortement que PCA/ICA/ROIs. [Biomarqueurs]
5. Bonne prédiction d'âge (MAE 3,13/4,84) et de sexe (81 %/89 %), cartes validées par NeuroSynth. [Mod. normative]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Modèle normatif HBR sur le latent → index de déviation individuel |
| Méthode | Hybride | Autoencodeur profond (IA) chaîné à une régression bayésienne hiérarchique |
| Population | Saine | HCP (jeunes adultes) + UKB (population générale) ; clinique = perspective |
| Type IRM | Fonctionnel | Contrastes task-fMRI uniquement |
| Interprétabilité | Haute | Latent décodable vers l'espace voxel + validation NeuroSynth |
| Pertinence (1–5) | 4 | Cœur normatif + score individuel ; mais fonctionnel, population saine |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : contrastes task-fMRI cerveau entier ; niveau voxel (56×64×56, 3 mm) ; ~40K scans HCP (86 contrastes), ~104K scans UKB (5 contrastes).
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge (continu) + sexe, en cibles supervisées de l'autoencodeur ; effets non linéaires modélisés par HBR (sexe = effet de batch).

## Étape 2 — Modélisation normative
Méthode · granularité · validation : autoencodeur 3D conv. semi-supervisé (λ=0,05, bottleneck 100 nœuds) → UMAP 2 composantes → HBR (non gaussien, hétéroscédastique) ; granularité : composantes UMAP globales ; validation : 5-fold au niveau sujet (HCP, n=468), split train/test (UKB, n=20 781).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : latent index = z-score de déviation à la normative UMAP, par composante et par sujet ; combine les 2 composantes UMAP du latent ; direction signée (z) ; seuillage non rapporté.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : niveau global par sujet ; but = association au phénotype ; corrélation de Spearman entre le latent index et les nIDPs après contrôle âge/sexe ; comparé à PCA, ICA, ROIs (associations plus faibles).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : biomarqueur candidat des scores cognitifs/comportementaux ; détection d'atypies cliniques évoquée comme perspective (non réalisée dans ce papier).

## Biomarqueur identifié ?
**Verdict : Candidat**

Autoencodeur 3D semi-supervisé + modélisation normative (HBR) sur l'espace latent (UMAP) dans des cohortes saines (HCP, UK Biobank) ; l'indice latent de déviation est fortement associé aux mesures cognitives/comportementales (nIDPs). Aucune discrimination d'une population clinique ; les auteurs qualifient eux-mêmes ces déviations de candidate biomarkers. Proposition associative non validée comme biomarqueur discriminatif -> Candidat.

> « The deviations from this manifold are informative about individual differences and provide candidate biomarkers. »

## Mes réflexions
*(à compléter par moi)*
