---
id: Kumar2023
titre: "Subcortical brain alterations in carriers of genomic copy number variants"
auteur_principal: "Kuldeep Kumar (co-premier auteur : Claudia Modenato)"
annee: 2023
journal: American Journal of Psychiatry
doi: 10.1176/appi.ajp.20220304
date_ajout: 2026-06-03
statut: lu
theme:
  - "[[Biomarqueurs]]"
  - "[[Mod. normative]]"
methode_cat:
  - "[[Hybride]]"
population:
  - "[[Les deux]]"
type_irm:
  - "[[Structurel]]"
interpretabilite: "[[Haute]]"
pertinence: 5
biomarqueur: "Computationnel"
methode_detail:
  - "[[GPR]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[ENIGMA]]"
  - "[[UK Biobank]]"
  - "[[Simons Searchlight]]"
application:
  - "[[Autisme]]"
  - "[[Schizophrénie]]"
  - "[[Neurodéveloppement]]"
niveau_score:
  - "[[Par région]]"
usage_score:
  - "[[Localisation]]"
  - "[[Comparaison de groupes]]"
  - "[[Association au phénotype]]"
tags_libres: []
fichier_source: non précisé
---
![[Kumar2023.png]]
## TL;DR
La modélisation normative appliquée à 11 CNV montre que la sévérité des altérations sous-corticales suit le risque génétique de maladie, et qu'une dimension latente commune (ganglions de la base ↔ système limbique) sous-tend la pléiotropie partagée entre CNV et troubles psychiatriques.

## Contributions
1. La modélisation normative (GPR) sur la plus grande base IRM de 11 CNV montre que 9/11 variants altèrent le volume sous-cortical. [Biomarqueurs]
2. L'analyse de forme vertex révèle des altérations sous-régionales (caudé, hippocampe) invisibles au volume global. [Biomarqueurs]
3. La taille d'effet des CNV sur le cerveau est corrélée à leur effet sur le QI et au risque ASD/SZ. [Mod. normative]
4. Une dimension latente commune (ganglions de la base vs limbique) relie CNV et NPD et éclaire la pléiotropie. [Biomarqueurs]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Biomarqueurs | Régions/formes sous-corticales distinguant porteurs de CNV et NPD |
| Méthode | Hybride | GPR pour les W-scores, puis régression/PCA/clustering classiques |
| Population | Les deux | Modèle normatif sur contrôles sains, appliqué aux porteurs |
| Type IRM | Structurel | T1 : volumes et formes (épaisseur, surface) |
| Interprétabilité | Haute | Cohen's d, W-scores et loadings PCA directement lisibles |
| Pertinence (1–5) | 5 | Même équipe ; normatif + biomarqueurs sous-corticaux, cœur du projet |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : volumes de 7 structures sous-corticales bilatérales + ICV, et formes vertex (épaisseur = distance radiale, surface = log du déterminant jacobien) ; niveaux structure et vertex ; ≈ 27 000 vertices par carte.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge (6–80 ans), sexe, site, ICV ; effets non-linéaires de l'âge modélisés par processus gaussiens (comparés à un modèle linéaire).

## Étape 2 — Modélisation normative
Méthode · granularité · validation : GPR ajustée sur 782 contrôles (covariables âge, sexe, site, ICV) ; granularité par structure et par vertex ; validation par comparaison GP vs linéaire et analyses de sensibilité (diagnostic, site, latéralité), concordance r = 0,93 avec un échantillon antérieur plus large (22q11.2).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : W-score (Z-score GPR par rapport à la moyenne et l'écart-type des contrôles), puis Cohen's d cas-contrôle calculé par CNV/NPD ; signé (hausse et baisse) ; seuil FDR q < 0,05.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : niveau par région (structure + vertex, top décile des d) ; localisation des altérations sous-régionales ; comparaison de groupes (11 CNV vs contrôles, puis CNV vs 6 NPD via corrélations, clustering, PCA — PC1/PC2 expliquant 45 % et 28 % de la variance) ; association au phénotype (d corrélés au QI r = 0,66–0,75 et au risque ASD/SZ r = 0,69–0,89).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : éclaire la pléiotropie des CNV (pourquoi tous augmentent le risque d'ASD et/ou SZ) ; dimension latente partagée (axe ganglions de la base ↔ système limbique) entre CNV et troubles psychiatriques (ASD, SZ, BD, MDD, OCD, ADHD).

## Biomarqueur identifié ?
**Verdict : Computationnel**

Modèle normatif (GPR, W-scores) appliqué à 11 CNV : les altérations sous-corticales sont spécifiques à chaque CNV et hétérogènes (effets opposés ganglions de la base vs limbique), sans région universelle, et sont intégrées en une dimension latente multivariée commune. Résultat quantitatif réalisé : 9/11 CNV altèrent le volume d'au moins une structure sous-corticale, et les tailles d'effet cérébrales corrèlent avec les effets sur la cognition et le risque d'ASD/SZ. Profil multivarié personnalisé, donc biomarqueur computationnel.

> « Nine of the 11 CNVs affected volume of at least one subcortical structure. The hippocampus and amygdala were affected by five CNVs. Effect sizes of CNVs on subcortical volume, thickness and local surface area were correlated with their previously reported effect sizes on cognition and risk for ASD and SZ. »

## Mes réflexions
*(à compléter par moi)*
