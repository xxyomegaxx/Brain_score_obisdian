---
id: Rutherford2022b
titre: "The normative modeling framework for computational psychiatry"
auteur_principal: "Saige Rutherford"
annee: 2022
journal: "Nature Protocols"
doi: "10.1038/s41596-022-00696-5"
date_ajout: 2026-06-08
statut: lu
theme:
  - "[[Mod. normative]]"
  - "[[Biomarqueurs]]"
  - "[[Scores-méd. personnalisée]]"
methode_cat:
  - "[[Stats classiques]]"
population:
  - "[[Les deux]]"
type_irm:
  - "[[Structurel]]"
interpretabilite: "[[Haute]]"
pertinence: 5
biomarqueur: "Non"
methode_detail:
  - "[[BLR]]"
  - "[[Warped BLR]]"
  - "[[HBR]]"
  - "[[GPR]]"
modalite_detail:
  - "[[sMRI]]"
niveau_score:
  - "[[Par région]]"
  - "[[Global par sujet]]"
usage_score:
  - "[[Localisation]]"
  - "[[Comparaison de groupes]]"
  - "[[Stratification]]"
  - "[[Prédiction]]"
  - "[[Détection d'atypies]]"
tags_libres: []
fichier_source: "Nature Protocols 17:1711-1734 (PDF Amsterdam UMC)"
---
![[Rutherford2022b.svg|649]]
## TL;DR
Un protocole pas-à-pas pour faire de la modélisation normative avec le PCNtoolkit : du choix des données de référence à l'estimation du modèle (BLR/Warped BLR/HBR), jusqu'aux analyses en aval (stratification, sous-typage, prédiction comportementale) — pour dépasser le cadre cas-témoins en psychiatrie computationnelle.

## Contributions
1. Distille la méthode de modélisation normative en un protocole reproductible end-to-end via le PCNtoolkit. [Mod. normative]
2. Explique les choix de modélisation (référence, covariables, algorithme) et l'usage de HBR pour des scores Z agnostiques au site sur données multisites. [Mod. normative]
3. Démontre les analyses en aval : stratification d'individus à haut risque, sous-typage, prédiction comportementale. [Scores-méd. personnalisée]
4. Positionne la modélisation normative face aux approches cas-témoins et aux modèles prédictifs cerveau-comportement. [Biomarqueurs]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Protocole dédié à l'estimation et à l'usage de modèles normatifs. |
| Méthode | Stats classiques | BLR, Warped BLR, HBR, GPR (régressions bayésiennes/statistiques). |
| Population | Les deux | Référence = neurotypiques ; jeu test = témoins + groupes patients. |
| Type IRM | Structurel | Démo sur épaisseur corticale et volumes sous-corticaux (FreeSurfer). |
| Interprétabilité | Haute | Scores Z, brain score prédit et variance, cartes de déviation. |
| Pertinence (1–5) | 5 | Protocole de référence et boîte à outils centrale du domaine. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : épaisseur corticale et volumes sous-corticaux (sMRI/FreeSurfer) dans la démonstration ; niveau ROI ou vertex/voxel selon le choix.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge, sexe, site ; option indice de qualité (déplacement, nombre d'Euler) ; effets non-linéaires via warping/splines selon l'algorithme.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : PCNtoolkit ; algorithmes BLR, Warped BLR, HBR, GPR ; HBR estime des effets de site hiérarchiques produisant des scores Z agnostiques au site ; split train/test (≈70/30 ou 80/20) stratifié par site pour évaluer la généralisation hors-échantillon. Tailles d'échantillon précises de la démo : non précisé ici.

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : sorties = brain score prédit, variance prédictive (modèle + bruit) et score de déviation Z par sujet ; cartes de déviation par région ; déviations positives/négatives ; résumé par statistiques des valeurs extrêmes (compte de déviations extrêmes).

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : (i) **Par région** — cartes de déviation, t-tests cas-témoins sur ces cartes (localisation, comparaison de groupes) ; (ii) **Global par sujet** — compte de déviations extrêmes par sujet et par groupe (détection d'atypies), puis stratification d'individus à haut risque, sous-typage et prédiction comportementale en aval.

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : cadre transdiagnostique pour la psychiatrie computationnelle ; dépasse les comparaisons cas-témoins face à l'hétérogénéité, et soutient stratification et prédiction au niveau individuel.

## Biomarqueur identifié ?
**Verdict : Non**

Protocole standardise (Nature Protocols) guidant pas a pas l'analyse de modelisation normative avec le PCNtoolkit. C'est un tutoriel methodologique ; aucune decouverte ni resultat discriminatif quantitatif n'est realise dans ce papier.

> « Here we define a standardized protocol to guide users through, from start to finish, normative modeling analysis using the Predictive Clinical Neuroscience toolkit »

## Mes réflexions
*(à compléter par moi)*
