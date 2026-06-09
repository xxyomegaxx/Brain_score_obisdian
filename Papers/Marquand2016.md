---
id: Marquand2016
titre: "Understanding Heterogeneity in Clinical Cohorts Using Normative Models: Beyond Case-Control Studies"
auteur_principal: Marquand
annee: 2016
journal: Biological Psychiatry
doi: 10.1016/j.biopsych.2015.12.023
date_ajout: 2026-06-03
statut: lu
theme:
  - "[[Mod. normative]]"
  - "[[Biomarqueurs]]"
  - "[[Scores-méd. personnalisée]]"
methode_cat:
  - "[[IA]]"
population:
  - "[[Saine]]"
type_irm:
  - "[[Fonctionnel]]"
interpretabilite: "[[Haute]]"
pertinence: 5
biomarqueur: "Candidat"
methode_detail:
  - "[[GPR]]"
  - "[[EVS]]"
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
tags_libres: []
fichier_source:
---

![[Marquand2016.png]]

## TL;DR
Premier cadre de modélisation normative pour l'imagerie : on apprend la distribution normale d'une population saine, puis on mesure pour chaque individu et chaque région son écart au modèle (Z-score), résumé en un indice d'anomalie unique — une alternative au paradigme cas-témoins qui permet l'inférence au niveau individuel.

## Contributions
1. Introduit la modélisation normative pour parser l'hétérogénéité, sans dichotomiser la cohorte. [Mod. normative]
2. Score de déviation probabiliste (Z/NPM) par sujet et par région, avec incertitude, via GPR. [Mod. normative]
3. Indice d'anomalie global par sujet via théorie des valeurs extrêmes (brainscore). [Scores-méd. personnalisée]
4. Spécificité clinique : corrélation avec l'hyperactivité (r=.91 top 1%) mais pas l'inattention. [Biomarqueurs]
5. Deux mécanismes distincts derrière un même symptôme (extrême normal vs déviation idiosyncrasique). [Biomarqueurs]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Article fondateur du cadre de modélisation normative |
| Méthode | IA | GPR (apprentissage bayésien) au cœur du modèle |
| Population | Saine | Cohorte saine N=491 (HCP) |
| Type IRM | Fonctionnel | Contrastes fMRI récompense–baseline |
| Interprétabilité | Haute | NPM par région lisibles + incertitude explicite |
| Pertinence (1–5) | 5 | Papier socle du projet |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : images de contraste fMRI (récompense − baseline) ; niveau voxel/vertex (« brainordinate »), cerveau entier ; N = 491 sujets sains (HCP, 288 femmes, âge moyen 27 ans).
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : délai discounting (AUC à $40 000 et $200) comme proxy d'impulsivité trait ; niveau sujet ; relations non-linéaires accommodées par le GPR.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : régression par processus gaussien (GPR), estimée indépendamment pour chaque brainordinate ; validation croisée 10-fold tenant compte de la structure familiale ; coût ~ quelques secondes par localisation.

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : Z-score (NPM) Z = (y − ŷ)/√(σ²ij + σ²nj), combinant erreur, variance prédictive du point test et variance normative ; calculé par région ; déviations signées (positives/négatives) et absolues ; seuillage p < .05 corrigé FDR.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : (a) par région → localisation des régions déviantes par sujet (NPM ; aucune région déviante chez plus de 3 sujets) et détection d'atypies (22 sujets) ; (b) global par sujet → indice d'anomalie via valeurs extrêmes (moyenne tronquée 90% du top 1% des Z), associé à l'hyperactivité (r=.91 top 1% ; persiste : r=.22 à 20%), pas à l'inattention ; sert à stratifier les sujets à forte hyperactivité.

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : TDAH — spécificité pour la dimension hyperactivité (et non l'inattention) ; met en évidence une hétérogénéité mécanistique où un même symptôme provient soit de l'extrême d'un axe normal, soit de déviations idiosyncrasiques.

## Biomarqueur identifié ?
**Verdict : Candidat**

Article fondateur introduisant la modélisation normative (régression par processus gaussien) pour analyser l'hétérogénéité au niveau individuel, avec prédictions par sujet. Démonstration de preuve de concept dans une cohorte saine (N=491) reliant impulsivité-trait et activité de récompense : l'amplitude de déviation (outlier) relie a des symptômes TDAH spécifiques (hyperactivité, pas inattention). Cadre proposé avec preuve préliminaire, sans biomarqueur clinique validé (pas d'AUC diagnostique).

> « the degree of deviation (outlier magnitude) relates to specific attention-deficit/hyperactivity disorder symptoms (hyperactivity, but not inattention) on the basis of individualized patterns of abnormality »

## Mes réflexions
*(à compléter par moi)*
