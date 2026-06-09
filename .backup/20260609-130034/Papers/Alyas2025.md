---
id: Alyas2025
titre: "Normative Modelling in Neuroimaging: A Practical Guide for Researchers"
auteur_principal: "Nida Alyas"
annee: 2025
journal: "arXiv (preprint)"
doi: "10.48550/arXiv.2509.07237"
date_ajout: 2026-06-08
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
methode_detail:
  - "[[Régression linéaire]]"
  - "[[GPR]]"
  - "[[GAMLSS]]"
  - "[[HBR]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[IDEAS]]"
  - "[[ENIGMA]]"
application:
  - "[[Épilepsie]]"
niveau_score:
  - "[[Par région]]"
usage_score:
  - "[[Localisation]]"
  - "[[Détection d'atypies]]"
  - "[[Comparaison de groupes]]"
tags_libres: []
fichier_source: "arXiv:2509.07237 (PDF)"
---
![[Alyas2025.svg|649]]
## TL;DR
Un guide pratique pour utiliser des modèles normatifs pré-entraînés en recherche clinique : comment calibrer un modèle à un nouveau site, combien de témoins il faut, et comment vérifier la calibration — illustré par un exemple d'épilepsie temporale mésiale gauche.

## Contributions
1. Compare modélisation normative et approche cas-témoins, et montre la robustesse des déviations aux écarts démographiques (âge, sexe). [Mod. normative]
2. Quantifie combien de témoins site-spécifiques sont nécessaires pour calibrer un modèle pré-entraîné (dès ~30, mais davantage est préférable). [Biomarqueurs]
3. Donne des recommandations pratiques pour vérifier qu'un modèle pré-entraîné est bien calibré à de nouvelles données. [Mod. normative]
4. Illustre chaque point sur un cas réel d'épilepsie (dataset IDEAS, plateforme Brain MoNoCle). [Biomarqueurs]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Revue méthodologique centrée sur l'usage des modèles normatifs. |
| Méthode | Stats classiques | Discute régression linéaire, GPR, GAMLSS, HBR. |
| Population | Les deux | Exemple : patients TLE gauche (n=23) + 70 témoins sains. |
| Type IRM | Structurel | Épaisseur corticale (atlas Desikan-Killiany, FreeSurfer). |
| Interprétabilité | Haute | Z-scores/centiles par région, cartes d'anomalie individuelles. |
| Pertinence (1–5) | 4 | Guide pratique utile sur la calibration et les pièges d'usage. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : épaisseur corticale (surface, volume évoqués) par région, atlas Desikan-Killiany via FreeSurfer (recon-all) ; exemple = 23 TLE mésial gauche + 70 témoins (IDEAS).
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge, sexe, site du scanner ; modèles capables de relations non linéaires et distributions non gaussiennes.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : revue d'algorithmes (régression linéaire, GPR, GAMLSS, HBR) et de modèles pré-entraînés (Brain MoNoCle, BrainChart, PCN Toolkit, CentileBrain) ; calibration au nouveau site via un petit échantillon de témoins ; convergence des modèles vers ~3000 sujets d'entraînement, calibration raisonnable dès n≈30 témoins.

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : Z-scores/centiles par région vs distribution saine attendue ; cartes d'anomalie individuelles (réductions/augmentations) ; robustes aux écarts démographiques (différence moyenne de taille d'effet régionale 0,12–0,19 ; r=0,84–0,94 entre groupes appariés vs non appariés).

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : **Par région** — cartes Z d'anomalie d'un sujet (localisation), déviations individuelles robustes (détection d'atypies), et tailles d'effet régionales (Cohen's d) cas-témoins agrégées, comparées aux effets ENIGMA-épilepsie.

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : adoption responsable de modèles pré-entraînés en clinique ; exemple d'épilepsie temporale mésiale gauche montrant des réductions corticales individuelles fiables même avec peu de témoins.

## Mes réflexions
*(à compléter par moi)*
