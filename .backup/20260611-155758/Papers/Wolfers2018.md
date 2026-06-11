---
id: Wolfers2018
titre: "Mapping the Heterogeneous Phenotype of Schizophrenia and Bipolar Disorder Using Normative Models"
auteur_principal: "Thomas Wolfers"
annee: 2018
journal: "JAMA Psychiatry"
doi: "10.1001/jamapsychiatry.2018.2467"
date_ajout: 2026-06-07
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
biomarqueur: "Candidat"
methode_detail:
  - "[[GPR]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[TOP]]"
application:
  - "[[Schizophrénie]]"
  - "[[Trouble bipolaire]]"
niveau_score:
  - "[[Par région]]"
usage_score:
  - "[[Localisation]]"
  - "[[Comparaison de groupes]]"
  - "[[Association au phénotype]]"
  - "[[Détection d'atypies]]"
tags_libres: ["VBM", "schizophrénie", "trouble bipolaire", "hétérogénéité", "déviation extrême", "TOP Oslo"]
fichier_source: "Wolfers et al., JAMA Psychiatry 75(11):1146-1155 (2018) — PMC6248110"
---
![[Wolfers2018.svg|649]]
## TL;DR
En cartographiant, sujet par sujet, l'écart de chaque cerveau à un modèle normatif d'âge/sexe (régression par processus gaussien sur la morphométrie VBM), l'étude montre que la « moyenne du patient » est trompeuse : les déviations extrêmes sont fréquentes mais **très hétérogènes**, avec un chevauchement spatial supérieur à 2 % des patients seulement dans quelques régions (frontales, temporales, cérébelleuses). La schizophrénie présente plus de déviations négatives extrêmes (0,9 % des voxels en substance grise) que les contrôles (0,23 %) et que le trouble bipolaire (0,24 %).

## Contributions
1. Démontre que les différences de groupe (case-control) masquent l'essentiel des anomalies cérébrales, qui sont en réalité individuelles et hétérogènes. [Mod. normative]
2. Quantifie le chevauchement spatial des déviations extrêmes entre patients : >2 % seulement dans de rares loci, prouvant que « le patient moyen » est un construit peu informatif. [Biomarqueurs]
3. Montre que la proportion de voxels extrêmes est associée au diagnostic et aux caractéristiques cognitives/cliniques au sein des groupes. [Biomarqueurs]
4. Fournit un cadre reproductible (Z-scores voxel par voxel, seuil |z|>2,6) ouvrant une voie vers la médecine de précision en psychiatrie. [Mod. normative]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Applique un modèle normatif pour cartographier l'hétérogénéité individuelle. |
| Méthode | Stats classiques | Régression par processus gaussien (GPR) sur âge + sexe. |
| Population | Les deux | 256 contrôles sains + 218 schizophrénie + 190 bipolaires. |
| Type IRM | Structurel | T1w : VBM (substance grise/blanche) + FreeSurfer (épaisseur corticale, aire piale). |
| Interprétabilité | Haute | Z-scores voxel par voxel, directement localisables et signés. |
| Pertinence (1–5) | 5 | Article fondateur de l'application clinique de la modélisation normative à l'hétérogénéité. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : volumes régionaux de substance grise et blanche issus de la morphométrie voxel-à-voxel (VBM) sur images T1w ; mesures complémentaires d'épaisseur corticale et d'aire piale (FreeSurfer) ; niveau voxel/région. Données : étude TOP (Thematically Organized Psychosis, Oslo).
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge et sexe ; niveau sujet ; non-linéarités captées par le noyau du processus gaussien.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : **régression par processus gaussien (GPR)** prédisant le volume régional à partir de l'âge et du sexe, par voxel/région ; normativité estimée chez les 256 sujets sains en **validation croisée 10-fold**, puis modèle entraîné sur l'ensemble appliqué aux patients. La GPR fournit une mesure de confiance prédictive (incertitude) utilisée pour normaliser les écarts.

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : Z-score par voxel = (volume observé − volume prédit) / incertitude de la prédiction ; signé (déviations positives et négatives) ; déviation extrême définie par **|z| > 2,6** (P < 0,005), seuil fixe et identique pour tous les sujets.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : **par région** — cartes individuelles et cartes de chevauchement (% de patients déviants par locus) ; comparaison de groupes par PALM/permutations (substance grise : SZ 0,9 % vs HC 0,23 % vs BD 0,24 % de voxels extrêmes négatifs). Chevauchement >2 % seulement en régions frontales, temporales, cérébelleuses. Le % de voxels extrêmes est associé au diagnostic et aux performances cognitives/cliniques (corrigé Bonferroni-Holm).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : schizophrénie (déficits frontaux, temporaux, cérébelleux) et trouble bipolaire (déficits surtout cérébelleux). Les profils étant individuels, l'approche soutient une stratification et une médecine de précision plutôt qu'un biomarqueur de groupe unique.

## Biomarqueur identifié ?
**Verdict : Candidat**

Cartes de déviation voxelwise individualisées (régression par processus gaussien) en schizophrénie/trouble bipolaire. Les déviations extrêmes sont très hétérogènes — moins de 2% des patients partagent une anomalie au même endroit — donc aucune région universelle. Différence de groupe quantitative dans la charge de déviations extrêmes (SCZ 0,9% des voxels vs contrôles 0,23%, chi2 = 219,67, p<.001), liée a la cognition. L'article conclut toutefois qu'aucun biomarqueur individuel robuste n'est établi (pas de classifieur validé) ; le cadre de déviation est proposé comme voie.

> « patients with schizophrenia had a higher percentage of extreme negative deviations across voxels (0.9% of voxels) compared with healthy individuals (0.23% of voxels, P < .001) »

## Mes réflexions
*(à compléter par moi)*
