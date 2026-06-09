---
id: Bozek2023
titre: "Normative models for neuroimaging markers: impact of model selection, sample size and evaluation criteria"
auteur_principal: "Jelena Bozek"
annee: 2023
journal: "NeuroImage"
doi: "10.1016/j.neuroimage.2023.119864"
date_ajout: 2026-06-07
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
  - "[[Centiles]]"
modalite_detail:
  - "[[sMRI]]"
dataset: []
application: []
niveau_score:
  - "[[Par région]]"
usage_score: []
tags_libres: ["simulation", "taille d'échantillon", "biais-variance", "percentiles", "hippocampe", "extrapolation"]
fichier_source: "Bozek, Griffanti, Lau & Jenkinson, NeuroImage 268:119864 (2023)"
---
![[Bozek2023.svg|649]]
## TL;DR
Étude de **simulation** qui évalue, du point de vue clinique, la fiabilité de l'estimation des **courbes de percentiles** normatives en fonction de la **taille d'échantillon** et du choix de modèle. À partir de distributions « vérité-terrain » plausibles du volume hippocampique (45–80 ans), des échantillons de 50 à 50 000 points sont simulés et réajustés ; en se concentrant sur les **percentiles externes** (1ᵉʳ, 5ᵉ, 10ᵉ) — les plus pertinents cliniquement — les auteurs montrent que la variance diminue avec n mais que le **biais reste élevé**, et qu'il faut des **milliers** de points pour estimer correctement les percentiles extrêmes, surtout aux extrémités de la plage d'âge où il faut éviter toute extrapolation.

## Contributions
1. Cadre de simulation à vérité-terrain connue pour quantifier biais ET variance de l'estimation des percentiles normatifs, plutôt qu'une seule métrique d'erreur. [Mod. normative]
2. Quantification de l'effet de la taille d'échantillon : la variance chute avec n, mais le biais ne s'améliore que modestement, même à grands n. [Mod. normative]
3. Les modèles flexibles (non-linéaires) sont préférables sur toute la gamme de tailles, surtout quand la vérité-terrain est non-linéaire. [Mod. normative]
4. Constat pratique : des milliers de points sont nécessaires pour capter les percentiles externes, et l'incertitude explose aux extrémités de la plage d'âge — l'extrapolation doit être évitée. [Mod. normative]
5. Recommandation méthodologique + code public pour guider l'évaluation des modèles normatifs (biais et variance). [Mod. normative]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Étude entièrement consacrée à l'estimation/évaluation des modèles normatifs. |
| Méthode | Stats classiques | Ajustement de courbes de percentiles (GAMLSS), pas d'apprentissage profond. |
| Population | Saine | Distributions simulées de sujets sains ; aucun patient. |
| Type IRM | Structurel | Marqueur = volume hippocampique (mesure structurelle). |
| Interprétabilité | Haute | Courbes de percentiles paramétriques directement interprétables. |
| Pertinence (1–5) | 4 | Guide pratique sur taille d'échantillon et évaluation, utile à tout modèle normatif. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : volume hippocampique **simulé** (marqueur unique) ; niveau région/marqueur ; échantillons simulés de 50 à 50 000 points, répétés plusieurs fois pour estimer la variabilité.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge (plage 45–80 ans) ; distributions « vérité-terrain » plausibles avec formes linéaires et non-linéaires ; aucune donnée IRM réelle (étude de simulation).

## Étape 2 — Modélisation normative
Méthode · granularité · validation : ajustement de **modèles de courbes de percentiles** linéaires et non-linéaires (cadre GAMLSS, code public) sur chaque échantillon simulé. Validation par comparaison à la vérité-terrain connue, en répétant les simulations pour estimer la variabilité inter-répétitions, avec focus sur les percentiles externes (1ᵉʳ/5ᵉ/10ᵉ).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : l'objet d'étude est l'**estimation des centiles** eux-mêmes (position dans la norme), et non le calcul d'un z-score sur des sujets réels. Le compromis biais-variance des percentiles estimés est quantifié ; aucun seuillage clinique appliqué.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : **par région** (marqueur hippocampique unique). Finalité clinique : **non rapportée** — il s'agit d'une étude méthodologique de simulation qui mesure la précision d'estimation des percentiles, sans application des déviations à une cohorte de patients.

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : aucune application clinique réalisée (étude de simulation). Portée pratique : recommandations sur la taille d'échantillon minimale et l'évaluation (biais + variance) pour quiconque construit ou utilise des modèles normatifs ; mise en garde contre l'extrapolation aux extrémités de la plage d'âge.

## Mes réflexions
*(à compléter par moi)*
