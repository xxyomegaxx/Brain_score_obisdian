---
id: LawryAguila2022
titre: Conditional VAEs for Confound Removal and Normative Modelling of Neurodegenerative Diseases
auteur_principal: Ana Lawry Aguila
annee: 2022
journal: MICCAI 2022 (LNCS 13431, pp. 430–440)
doi: 10.1007/978-3-031-16431-6_41
date_ajout: 2026-06-03
statut: lu
theme:
  - "[[Mod. normative]]"
  - "[[Biomarqueurs]]"
  - "[[Scores-méd. personnalisée]]"
methode_cat:
  - "[[IA]]"
population:
  - "[[Les deux]]"
type_irm:
  - "[[Structurel]]"
interpretabilite: "[[Moyenne]]"
pertinence: 5
biomarqueur: "Candidat"
methode_detail:
  - "[[cVAE]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[UK Biobank]]"
  - "[[ADNI]]"
application:
  - "[[Alzheimer]]"
  - "[[Sclérose en plaques]]"
  - "[[Trouble bipolaire]]"
niveau_score:
  - "[[Global par sujet]]"
  - "[[Par région]]"
usage_score:
  - "[[Comparaison de groupes]]"
  - "[[Association au phénotype]]"
  - "[[Localisation]]"
tags_libres: []
fichier_source: MICCAI_paper_AnaLawryAguila.pdf
---
![[LawryAguila2022.png]]

## TL;DR
Un cVAE normatif entraîné sur cerveaux sains et conditionné sur les confondants : sa métrique de déviation latente (D_L) sépare mieux les cohortes pathologiques que D_MSE et que la GPR, tout en localisant des biomarqueurs (amygdale, hippocampe).

## Contributions
1. Entraîne un cVAE sur IRM structurelles de cerveaux sains en intégrant directement les confondants (âge, ICV) au lieu de les retirer en amont. [Mod. normative]
2. Propose la déviation latente D_L, qui sépare mieux malades/témoins que D_MSE et que la GPR, à moindre coût de calcul. [Scores-méd. personnalisée]
3. Montre que la déviation latente suit la sévérité de la maladie (EMCI < LMCI < AD dans ADNI). [Scores-méd. personnalisée]
4. Ramène les déviations latentes à 43 régions (HC vs LMCI) / 63 régions (HC vs AD), retrouvant l'atrophie amygdale-hippocampe. [Biomarqueurs]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Construit un modèle normatif cVAE du cerveau sain |
| Méthode | IA | VAE conditionnel, apprentissage profond non supervisé |
| Population | Les deux | Entraîné sur sains (UKB), testé sur pathologiques (UKB, ADNI) |
| Type IRM | Structurel | Volumes régionaux issus d'IRM structurelle |
| Interprétabilité | Moyenne | Modèle profond, mais déviations re-projetées sur régions |
| Pertinence (1–5) | 5 | Modèle normatif + score de déviation + biomarqueurs |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : volumes de régions cérébrales (IRM structurelle), au niveau du sujet, standardisés par la moyenne/écart-type des régions du UK Biobank ; sujets âgés de 47–73 ans, ICV 0,95–2,31 ; nombre exact de régions non rapporté.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge et ICV, découpés en 10 bins quantiles encodés one-hot et fournis comme variables conditionnelles ; les effets non-linéaires sont capturés par le réseau profond.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : cVAE conditionné sur les confondants ; encodeur = couche linéaire de 40 nœuds + ReLU puis couches moyenne/log-variance, espace latent de dimension 10 ; décodeur = 2 couches linéaires séparées par ReLU ; entraîné sur la cohorte de sujets sains du UK Biobank ; sélection de paramètres (dimensions latentes 5/10/15/20, couches 20/40/60/80) en surveillant la séparation CN vs AD ; la Table 1 montre que le cVAE réduit fortement l'association latents↔covariables vs le VAE simple.

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : D_L = déviation dans l'espace latent (tenant compte de l'incertitude des vecteurs latents), D_MSE = déviation par erreur de reconstruction, D_LS = déviation par vecteur latent ; magnitude de déviation ; significativité des séparations par régression logistique, et test de Welch par région avec seuil Bonferroni p=0,00061 pour le retour aux régions.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : (Global par sujet) D_L → comparaison de groupes HC vs SEP/bipolaire (UKB) et HC vs EMCI/LMCI/AD (ADNI), avec p-values plus significatives que D_MSE et GPR (ex. ADNI HC vs AD : D_L p=2,67E-08 vs D_MSE p=0,0176 vs GPR p=1,67E-07) ; association au phénotype via le gradient de sévérité. (Par région) D_LS sur les vecteurs latents 5 et 6, décodés en fixant le reste à zéro → localisation : 43 régions significatives (HC vs LMCI), 63 (HC vs AD).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : détection et stratification de la maladie d'Alzheimer le long du continuum MCI → AD ; distinction de la sclérose en plaques et du trouble bipolaire vs témoins ; biomarqueurs structuraux convergents (atrophie amygdale et hippocampe), cohérents avec la littérature MCI/AD.

## Biomarqueur identifié ?
**Verdict : Candidat**

Article méthodologique (MICCAI) proposant un cVAE pour retirer les confonds et une metrique de deviation latente personnalisee. Preuve de concept sur l'Alzheimer : le modèle identifie les cohortes malades comme déviations reflétant la sévérité, mais sans métrique de discrimination quantitative validée rapportée dans le résumé. Métrique proposée à preuve préliminaire -> Candidat.

> « We propose a latent deviation metric and use it to quantify deviations in individual subjects with neurological disorders [...] Our model is able to identify these disease cohorts as deviations from the normal brain in such a way that reflect disease severity. »

## Mes réflexions
*(à compléter par moi)*
