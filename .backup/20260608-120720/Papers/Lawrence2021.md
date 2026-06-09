---
id: Lawrence2021
titre: "Age and sex effects on advanced white matter microstructure measures in 15,628 older adults: A UK biobank study"
auteur_principal: Katherine E. Lawrence
annee: 2021
journal: Brain Imaging and Behavior
doi: 10.1007/s11682-021-00548-y
date_ajout: 2026-06-03
statut: lu
theme:
  - "[[Mod. normative]]"
  - "[[Biomarqueurs]]"
methode_cat:
  - "[[Stats classiques]]"
population:
  - "[[Saine]]"
type_irm:
  - "[[Diffusion]]"
interpretabilite: "[[Haute]]"
pertinence: 3
methode_detail:
  - "[[Polynômes fractionnaires]]"
  - "[[Régression quantile]]"
modalite_detail:
  - "[[dMRI]]"
dataset:
  - "[[UK Biobank]]"
application:
  - "[[Vieillissement]]"
niveau_score:
  - "[[Par région]]"
usage_score: []
tags_libres: []
fichier_source: 
---
![[Lawrence2021.svg|697]]

## TL;DR
Sur 15 628 adultes (45–80 ans) de l'UK Biobank, l'âge et le sexe affectent largement la microstructure de la substance blanche ; parmi quatre modèles dMRI, les modèles les plus fidèles à la neurobiologie sont les plus sensibles (TDF pour l'âge, NODDI pour le sexe), et des courbes centiles normatives sexe-stratifiées sont fournies comme référence.

## Contributions
1. Caractérise âge et sexe sur la microstructure WM dans le plus grand échantillon dMRI publié (n=15 628). [Mod. normative]
2. Compare 4 modèles dMRI (DTI, TDF, NODDI, MAPMRI) et identifie les plus sensibles. [Biomarqueurs]
3. Les modèles fidèles à la biologie dominent : TDF pour l'âge, NODDI pour le sexe et l'interaction âge×sexe.
4. Courbes centiles normatives sexe-stratifiées par région (5e/25e/50e/75e/95e). [Mod. normative]
5. Âge modélisé en non-linéaire (polynômes fractionnaires).

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Courbes centiles normatives de référence. |
| Méthode | Stats classiques | Polynômes fractionnaires + régression quantile. |
| Population | Saine | Cohorte communautaire UK Biobank. |
| Type IRM | Diffusion | dMRI seulement. |
| Interprétabilité | Haute | Modèles paramétriques, effets en R². |
| Pertinence (1–5) | 3 | Référentiel normatif pertinent, mais stats classiques, sans brainscore. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : 12 métriques de microstructure WM — DTI (FA, MD, AD, RD), TDF (FA), NODDI (OD, ICVF, ISOVF), MAPMRI (RTOP, RTAP, RTPP) ; niveau par ROI (WM totale, corps calleux, +14 ROIs d'atlas) ; n=15 628 sujets (45–80 ans, 47,6 % hommes).
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge et sexe ; covariables de nuisance (liste exacte non précisée dans le texte principal) ; âge modélisé non-linéairement par polynômes fractionnaires.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : polynômes fractionnaires pour les effets d'âge ; régression quantile pour les courbes centiles sexe-stratifiées ; granularité par ROI ; étude transversale, un seul scanner ; robustesse testée (seuils p<0,01 et p<0,001, modèle d'âge alternatif).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : « score » = position sur les courbes centiles normatives (par âge et sexe) ; centiles fournis 5e/25e/50e/75e/95e ; direction implicite des extrêmes (<5e ou >95e centile = « anormal ») ; aucun Z-score / score de déviation par sujet n'est calculé ni appliqué — le livrable est le référentiel.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : niveau par région ; usage réalisé = caractérisation des tailles d'effet âge/sexe par ROI et comparaison de la sensibilité des modèles ; les finalités de score de déviation (détection d'atypies, stratification) sont évoquées comme motivation mais non réalisées (« non précisé » côté implémentation).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : courbes normatives destinées à permettre, à l'avenir, le repérage d'individus à WM anormale pour leur âge/sexe et le ciblage des phénotypes les plus atteints (maladies neurodégénératives, ex. Alzheimer) — non réalisé dans ce papier.

## Mes réflexions
*(à compléter par moi)*
