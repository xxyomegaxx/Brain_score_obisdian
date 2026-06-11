---
id: Parker2025
titre: "Generalizable MRI normative modelling to detect age-inappropriate neurodegeneration"
auteur_principal: "Thomas D. Parker"
annee: 2025
journal: "Alzheimer's Research & Therapy"
doi: "10.1186/s13195-025-01872-x"
date_ajout: 2026-06-07
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
biomarqueur: "Simple"
methode_detail:
  - "[[GAMLSS]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[NACC]]"
  - "[[ADNI]]"
  - "[[NIFD]]"
application:
  - "[[Alzheimer]]"
  - "[[Démence frontotemporale]]"
  - "[[Vieillissement]]"
niveau_score:
  - "[[Par région]]"
  - "[[Global par sujet]]"
usage_score:
  - "[[Localisation]]"
  - "[[Détection d'atypies]]"
  - "[[Comparaison de groupes]]"
  - "[[Association au phénotype]]"
  - "[[Prédiction]]"
tags_libres: ["BrainChart", "centiles", "atrophie", "FreeSurfer", "out-of-sample", "neurodégénérescence"]
fichier_source: "Parker et al., Alzheimer's Res Ther 17:244 (2025)"
---
![[Parker2025.svg|649]]
## TL;DR
À partir du modèle normatif BrainChart (GAMLSS, 56 173 sujets sur la vie entière), des **scores de centiles régionaux** d'épaisseur corticale et de volume hippocampe/amygdale (ajustés sur le volume intracrânien) constituent une méthode **généralisable** pour détecter objectivement une atrophie « inappropriée pour l'âge » au niveau individuel ; ces centiles corrèlent à la cognition, à la charge tau, discriminent l'Alzheimer de témoins appariés, et révèlent des patrons distincts selon les phénotypes de dégénérescence lobaire frontotemporale.

## Contributions
1. Cartes normatives (« brain charts ») régionales d'épaisseur corticale et de volumes hippocampe/amygdale applicables à l'individu, dérivées de 56 173 sujets et ajustées sur le volume intracrânien estimé. [Mod. normative]
2. Méthode généralisable : estimation hors-échantillon (random effects par maximum de vraisemblance) alignant de nouveaux jeux de données sur la trajectoire normative de référence. [Mod. normative]
3. Les centiles régionaux corrèlent avec la cognition (MMSE) et discriminent l'Alzheimer neuropathologique (n=351) de témoins cognitivement normaux appariés par propension (NACC). [Biomarqueurs]
4. Dans ADNI-3 (amyloïde-PET +), les centiles s'associent au stade de la maladie, à la cognition et au dépôt de tau régional (n=39 démence AD, n=71 MCI). [Biomarqueurs]
5. Patrons distincts d'atrophie corticale inappropriée pour l'âge selon les variants cliniques de dégénérescence lobaire frontotemporale (NIFD, n=113). [Scores-méd. personnalisée]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Développe/applique des modèles normatifs (brain charts) généralisables à l'individu. |
| Méthode | Stats classiques | GAMLSS paramétrique (cadre BrainChart), pas d'apprentissage profond. |
| Population | Les deux | Référence saine (56 173) + patients AD/MCI/DLFT vs témoins normaux. |
| Type IRM | Structurel | Épaisseur corticale + volumes hippocampe/amygdale (FreeSurfer, T1w). |
| Interprétabilité | Haute | Scores de centiles directement interprétables comme position dans la norme. |
| Pertinence (1–5) | 4 | Démonstration de généralisabilité d'un score normatif individuel pour la neurodégénérescence. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : épaisseur corticale régionale (aparc.stats) et volumes hippocampe/amygdale (aseg.stats) extraits via FreeSurfer ; niveau région ; jeux d'application NACC (n=351 AD + témoins appariés), ADNI-3 (n=39 démence AD, n=71 MCI), NIFD (n=113 DLFT) ; référence normative = 56 173 scans sur la vie entière.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge et sexe (trajectoires non-linéaires GAMLSS) ; volume intracrânien estimé (eTIV) comme confondant ; effets aléatoires spécifiques au site/scanner.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : modèle normatif **GAMLSS** suivant Bethlehem, Seidlitz, White et al. (2022), estimé sur 56 173 témoins ; un modèle par région. Les nouveaux jeux (NACC, ADNI, NIFD) ne servent pas à estimer la référence : **estimation hors-échantillon** des effets aléatoires d'étude par maximum de vraisemblance, alignant moyenne/variance/asymétrie. Estimation stable nécessite ~100 sujets sains par scanner.

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : **score de centile** régional par sujet (position dans la distribution normative ajustée âge/sexe/eTIV) ; signé (centiles bas = atrophie). Seuillage explicite non rapporté ; interprétation continue des centiles.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : **par région** (patrons spatiaux d'atrophie ; localisation ; patrons distincts par phénotype DLFT) ; **global par sujet** (cas individuels ; association cognition/MMSE, stade, tau PET temporal ; discrimination AD vs témoins appariés par propension). Finalités : localisation, détection d'atypies (atrophie inappropriée pour l'âge), comparaison de groupes, association au phénotype, prédiction de la performance cognitive.

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : maladie d'Alzheimer, dégénérescence lobaire frontotemporale, vieillissement. Outil généralisable, applicable à un patient unique, pour objectiver une atrophie pathologique au-delà du « normal pour l'âge » et soutenir le diagnostic différentiel des démences.

## Biomarqueur identifié ?
**Verdict : Simple**

Brain charts regionaux (centiles GAMLSS d'epaisseur corticale et de volumes hippocampe/amygdale, references sur 56 173 sujets) appliques individuellement. La discrimination repose sur des regions universelles connues de l'atrophie Alzheimer (hippocampe, amygdale, cortex entorhinal/temporal) : marqueur direct par region/metrique specifique. Resultat quantitatif valide dans des cohortes independantes : AUC amygdale 0,82/0,79, hippocampe 0,79/0,78, modele combine 0,86 (NACC), confirme en validation croisee (0,84) et dans ADNI. Marqueur simple/universel plutot que carte de deviation heterogene.

> « amygdala (left AUC = 0.82; right AUC = 0.79) and hippocampal volume (left AUC = 0.79; right AUC = 0.78) centile scores ... were the ROIs that demonstrated the greatest discriminative ability ... A combined model ... provided an AUC of 0.86 »

## Mes réflexions
*(à compléter par moi)*
