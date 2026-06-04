---
id: DiBiase2022
titre: Cell type-specific manifestations of cortical thickness heterogeneity in schizophrenia
auteur_principal: Maria A. Di Biase
annee: 2022
journal: Molecular Psychiatry
doi: 10.1038/s41380-022-01460-7
date_ajout: 2026-06-03
statut: lu
theme:
  - "[[Biomarqueurs]]"
  - "[[Mod. normative]]"
  - "[[Scores-méd. personnalisée]]"
methode_cat:
  - "[[Stats classiques]]"
population:
  - "[[Les deux]]"
type_irm:
  - "[[Structurel]]"
interpretabilite: "[[Haute]]"
pertinence: 5
methode_detail:
  - "[[Régression quantile]]"
  - "[[Clustering Ward]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[HCP]]"
  - "[[ASRB]]"
  - "[[Allen Human Brain Atlas]]"
application:
  - "[[Schizophrénie]]"
niveau_score:
  - "[[Par région]]"
  - "[[Global par sujet]]"
usage_score:
  - "[[Détection d'atypies]]"
  - "[[Localisation]]"
  - "[[Comparaison de groupes]]"
  - "[[Association au phénotype]]"
  - "[[Stratification]]"
tags_libres: []
fichier_source: PDF déposé (non précisé)
---
![[DiBiase2022.svg|692]]
## TL;DR
L'hétérogénéité de l'épaisseur corticale en schizophrénie s'explique par des contributions de types cellulaires distincts : en cartographiant les déviations individuelles sur des cartes d'expression génique, on stratifie les patients en sous-types cellulaires validés par leur risque polygénique propre.

## Contributions
1. L'hétérogénéité de l'épaisseur corticale s'aligne sur l'expression de types cellulaires précis (astrocytes, endothélial, OPC, neurones excit./inhib.). [Biomarqueurs]
2. Modèle normatif (régression quantile, âge+sexe) sur 34 régions, validé sur 2 cohortes indépendantes. [Mod. normative]
3. Stratification des patients en 3 sous-types cellulaires à partir des profils de déviation individuels. [Scores-méd. personnalisée]
4. Validation génomique : la déviation corticale covarie avec le risque polygénique cellulaire correspondant. [Biomarqueurs]
5. Intégration de 3 échelles biologiques (génome, transcriptome, IRM) chez les mêmes individus. [Mod. normative]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Biomarqueurs | Cherche les types cellulaires sous-tendant l'hétérogénéité corticale. |
| Méthode | Stats classiques | Régression quantile + PCA + clustering de Ward. |
| Population | Les deux | Normes sur témoins, déviations chez les patients. |
| Type IRM | Structurel | Épaisseur corticale (IRM anatomique). |
| Interprétabilité | Haute | Centiles/z-scores et cartes cellulaires interprétables. |
| Pertinence (1–5) | 5 | Modèle normatif + déviations + biomarqueurs cellulaires en schizophrénie. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : épaisseur corticale (CTh) ; par région ; 34 régions de l'atlas Desikan-Killiany (hémisphère gauche), une valeur par région et par sujet.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge et sexe ; niveau sujet ; effets non-linéaires captés par les courbes de centiles de la régression quantile.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : régression quantile avec IC par bootstrap (n=1000), plage normative = centiles 5–95 % en fonction de l'âge/sexe ; granularité par région (34 régions) ; entraînée sur témoins sains (n=1127 HCP, n=185 ASRB) ; validée sur 2 cohortes indépendantes (>90 % des témoins dans la plage).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : déviation Δ exprimée en z-score par région et par sujet ; catégorisation normal / supra-normal / infra-normal ; signé ; seuillage aux 5ᵉ et 95ᵉ centiles ; >80 % des patients restent dans la plage pour chaque région.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : (Par région) détection d'atypies, localisation (frontal/temporal/insula), comparaison patients vs témoins, et couplage du profil de déviation aux cartes d'expression de 7 types cellulaires (5/7 significatifs, Ansari-Bradley FDR<0,05) ; (Global par sujet) stratification en 3 sous-types (Ward+PCA) et covariation de la déviation moyenne avec les scores polygéniques cellulaires (sczPRS) — Sous-type I r=−0,40 (FDRp=0,010), III r=−0,30 (FDRp=0,028), II r=+0,20 (FDRp=0,037).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : stratification cellulaire de la schizophrénie pouvant orienter la modélisation in vitro de sous-groupes de patients ; les sous-types ne sont pas expliqués par les symptômes ni la durée de maladie ; appuie l'idée d'une maladie multicellulaire à composition variable selon l'individu.

## Mes réflexions
*(à compléter par moi)*
