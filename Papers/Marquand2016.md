---
id: Marquand2016
titre: "Understanding Heterogeneity in Clinical Cohorts Using Normative Models: Beyond Case-Control Studies"
auteur_principal: Andre F. Marquand
annee: 2016
journal: Biological Psychiatry
doi: 10.1016/j.biopsych.2015.12.023
date_ajout: 2026-06-02
statut: lu
theme:
  - "[[Mod. normative]]"
  - "[[Biomarqueurs]]"
  - "[[Scores-méd. personnalisée]]"
methode_cat:
  - "[[Stats classiques]]"
population:
  - "[[Saine]]"
type_irm:
  - "[[Fonctionnel]]"
interpretabilite: "[[Haute]]"
pertinence: 5
methode_detail:
  - "[[GPR]]"
modalite_detail:
  - "[[fMRI]]"
dataset:
  - "[[HCP]]"
application:
  - "[[TDAH]]"
niveau_score:
  - "[[Par région]]"
  - "[[Global par sujet]]"
usage_score:
  - "[[Localisation]]"
  - "[[Détection d'atypies]]"
  - "[[Association au phénotype]]"
  - "[[Stratification]]"
tags_libres: [extreme-value-statistics, RDoC, heterogeneite]
fichier_source: 
---

## TL;DR
La modélisation normative permet d'étudier les troubles cérébraux au niveau de chaque individu — comme un écart à la norme plutôt qu'une appartenance à un groupe — brisant la symétrie artificielle de l'approche cas-témoins.

## Contributions
1. Introduit la modélisation normative comme alternative à l'approche cas-témoins, cartographiant la variation individuelle plutôt que deux groupes supposés homogènes. [Mod. normative]
2. Propose un Z-score (NPM) par région mesurant l'écart de chaque sujet à la norme, avec quantification de l'incertitude. [Biomarqueurs]
3. Agrège ces écarts en un indice d'anomalie individuel via les statistiques des valeurs extrêmes. [Scores-méd. personnalisée]
4. Montre que le degré de déviation se relie spécifiquement à l'hyperactivité (TDAH) mais pas à l'inattention. [Biomarqueurs]
5. Permet d'inclure les étiquettes diagnostiques comme covariables, donc d'inférer sur leur validité biologique. [Mod. normative]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Pose et illustre le cadre conceptuel de la modélisation normative |
| Méthode | Stats classiques | GPR bayésien + statistiques des valeurs extrêmes |
| Population | Saine | Cohorte HCP de 491 sains ; pathologie inférée comme extrême |
| Type IRM | Fonctionnel | IRMf de tâche (traitement de la récompense) |
| Interprétabilité | Haute | Cartes NPM régionales et Z-scores reliés à des symptômes |
| Pertinence (1–5) | 5 | Papier fondateur définissant le Z-score de déviation |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : activité cérébrale liée à la récompense (contraste IRMf récompense-baseline), modélisée indépendamment à chaque brainordinate (vertex cortical / voxel sous-cortical) ; nombre exact de brainordinates non précisé.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : delay discounting (impulsivité de trait, résumé par l'AUC à $200 et $40 000), au niveau du sujet ; effets non-linéaires accommodés par le noyau du processus gaussien.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : régression par processus gaussien (GPR) bayésienne, un modèle estimé par brainordinate, fournissant moyenne et variance prédictives ; validation croisée 10-fold respectant la structure familiale des données ; N = 491 participants sains (HCP).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : Z-score normatif (NPM) Z = (y − ŷ) / √(σ²ij + σ²nj) combinant erreur, variance prédictive et variance normative ; calculé par région ; versions signée (top/bottom 1 %) et absolue ; seuillage à p < .05 corrigé FDR ; distribution des valeurs extrêmes pour l'inférence au niveau sujet.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : **Par région** → localisation des régions déviantes par sujet (patrons individualisés, aucune région chez plus de 3 sujets) et détection d'atypies (22 sujets déviants). **Global par sujet** → indice d'anomalie agrégé (block maxima, moyenne robuste à 90 % du top 1 % des Z) corrélé à l'hyperactivité (r = .91 pour le top 1 %, persistant jusqu'au top 20 %), et stratification des sujets en « extrême normal » vs. « déviation idiosyncrasique ».

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : la déviance se relie spécifiquement à l'hyperactivité du TDAH (et non à l'inattention), distinguant deux mécanismes biologiques convergeant vers le même symptôme ; cadre cohérent avec le RDoC, permettant d'étudier les axes de variation sans dichotomiser la cohorte ni présupposer les étiquettes diagnostiques.

## Mes réflexions
*(à compléter par moi)*
