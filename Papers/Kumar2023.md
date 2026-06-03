---
id: Kumar2023
titre: "Subcortical brain alterations in carriers of genomic copy number variants"
auteur_principal: "Kuldeep Kumar"
annee: 2023
journal: "American Journal of Psychiatry"
doi: "10.1176/appi.ajp.20220304"
date_ajout: 2026-06-02
statut: lu
theme:
  - "[[Biomarqueurs]]"
  - "[[Mod. normative]]"
  - "[[Scores-méd. personnalisée]]"
methode_cat:
  - "[[Hybride]]"
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
  - "[[ENIGMA]]"
  - "[[UK Biobank]]"
application:
  - "[[Schizophrénie]]"
  - "[[Autisme]]"
  - "[[TDAH]]"
niveau_score:
  - "[[Par région]]"
  - "[[Global par sujet]]"
usage_score:
  - "[[Localisation]]"
  - "[[Association au phénotype]]"
  - "[[Comparaison de groupes]]"
  - "[[Détection d'atypies]]"
tags_libres: [CNV, subcortical, forme, pleiotropie, ENIGMA]
fichier_source: 
---

## TL;DR
Sur 11 variants du nombre de copies (CNV) et 6 troubles psychiatriques, les altérations subcorticales (volume et forme) d'un CNV sont d'autant plus marquées que ce CNV pèse sur le QI et le risque d'autisme/schizophrénie ; une même dimension cérébrale latente (limbique vs noyaux gris) traverse CNV et troubles, éclairant la pléiotropie génétique.

## Contributions
1. Premier atlas comparatif des altérations subcorticales (volume + forme) à travers 11 CNV et 6 troubles psychiatriques sur protocole harmonisé. [Biomarqueurs]
2. L'analyse de forme au niveau vertex révèle des altérations subrégionales qui s'annulent au niveau du volume global. [Biomarqueurs]
3. La taille d'effet cérébrale d'un CNV est corrélée à son effet sur le QI et au risque d'autisme/SZ (r = 0,66–0,89). [Scores-méd. personnalisée]
4. Une dimension latente commune (effets opposés limbique vs noyaux gris) traverse CNV et troubles. [Biomarqueurs]
5. Modèle normatif d'âge par processus gaussiens (W-scores) comme référence des déviations. [Mod. normative]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Biomarqueurs | Identifie régions/métriques subcorticales distinguant porteurs de CNV et contrôles. |
| Méthode | Hybride | GPR pour la norme, puis stats classiques (régression, PCA, clustering). |
| Population | Les deux | Contrôles sains pour la norme ; porteurs de CNV + troubles. |
| Type IRM | Structurel | IRM T1 : volumes et forme subcorticaux. |
| Interprétabilité | Haute | Cartes vertex localisées, dimensions latentes anatomiquement interprétables. |
| Pertinence (1–5) | 4 | Modèle normatif + biomarqueurs ; pas de brainscore individuel prédictif. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : volume de 7 structures subcorticales bilatérales (accumbens, amygdale, caudé, hippocampe, putamen, pallidum, thalamus) + ICV ; forme au niveau vertex via le pipeline ENIGMA — épaisseur (distance radiale) et surface (log du déterminant jacobien), ~27 000 vertex. Segmentation FreeSurfer 5.3.0.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge, sexe, site, ICV ; niveau sujet ; effet de l'âge modélisé de façon non-linéaire par processus gaussiens (comparé à un modèle linéaire).

## Étape 2 — Modélisation normative
Méthode · granularité · validation : régression par processus gaussiens (GPR) ajustée sur 782 contrôles (âge 6–80 ans) pour modéliser moyenne et écart-type ; W-scores dérivés (Z-scores normatifs). Granularité par vertex et par structure. Validation par concordance élevée (r = 0,93) avec un échantillon publié plus large pour le 22q11.2, et analyses de sensibilité (diagnostic, site, latéralité).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : W-scores (Z-scores normatifs GPR) ; au niveau vertex et structure ; signés (augmentations et diminutions vs contrôles) ; agrégés en Cohen's d case-contrôle, correction FDR q < 0,05 (across 11 CNV × 27 000 vertex pour la forme), focalisation sur le décile supérieur du Cohen's d pour comparer CNV et troubles.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : (Par région) localisation d'altérations subrégionales (tête/corps/queue du caudé, hippocampe) invisibles au volume global ; (Global par sujet) profils Cohen's d agrégés soumis à PCA → 2 premières composantes ≈ 45 % + 28 % de variance, clustering hiérarchique comparant 11 CNV et 6 troubles ENIGMA ; corrélation des tailles d'effet avec QI et risque ASD/SZ (r = 0,66–0,89).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : éclaire deux questions de longue date — pourquoi des CNV de loci différents augmentent le risque du même trouble, et pourquoi un seul CNV augmente le risque de troubles variés. Certains CNV se regroupent avec les troubles adultes (SZ, BD, MDD, OCD), d'autres avec l'autisme ; la dimension latente partagée (effets opposés limbique vs noyaux gris) est proposée comme substrat de la pléiotropie.

## Mes réflexions
*(à compléter par moi)*
