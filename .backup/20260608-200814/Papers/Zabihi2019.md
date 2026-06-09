---
id: Zabihi2019
titre: "Dissecting the Heterogeneous Cortical Anatomy of Autism Spectrum Disorder Using Normative Models"
auteur_principal: "Mariam Zabihi"
annee: 2019
journal: "Biological Psychiatry: Cognitive Neuroscience and Neuroimaging"
doi: "10.1016/j.bpsc.2018.11.013"
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
pertinence: 4
methode_detail:
  - "[[GPR]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[EU-AIMS LEAP]]"
application:
  - "[[Autisme]]"
  - "[[Neurodéveloppement]]"
niveau_score:
  - "[[Par région]]"
  - "[[Global par sujet]]"
usage_score:
  - "[[Localisation]]"
  - "[[Comparaison de groupes]]"
  - "[[Détection d'atypies]]"
  - "[[Association au phénotype]]"
tags_libres: []
fichier_source: "extrospection.eu (PDF Biological Psychiatry CNNI)"
---
![[Zabihi2019.svg|649]]
## TL;DR
Plutôt que de comparer « l'autiste moyen » à des témoins, un modèle normatif vertexwise de l'épaisseur corticale révèle que chaque personne autiste s'écarte du patron typique de façon très individualisée et dispersée — des empreintes neurobiologiques propres à chacun, masquées par l'approche cas-témoins.

## Contributions
1. Applique la modélisation normative (GPR vertexwise) à l'anatomie corticale de l'autisme, au niveau de l'individu. [Mod. normative]
2. Montre que les déviations individuelles sont très hétérogènes et faiblement recouvrantes, là où les différences cas-témoins de groupe sont quasi nulles. [Biomarqueurs]
3. Résume la déviation de chaque sujet par une statistique des valeurs extrêmes (déviation maximale). [Scores-méd. personnalisée]
4. Relie la déviation à la sévérité clinique (comportements répétitifs survivant la correction FDR). [Biomarqueurs]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Construit/valide un modèle normatif de l'épaisseur corticale. |
| Méthode | Stats classiques | Régression par processus gaussien (GPR) bayésienne. |
| Population | Les deux | Modèle estimé sur 206 TD, testé sur 321 sujets ASD. |
| Type IRM | Structurel | T1 ; épaisseur corticale et surface (FreeSurfer). |
| Interprétabilité | Haute | Z-scores par vertex, analogie des courbes de croissance. |
| Pertinence (1–5) | 4 | Référence fondatrice pour les déviations individuelles en neurodéveloppement. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : épaisseur corticale (et surface) par vertex sur la surface corticale FreeSurfer (v5.3) ; niveau vertexwise.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge et sexe ; non-linéarités captées par le noyau du GPR.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : GPR séparé par vertex, entraîné sur les 206 TD seulement (pour éviter l'enrichissement en ASD) ; validation par 10-fold CV puis ré-entraînement sur tous les TD avant prédiction sur les ASD.

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : carte de probabilité normative (NPM) = Z-score par vertex vs patron typique ; seuillage FDR p<.05 par sujet ; déviations positives et négatives séparées ; score résumé par sujet = statistique des valeurs extrêmes (moyenne tronquée des 1% top déviations absolues).

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : (i) **Par région** — cartes Z seuillées et carte de recouvrement (localisation), GLM cas-témoins en comparaison ; (ii) **Global par sujet** — score de déviation extrême (détection d'atypies), corrélé (Spearman, FDR) à la sévérité ADI-R / ADOS-2.

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : empreintes neurobiologiques individualisées en ASD orientant vers la médecine de précision ; déviation corrélée à la sévérité des comportements répétitifs et de la communication sociale.

## Mes réflexions
*(à compléter par moi)*
