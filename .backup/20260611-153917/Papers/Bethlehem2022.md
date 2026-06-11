---
id: Bethlehem2022
titre: Brain charts for the human lifespan
auteur_principal: Bethlehem, R. A. I.
annee: 2022
journal: Nature
doi: 10.1038/s41586-022-04554-y
date_ajout: 2026-06-03
statut: lu
theme:
  - "[[Mod. normative]]"
  - "[[Scores-méd. personnalisée]]"
  - "[[Biomarqueurs]]"
methode_cat:
  - "[[Stats classiques]]"
population:
  - "[[Les deux]]"
type_irm:
  - "[[Structurel]]"
interpretabilite: "[[Haute]]"
pertinence: 5
biomarqueur: "Simple"
methode_detail:
  - "[[GAMLSS]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[UK Biobank]]"
  - "[[ABCD]]"
  - "[[HCP]]"
  - "[[CamCAN]]"
  - "[[ADNI]]"
application:
  - "[[Neurodéveloppement]]"
  - "[[Vieillissement]]"
  - "[[Alzheimer]]"
  - "[[Schizophrénie]]"
  - "[[Autisme]]"
  - "[[TDAH]]"
niveau_score:
  - "[[Par région]]"
  - "[[Global par sujet]]"
usage_score:
  - "[[Localisation]]"
  - "[[Comparaison de groupes]]"
  - "[[Détection d'atypies]]"
  - "[[Association au phénotype]]"
  - "[[Stratification]]"
tags_libres: []
fichier_source: 
---
![[Bethlehem2022.png|697]]

## TL;DR
À partir de 123 984 IRM agrégées sur la vie entière, le papier établit des courbes de croissance cérébrale normatives (GAMLSS) et convertit chaque scan en centile âge/sexe — un brainscore standardisé d'atypicité, comparable entre troubles et entre âges.

## Contributions
1. Premières courbes de croissance cérébrale couvrant mi-gestation → 100 ans (123 984 IRM, >100 études). [Mod. normative]
2. Centile individuel standardisé par âge et sexe = score d'atypicité comparable trans-diagnostique. [Scores-méd. personnalisée]
3. Les centiles séparent significativement cas et témoins (AD > MCI > SCZ sur la CMD). [Biomarqueurs]
4. Nouveaux jalons (pic GMV 5,9 ans ; épaisseur corticale 1,7 an) et héritabilité des centiles accrue (+11,8 pts h²). [Mod. normative]
5. Outil ouvert brainchart.io pour scorer une nouvelle étude (≥100 scans) sans partage des données brutes. [Mod. normative]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Construit/valide les trajectoires de référence. |
| Méthode | Stats classiques | GAMLSS paramétrique, pas d'IA. |
| Population | Les deux | Témoins sains (référence) + cohortes pathologiques. |
| Type IRM | Structurel | Volumes, épaisseur, surface corticale (T1). |
| Interprétabilité | Haute | Centiles type courbes de croissance. |
| Pertinence (1–5) | 5 | Papier fondateur du projet. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : 4 volumes cérébraux (GMV, WMV, sGMV, ventricules/CSF) + global (volume cérébral total, épaisseur corticale moyenne, surface) + régional (34 aires Desikan-Killiany) ; niveau global et régional ; 123 984 scans / 101 457 sujets / >100 études (115 j post-conception → 100 ans).
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge (log) et sexe (modèles stratifiés), version logicielle (5 catégories) en effet fixe, étude en effet aléatoire (μ, σ) ; non-linéarité via polynômes fractionnaires.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : GAMLSS avec distribution gamma généralisée ; estimation de la médiane et de la variance par sexe ; validation par bootstrap, validation croisée et leave-one-study-out (out-of-sample fiable pour N>100).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : centiles (rang quantile relatif à la trajectoire âge×sexe) ; CMD = distance de Mahalanobis combinant les 4 phénotypes globaux ; direction = centile signé (0–100 %) ; seuillage = non rapporté (pas de seuil binaire défini).

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à :
- Par région → Localisation : hétérochronie corticale, gradient sensori-associatif, pics régionaux 2–10 ans.
- Global par sujet → Comparaison de groupes (cas-témoins, AD d=0,88), Détection d'atypies (CMD ; SCZ 3ᵉ), Association au phénotype (âge gestationnel et poids de naissance p<2e-16 ; héritabilité +11,8 pts), Stratification (clustering → 3 groupes : neurodégén., humeur/anxiété, neurodével.).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : comparaisons trans-diagnostiques (AD, MCI, SCZ, ASD, ADHD, ANX, MDD, BD) ; suivi de la transition MCI → AD via la stabilité longitudinale des centiles ; outil ouvert de scoring out-of-sample. Aucun diagnostic individuel n'est revendiqué (objectif futur).

## Biomarqueur identifié ?
**Verdict : Simple**

Charts normatifs du cerveau (GAMLSS, 123 984 scans) fournissant des scores centiles individualisés. Différences cas-témoins hautement significatives sur de multiples troubles, avec une métrique directe (centile du volume de matière grise) discriminant le plus fortement la maladie d'Alzheimer (taille d'effet d=0,88). Marqueur direct/universel avec résultat quantitatif réalisé ; les auteurs ne revendiquent toutefois pas encore de diagnostic individuel.

> « Alzheimer's disease showed the greatest overall difference, with a maximum difference localized to grey matter volume in biologically female patients (median centile score = 14%, 36 percentage points difference from CN median, corresponding to Cohen's d = 0.88). »

## Mes réflexions
*(à compléter par moi)*
