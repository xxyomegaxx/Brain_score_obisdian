---
id: Wolfers2020
titre: "Individual differences v. the average patient: mapping the heterogeneity in ADHD using normative models"
auteur_principal: "Thomas Wolfers"
annee: 2020
journal: "Psychological Medicine"
doi: "10.1017/S0033291719000084"
date_ajout: 2026-06-08
statut: lu
theme:
  - "[[Mod. normative]]"
  - "[[Biomarqueurs]]"
methode_cat:
  - "[[Stats classiques]]"
population:
  - "[[Les deux]]"
type_irm:
  - "[[Structurel]]"
interpretabilite: "[[Haute]]"
pertinence: 4
biomarqueur: "Computationnel"
methode_detail:
  - "[[GPR]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[IMpACT]]"
application:
  - "[[TDAH]]"
niveau_score:
  - "[[Par région]]"
usage_score:
  - "[[Localisation]]"
  - "[[Détection d'atypies]]"
  - "[[Comparaison de groupes]]"
tags_libres: ["ADHD", "IMpACT", "VBM", "GPR", "hétérogénéité", "médecine de précision"]
fichier_source: "Wolfers et al., Psychological Medicine 2020;50(2):314–323 (doi 10.1017/S0033291719000084)"
---
![[Wolfers2020.svg|649]]
## TL;DR
En modélisant la matière grise saine par rapport à l'âge (régression par processus gaussien), on situe chaque adulte avec TDAH persistant dans la plage normative et on cartographie ses déviations individuelles. Résultat : les déviations sont fréquentes en TDAH, mais leur **localisation varie tellement d'un patient à l'autre** (chevauchement > 2 % seulement dans de rares loci) que le « patient TDAH moyen » des analyses cas-témoins n'a qu'une valeur informative très limitée — alors qu'en moyenne le groupe TDAH montre une matière grise réduite au cervelet et à l'hippocampe.

## Contributions
1. Applique la modélisation normative pour décrire la biologie cérébrale de chaque patient TDAH individuellement, plutôt que via un contraste cas-témoins. [Mod. normative]
2. Montre que les déviations extrêmes sont fréquentes en TDAH persistant mais se chevauchent entre patients dans très peu de loci (> 2 % seulement), quantifiant l'hétérogénéité spatiale. [Biomarqueurs]
3. Reproduit les effets de groupe attendus (matière grise réduite au cervelet et à l'hippocampe) tout en démontrant que ces moyennes ne reflètent quasiment aucun individu. [Biomarqueurs]
4. Fournit une première preuve concrète de la nécessité d'explorer le TDAH au niveau individuel et un moyen pratique d'y parvenir. [Mod. normative]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Construit un modèle normatif de matière grise et y situe chaque patient. |
| Méthode | Stats classiques | Régression par processus gaussien (GPR), bayésienne non-paramétrique. |
| Population | Les deux | Plage normative saine + adultes avec TDAH persistant (cohorte IMpACT). |
| Type IRM | Structurel | Volume de matière grise (VBM) à partir de T1 (SPM12 + DARTEL). |
| Interprétabilité | Haute | Centiles et z-scores explicites par voxel/région. |
| Pertinence (1–5) | 4 | Cas d'usage fondateur de la modélisation normative pour l'hétérogénéité. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : volume de matière grise voxel-à-voxel (VBM), images T1 MPRAGE 1 mm³ segmentées sous SPM12, normalisées via un template d'étude DARTEL puis lissées (noyau gaussien 8 mm) ; niveau voxel (cerveau entier) ; effectifs exacts non rapportés dans le texte intégral récupéré.
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge (modèle de changements structuraux à travers la vie) ; niveau sujet ; non-linéarités captées par le noyau de la GPR. Détails complets des covariables dans les méthodes supplémentaires (non rapportés dans le texte récupéré).

## Étape 2 — Modélisation normative
Méthode · granularité · validation : régression par processus gaussien (Rasmussen & Williams ; cadre de Marquand et al. 2016), méthode bayésienne non-paramétrique fournissant des estimations ponctuelles et une mesure de confiance prédictive utilisée pour calculer les centiles. Participants issus de la cohorte néerlandaise IMpACT (adultes avec TDAH persistant et témoins sains appariés genre/âge/QI). Détails de validation non rapportés dans le texte intégral récupéré.

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : z-score par voxel quantifiant l'écart à la plage normative (la confiance prédictive de la GPR sert à normaliser l'écart) ; direction signée ; les déviations extrêmes (notamment infra-normales) sont identifiées par seuil de centile/z (valeur de seuil exacte non rapportée dans le texte récupéré).

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à :
- **Par région** → localisation (où se situent les déviations dans le cerveau) ; détection d'atypies individuelles (déviations fréquentes mais propres à chaque patient) ; comparaison de groupes (chevauchement > 2 % entre patients TDAH seulement dans de rares loci ; en moyenne matière grise réduite au cervelet et à l'hippocampe vs sains).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : démontre que le « patient TDAH moyen » des analyses cas-témoins masque l'hétérogénéité inter-individuelle ; plaide pour une caractérisation individualisée de la biologie cérébrale en TDAH comme préalable à une médecine de précision (sous-typage, cibles personnalisées).

## Biomarqueur identifié ?
**Verdict : Computationnel**

Modelisation normative (GPR) de la matiere grise selon l'age, situant chaque adulte avec TDAH persistant et cartographiant ses deviations individuelles. Les deviations sont frequentes mais leur localisation varie d'un patient a l'autre (chevauchement superieur a 2% dans de rares loci seulement) : aucune region universelle, un profil de deviation individualise est requis. Au niveau groupe, matiere grise reduite au cervelet et a l'hippocampe. NB: texte integral PMC inaccessible (reCAPTCHA) ; verdict fonde sur le resume chiffre et la note existante.

> « overlap of more than 2% between participants with ADHD was only observed in few brain loci »

## Mes réflexions
*(à compléter par moi)*
