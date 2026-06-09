---
id: Wiegert2025
titre: "Breaking the Norm: Population-Scale Normative Modeling of Brain Structure in Depression and Anxiety"
auteur_principal: "Julius Wiegert"
annee: 2025
journal: "medRxiv"
doi: "10.1101/2025.09.26.25336528"
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
  - "[[NAKO]]"
  - "[[UK Biobank]]"
application:
  - "[[Dépression]]"
  - "[[Anxiété]]"
  - "[[Trouble de l'usage d'alcool]]"
niveau_score:
  - "[[Global par sujet]]"
usage_score:
  - "[[Association au phénotype]]"
  - "[[Comparaison de groupes]]"
  - "[[Prédiction]]"
tags_libres: ["deep learning", "espace latent", "magnitude+direction", "scores polygéniques"]
fichier_source: "Wiegert et al. (corresp. E. Schwarz), medRxiv 2025.09.26.25336528 (PDF/texte intégral)"
---
![[Wiegert2025.svg|649]]

## TL;DR
Modèle normatif profond qui encode l'IRM structurelle cerveau-entier dans un espace latent non-linéaire (256 dimensions) : la déviation par rapport à la norme (apprise sur les sujets sains/peu symptomatiques) est quantifiée en **magnitude ET direction**. La magnitude croît avec la sévérité (PHQ-9, GAD-7), les directions séparent les tendances humeur-anxiété et usage d'alcool, et combinée aux scores polygéniques, elle améliore la classification (découverte NAKO ~29k → validation UK Biobank ~25k).

## Contributions
1. Cadre normatif profond cerveau-entier (espace latent 256D) modélisant la déviation en magnitude **et** direction. [Mod. normative]
2. Magnitude de déviation croissant avec la sévérité des symptômes (OR croissant) ; généralise de NAKO à l'UK Biobank. [Biomarqueurs]
3. Directions séparant les tendances humeur-anxiété vs usage d'alcool (groupe contrôle positif AUD).
4. Combiner déviations + scores polygéniques améliore la classification (dépression, anxiété) — apports complémentaires imagerie/génétique.

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Cadre normatif profond cerveau-entier, déviation magnitude+direction. |
| Méthode | IA | Autoencodeur profond encodant l'IRM voxel-wise en espace latent. |
| Population | Les deux | Référence saine/peu symptomatique + groupes symptomatiques (MDD, GAD, AUD). |
| Type IRM | Structurel | IRM structurelle cerveau-entier (voxel-wise). |
| Interprétabilité | Moyenne | Espace latent profond ; déviation interprétée en magnitude/direction. |
| Pertinence (1–5) | 4 | Modélisation normative profonde à l'échelle populationnelle, dépression/anxiété. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : IRM structurelle cerveau-entier voxel-wise, encodée dans un espace latent non-linéaire de 256 dimensions ; niveau sujet (cerveau-entier).
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge, sexe ; norme apprise sur les sujets sains/peu symptomatiques ; ajustement âge, âge², sexe et interaction sexe×âge dans les analyses.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : autoencodeur profond (apprentissage de représentation) entraîné sur la sous-population saine/peu symptomatique (PHQ-9 < 5, GAD-7 < 5, AUDIT-C < 8). Découverte sur NAKO (German National Cohort, N ≈ 29–30 000), validation externe sur UK Biobank (N ≈ 25 000).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : déviation = distance au référentiel normatif dans l'espace latent, quantifiée en **magnitude** et **direction** ; au niveau du sujet (cerveau-entier). La fraction de déviation dépassant la variabilité des contrôles sains (« shift ») est calculée par groupe.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : niveau **global par sujet**. Finalités : (a) **association au phénotype** — magnitude croissant avec la sévérité (OR croissant par bins de déviation) ; (b) **comparaison de groupes** — symptomatiques vs contrôles, et directions humeur-anxiété vs usage d'alcool ; (c) **prédiction** — classification de l'appartenance au groupe symptomatique, améliorée en combinant avec les scores polygéniques.

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : dépression (MDD, PHQ-9), anxiété (GAD, GAD-7) et trouble de l'usage d'alcool (AUDIT-C, contrôle positif) ; les déviations structurelles reflètent une variation continue et individuelle des symptômes affectifs et comportementaux.

## Mes réflexions
*(à compléter par moi)*
