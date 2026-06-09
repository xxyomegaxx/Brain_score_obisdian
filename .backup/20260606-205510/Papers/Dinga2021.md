---
id: Dinga2021
titre: "Normative modeling of neuroimaging data using generalized additive models of location scale and shape"
auteur_principal: Richard Dinga
annee: 2021
journal: bioRxiv (preprint)
doi: 10.1101/2021.06.14.448106
date_ajout: 2026-06-03
statut: lu
theme:
  - "[[Mod. normative]]"
methode_cat:
  - "[[Stats classiques]]"
population:
  - "[[Saine]]"
type_irm:
  - "[[Structurel]]"
interpretabilite: "[[Haute]]"
pertinence: 4
methode_detail:
  - "[[GAMLSS]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[UK Biobank]]"
application:
  - "[[Vieillissement]]"
niveau_score:
  - "[[Par région]]"
usage_score:
  - "[[Détection d'atypies]]"
tags_libres: [SHASH, transfert-site, calibration, worm-plot]
fichier_source: 
---
![[Dinga2021.png]]
## TL;DR
GAMLSS offre un cadre unique et flexible pour la modélisation normative du cerveau : il modélise simultanément les effets non-linéaires de l'âge, l'hétéroscédasticité (site, âge) et la non-gaussianité (loi SHASH), avec des outils de diagnostic dédiés et une procédure de transfert vers de nouveaux sites.

## Contributions
1. Introduit GAMLSS pour la modélisation normative cérébrale, unifiant non-linéarité, hétéroscédasticité et distributions non gaussiennes. [Mod. normative]
2. Décrit des outils de diagnostic/validation (logscore, MSLL, W de Shapiro-Wilk, worm plots, AIC/BIC) applicables au-delà de GAMLSS. [Mod. normative]
3. Montre pas-à-pas la modélisation des effets âge, sexe et site, et propose un modèle de base par défaut. [Mod. normative]
4. Démontre sur UK Biobank l'avantage du modèle non gaussien (meilleure calibration, écarts de z-scores dans les queues).
5. Propose une procédure de transfert vers un site non vu (réajustement de l'intercept et de l'échelle via offset). [Mod. normative]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Construit et valide un cadre de modélisation normative (GAMLSS). |
| Méthode | Stats classiques | Modèle statistique paramétrique (GAMLSS/SHASH). |
| Population | Saine | Sujets de référence sains (UK Biobank). |
| Type IRM | Structurel | Épaisseur corticale (FreeSurfer). |
| Interprétabilité | Haute | Fonctions lisses et paramètres de distribution interprétables. |
| Pertinence (1–5) | 4 | Référence méthodologique centrale, sans application biomarqueur. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : épaisseur corticale (médiane par ROI), 150 ROIs corticales, FreeSurfer 5.3/6.0 ; taille d'échantillon non rapportée (split 70 % train / 30 % test, UK Biobank).
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge, sexe, site de scan ; niveau sujet ; effet de l'âge modélisé de façon non-linéaire (splines pénalisées, GAM), hétéroscédasticité (σ) modélisée selon l'âge et le site.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : GAMLSS avec distribution SHASH à 4 paramètres (µ, σ, ν, τ), chaque paramètre fonction des covariables ; ajustement par maximum de vraisemblance pénalisé (bibliothèque mgcv) ; granularité par ROI ; validation sur jeu de test (split 70/30), comparaison par AIC/BIC, GAIC, logscore/déviance, MSLL, et W de Shapiro-Wilk ; transfert vers nouveau site par réajustement intercept + échelle (offset).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : pseudo-z-scores (résidus quantiles randomisés) ; centiles de la distribution ajustée mappés vers z d'une normale standard ; score signé ; pas de seuil clinique systématique, possibilité de vraisemblance censurée (ex. 1er–99e percentile) pour la robustesse et le ciblage des queues.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : scores au niveau de chaque ROI ; usage essentiellement méthodologique — quantification de la déviation individuelle et vérification de la calibration (les pseudo-z-scores doivent être ~N(0,1)) ; comparaison des z-scores entre modèles gaussien et non gaussien. Aucune association à un phénotype clinique ni comparaison de groupes patients/témoins n'est réalisée dans ce papier.

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : non réalisée dans ce papier (données saines). Applications mentionnées comme motivation via la littérature citée : schizophrénie et bipolaire (Wolfers 2018), TDAH (Wolfers 2020), lésion de substance blanche chez le nouveau-né (O'Muircheartaigh 2020).

## Mes réflexions
*(à compléter par moi)*
