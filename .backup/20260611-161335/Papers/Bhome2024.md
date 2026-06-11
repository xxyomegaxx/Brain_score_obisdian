---
id: Bhome2024
titre: "A neuroimaging measure to capture heterogeneous patterns of atrophy in Parkinson's disease and dementia with Lewy bodies"
auteur_principal: R. Bhome
annee: 2024
journal: "NeuroImage: Clinical"
doi: 10.1016/j.nicl.2024.103596
date_ajout: 2026-06-03
statut: lu
theme:
  - "[[Biomarqueurs]]"
  - "[[Scores-méd. personnalisée]]"
  - "[[Mod. normative]]"
methode_cat:
  - "[[Stats classiques]]"
population:
  - "[[Les deux]]"
type_irm:
  - "[[Structurel]]"
interpretabilite: "[[Haute]]"
pertinence: 5
biomarqueur: "Computationnel"
methode_detail:
  - "[[Warped BLR]]"
  - "[[HBR]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[NACC]]"
  - "[[Vision in PD (UCL)]]"
application:
  - "[[Parkinson]]"
  - "[[Démence à corps de Lewy]]"
niveau_score:
  - "[[Par région]]"
  - "[[Global par sujet]]"
usage_score:
  - "[[Localisation]]"
  - "[[Comparaison de groupes]]"
  - "[[Association au phénotype]]"
tags_libres: []
fichier_source: 
---
![[Bhome2024.png]]
## TL;DR
Un score individuel d'imagerie — le « total outlier count » dérivé d'un modèle normatif — résume l'atrophie hétérogène de 169 régions en un seul indice qui sépare DLB du Parkinson, distingue les Parkinson à risque de démence, et corrèle avec la cognition, là où le GLM de groupe échoue.

## Contributions
1. La modélisation normative capte une atrophie hétérogène que le GLM de groupe rate. [Mod. normative]
2. Le total outlier count sépare DLB vs PD et performeurs visuels faibles vs élevés en PD. [Biomarqueurs]
3. Un score individuel résume 169 régions, calculable via pipelines T1w gratuits. [Scores-méd. personnalisée]
4. Score élevé ↔ cognition plus faible (DLB : MoCA/composite ; PD : visuoperception/Hooper). [Biomarqueurs]
5. La distance de Hamming quantifie la dissimilarité inter-individuelle des outliers. [Mod. normative]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Biomarqueurs | Évalue une mesure distinguant populations et associée à la clinique |
| Méthode | Stats classiques | Warped BLR bayésien + tests Mann-Whitney/régressions/FDR |
| Population | Les deux | Patients PD/DLB vs cohorte de référence saine + contrôles |
| Type IRM | Structurel | T1w MPRAGE → épaisseur corticale + volumes sous-corticaux |
| Interprétabilité | Haute | Z-scores par région, seuils explicites, indice agrégé lisible |
| Pertinence (1–5) | 5 | Score normatif individuel + biomarqueurs sur IRM structurelle |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : épaisseur corticale (parcellation Destrieux, 148 régions) + volumes sous-corticaux (21 régions, aseg) ; niveau par région ; 169 régions au total.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge et sexe, avec correction des différences de site ; effets non-linéaires modélisés par warping (likelihood warping).

## Étape 2 — Modélisation normative
Méthode · granularité · validation : Warped Bayesian Linear Regression (modèle de référence de Rutherford 2022, n = 58 836, 82 sites) recalibré aux données d'étude par apprentissage par transfert hiérarchique bayésien (Kia 2022) ; granularité par région (169) ; pipeline PCNToolkit v0.20. Validation interne du modèle dans cette étude : non précisé (modèle pré-entraîné réutilisé).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : z-score par région ; direction signée, seul l'extrême bas (atrophie) considéré ; outlier si z < −1,96 (seuil alternatif −1,282 testé) ; agrégation = total outlier count (somme des outliers sur 169 régions).

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : (a) par région → localisation (cartes corticales ggseg) et comparaison de groupes régionale (Mann-Whitney + FDR ; distance de Hamming pour la dissimilarité) ; (b) global par sujet → comparaison de groupes (PD vs DLB : moy. 3,6 vs 8,7 ; performeurs visuels faibles vs élevés) et association au phénotype (MoCA, score cognitif composite, test de Hooper, corrigés âge/sexe).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : mesure de sévérité dans PD et DLB ; stratification du risque de démence en PD (performeurs visuels faibles) ; potentiel pronostique individualisé évoqué (non testé longitudinalement ici).

## Biomarqueur identifié ?
**Verdict : Computationnel**

Modélisation normative neuroanatomique appliquée à la maladie de Parkinson et à la démence à corps de Lewy : agrégation par sujet du nombre de régions aberrantes (z<-1,96 sur 169 régions), sans région universelle (atrophie hétérogène). Cet indice de déviation personnalisé discrimine des sous-groupes cliniques (mauvais vs bons performeurs visuels en MP ; DCL vs MP) et est associé à la cognition. Résultat discriminatif réalisé via une carte de déviation individualisée, d'où Computationnel. (Texte intégral OA mais non extractible ici — classification fondée sur le résumé structuré, aucun chiffre inventé.)

> « We found greater total outlier counts in PD poor visual performers, compared to high; and in DLB versus PD. Outlier counts were associated with global cognition in DLB, and visuoperception in PD. »

## Mes réflexions
*(à compléter par moi)*
