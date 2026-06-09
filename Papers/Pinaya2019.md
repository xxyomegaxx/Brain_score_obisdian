---
id: Pinaya2019
titre: "Using deep autoencoders to identify abnormal brain structural patterns in neuropsychiatric disorders: A large-scale multi-sample study"
auteur_principal: "Walter H. L. Pinaya"
annee: 2019
journal: "Human Brain Mapping"
doi: "10.1002/hbm.24423"
date_ajout: 2026-06-09
statut: lu
theme:
  - "[[Mod. normative]]"
  - "[[Biomarqueurs]]"
methode_cat:
  - "[[IA]]"
population:
  - "[[Les deux]]"
type_irm:
  - "[[Structurel]]"
interpretabilite: "[[Moyenne]]"
pertinence: 4
methode_detail:
  - "[[AE normatif]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[NUSDAST]]"
application:
  - "[[Schizophrénie]]"
  - "[[Autisme]]"
niveau_score:
  - "[[Global par sujet]]"
  - "[[Par région]]"
usage_score:
  - "[[Détection d'atypies]]"
  - "[[Comparaison de groupes]]"
tags_libres: ["deep learning", "erreur de reconstruction", "multi-échantillons"]
fichier_source: "Pinaya, Mechelli & Sato, Human Brain Mapping 2019 (PDF déposé)"
---
![[Pinaya2019.svg|649]]

## TL;DR
Première application des autoencodeurs profonds à la modélisation normative : entraîné sur des contrôles sains multi-échantillons, l'erreur de reconstruction sert de métrique de déviation pour détecter des patterns structurels anormaux en schizophrénie et en autisme.

## Contributions
1. Autoencodeur profond (parcimonieux) entraîné sur des contrôles sains ; l'erreur de reconstruction = métrique de déviation individuelle. [Mod. normative]
2. Étude multi-échantillons à grande échelle (schizophrénie, autisme). [Biomarqueurs]
3. Déviation plus élevée chez les patients que chez les contrôles ; erreur de reconstruction décomposable par région.

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Modèle normatif par autoencodeur, métrique de déviation individuelle. |
| Méthode | IA | Autoencodeur profond (apprentissage profond). |
| Population | Les deux | Contrôles sains (entraînement) + patients SCZ/ASD. |
| Type IRM | Structurel | Épaisseur corticale + volumes (FreeSurfer 5.3). |
| Interprétabilité | Moyenne | Modèle profond ; déviation globale moins directement interprétable. |
| Pertinence (1–5) | 4 | Référence fondatrice du normatif par deep learning. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : mesures morphologiques structurelles (épaisseur corticale et volumes sous-corticaux, FreeSurfer 5.3) ; niveau région ; par sujet.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge et sexe (également prédits par le modèle) ; niveau sujet.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : autoencodeur profond parcimonieux entraîné uniquement sur des contrôles sains (multi-échantillons) ; la métrique de déviation est l'erreur de reconstruction du modèle. Appliqué à plusieurs échantillons cliniques (schizophrénie — dont NUSDAST ; autisme).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : déviation = erreur de reconstruction ; niveau global par sujet et décomposable par région ; plus élevée chez les patients que chez les contrôles.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : niveaux **global par sujet** et **par région**. Finalités : (a) **détection d'atypies** via la métrique de déviation ; (b) **comparaison de groupes** patients vs contrôles (déviation plus élevée chez les patients).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : schizophrénie et autisme — identification de patterns structurels anormaux au niveau individuel.

## Mes réflexions
*(à compléter par moi)*
