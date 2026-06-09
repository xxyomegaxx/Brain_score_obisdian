---
id: Dorfschmidt2025
titre: "Charting structural brain asymmetry across the human lifespan"
auteur_principal: "Lena Dorfschmidt"
annee: 2025
journal: "bioRxiv (preprint)"
doi: "10.1101/2025.07.21.665924"
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
pertinence: 4
methode_detail:
  - "[[GAMLSS]]"
  - "[[Polynômes fractionnaires]]"
  - "[[k-means]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[UK Biobank]]"
application:
  - "[[Neurodéveloppement]]"
  - "[[Vieillissement]]"
  - "[[Autisme]]"
  - "[[Schizophrénie]]"
  - "[[Alzheimer]]"
niveau_score:
  - "[[Par région]]"
usage_score:
  - "[[Localisation]]"
  - "[[Comparaison de groupes]]"
  - "[[Détection d'atypies]]"
  - "[[Association au phénotype]]"
tags_libres: []
fichier_source: "Dorfschmidt et al. bioRxiv 2025.07.21.665924"
---
![[Dorfschmidt2025.svg|649]]
## TL;DR
Premier jeu complet de « brain charts » de l'asymétrie structurelle hémisphérique sur toute la vie (de la mi-gestation à 102 ans), construit par GAMLSS sur 177 701 scans de 138 231 individus issus de 128 études : il fournit des trajectoires normatives spécifiques à chaque hémisphère et des scores de centile d'asymétrie régionaux, dont la variabilité augmente dans l'autisme, la schizophrénie et Alzheimer.

## Contributions
1. Trajectoires normatives hémisphère-spécifiques (volume MG, épaisseur, surface, sous-cortical) de la mi-gestation à 102 ans. [Mod. normative]
2. Premier atlas lifespan de l'asymétrie : asymétrie gauche précoce des cortex associatifs, asymétrie droite tardive des régions sensorielles. [Mod. normative]
3. Scores de centile d'asymétrie individuels révélant une variabilité accrue (écart-type) dans l'autisme, la schizophrénie et Alzheimer. [Biomarqueurs]
4. Les régions à plus faible corrélation génétique gauche-droite sont les plus asymétriques (ρ_GM = −0,63, P_spin < 0,01) ; héritabilité SNP de 2-6 %.
5. Ressource ouverte (brainchart.io) : courbes de référence, code et statistiques GWAS pour des scores d'asymétrie sur données externes.

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Construit des chartes normatives lifespan de développement et d'asymétrie. |
| Méthode | Stats classiques | GAMLSS avec polynômes fractionnaires et effet de site, pas d'apprentissage profond. |
| Population | Les deux | Modèles estimés sur sujets sains, appliqués à des cohortes cliniques (ASD, SCZ, AD). |
| Type IRM | Structurel | T1w/T2w : volume MG, épaisseur, surface, volumes sous-corticaux. |
| Interprétabilité | Haute | Centiles et scores de centile standardisés directement lisibles. |
| Pertinence (1-5) | 4 | Référence lifespan riche pour biomarqueurs d'asymétrie, mais focalisée et en préprint. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : volume de matière grise corticale, épaisseur corticale, surface corticale et volumes sous-corticaux, ainsi qu'un indice d'asymétrie régional AI = (L − R) / (L + R) par paire de régions ; niveau par région (atlas Desikan-Killiany ; M-CRIB pour le fœtal/néonatal) ; 177 701 scans de 138 231 individus, 128 études, 25 pays.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge (de ~20 semaines post-menstruelles à 102 ans, échelle log), sexe (modèles stratifiés), site (effet aléatoire) ; niveau sujet/site ; effets d'âge non-linéaires via polynômes fractionnaires (cadre GAMLSS).

## Étape 2 — Modélisation normative
Méthode · granularité · validation : GAMLSS modélisant moyenne, variance, asymétrie et kurtosis, avec polynômes fractionnaires de l'âge et effet aléatoire de site ; sélection de la distribution par AIC ; un modèle par région et par hémisphère, puis modèles explicites d'asymétrie ; prétraitement FreeSurfer/SynthSeg, QC automatique par Euler index ; agrégation des petits sites en pseudo-sites ; robustesse par analyse leave-one-study-out et bootstrap stratifié (sexe/site). Clustering k-means (5 groupes) des trajectoires de volume MG pour dégager des profils de maturation.

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : avec les moments d'ordre supérieur du GAMLSS, le z-score classique n'est plus valide ; on calcule le centile de chaque observation et un « centile standard » (quantile de la loi normale) ; scores de centile régionaux par hémisphère et scores de centile d'asymétrie ; direction signée (AI > 0 = dominance gauche, AI < 0 = dominance droite) ; pas de seuil d'extrême unique rapporté (raisonnement sur la distribution complète des centiles).

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : niveau **par région**. Finalités : (a) **localisation** des trajectoires et jalons (pic de croissance/déclin), avec asymétrie gauche précoce des cortex associatifs et droite tardive des régions sensorielles ; (b) **comparaison de groupes** — différences cas-témoins des scores de centile d'asymétrie (ASD, SCZ, AD ; P_FDR < 0,05), plus localisées que pour les centiles hémisphériques ; (c) **détection d'atypies** — centiles plus extrêmes et écart-type accru chez les patients ; (d) **association au phénotype** — effet de la latéralité manuelle, corrélation génétique gauche-droite (ρ_GM = −0,63) et héritabilité SNP (2-6 %).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : appliqué à l'autisme, la schizophrénie et la maladie d'Alzheimer ; les différences moyennes d'asymétrie sont modestes mais la variabilité (écart-type des centiles) est nettement accrue chez les patients, cohérent avec une « asymétrie fluctuante » transdiagnostique liée à l'instabilité développementale ; pistes de diagnostic de précision (stratification du risque au neurodéveloppement, suivi des déséquilibres gauche-droite précoces en Alzheimer). Les auteurs présentent ces usages cliniques comme une démonstration de faisabilité.

## Mes réflexions
*(à compléter par moi)*
