---
id: Verdi2024
titre: "Personalizing progressive changes to brain structure in Alzheimer's disease using normative modeling"
auteur_principal: "Serena Verdi"
annee: 2024
journal: "Alzheimer's & Dementia"
doi: "10.1002/alz.14174"
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
biomarqueur: "Computationnel"
methode_detail:
  - "[[Warped BLR]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[ADNI]]"
  - "[[UK Biobank]]"
  - "[[ABCD]]"
  - "[[OASIS-3]]"
application:
  - "[[Alzheimer]]"
niveau_score:
  - "[[Par région]]"
  - "[[Global par sujet]]"
usage_score:
  - "[[Localisation]]"
  - "[[Détection d'atypies]]"
  - "[[Comparaison de groupes]]"
  - "[[Association au phénotype]]"
  - "[[Prédiction]]"
tags_libres: ["ADNI", "longitudinal", "tOC", "MCI", "transfer learning", "hippocampe"]
fichier_source: "Verdi et al., Alzheimer's & Dementia 2024;20(10):6998–7012 (doi 10.1002/alz.14174)"
---
![[Verdi2024.svg|649]]
## TL;DR
Première application de la modélisation normative neuro-anatomique à des données IRM **longitudinales** de la maladie d'Alzheimer : en comptant pour chaque scan le nombre de régions « hors-norme » (z < −1,96), on obtient un marqueur personnalisé d'atrophie, le **total outlier count (tOC)**. Le tOC augmente avec le temps chez les patients AD et chez les sujets MCI qui convertissent vers l'AD, corrèle avec la mémoire, l'amyloïde, la tau et l'*APOE*, et son taux d'augmentation sur 12 mois **prédit le risque de conversion MCI→AD** (chaque +3 outliers ≈ +30 % de risque).

## Contributions
1. Applique pour la première fois la modélisation normative neuro-anatomique à des séries IRM longitudinales d'AD (3 233 scans, 1 181 participants ADNI). [Mod. normative]
2. Propose un marqueur d'atrophie personnalisé et interprétable, le total outlier count (tOC), résumant par sujet le nombre de régions déviantes. [Scores-méd. personnalisée]
3. Montre que le tOC croît dans le temps chez les patients AD et MCI-progressifs, mais pas chez les contrôles, l'hippocampe gauche ayant le plus fort taux de changement. [Biomarqueurs]
4. Établit que le taux de changement du tOC sur 12 mois prédit la conversion MCI→AD (analyse de survie de Cox) et corrèle avec mémoire, fonctions exécutives, amyloïde et tau. [Biomarqueurs]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Étend la modélisation normative au suivi longitudinal de l'AD. |
| Méthode | Stats classiques | Régression bayésienne non-gaussienne (modèles braincharts) + transfert. |
| Population | Les deux | Référence saine (~58 k) + cohorte clinique ADNI (AD, MCI, contrôles). |
| Type IRM | Structurel | Épaisseur corticale et volumes sous-corticaux T1 (FreeSurfer). |
| Interprétabilité | Haute | z-scores régionaux et comptage d'outliers à seuil explicite. |
| Pertinence (1–5) | 5 | Score de déviation longitudinal personnalisé, cœur du projet brainscore. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : épaisseur corticale de 148 régions (atlas Destrieux) + volume de matière grise de 20 régions sous-corticales, extraites par FreeSurfer *recon-all*, soit 168 régions par scan ; niveau région ; 3 233 scans T1 de 1 181 participants ADNI (661 contrôles, 1 999 MCI, 573 AD).
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge, sexe et site ; niveau sujet ; non-linéarités et non-gaussianité captées par le modèle de régression bayésienne (braincharts) ; recalibrage par site sur 70 % des contrôles ADNI (apprentissage adaptatif / transfert).

## Étape 2 — Modélisation normative
Méthode · granularité · validation : modèle normatif de référence entraîné sur 58 836 scans sains de 82 sites (sources combinées dont UK Biobank, ABCD, OASIS) avec covariables âge/sexe/site — régression bayésienne non-gaussienne (cadre braincharts, un modèle par région). Adaptation par transfert aux données ADNI via 70 % des contrôles cognitivement intacts (par site, stratifié sexe). Les 30 % de contrôles restants + MCI + AD sont comparés au modèle pour produire les z-scores. Modèles ouverts : github predictive-clinical-neuroscience/braincharts.

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : z-score par région ; un « outlier » = région avec z < −1,96 (épaisseur/volume réduit ; z des ventricules inversé pour refléter l'expansion) ; direction signée (versant infra-normal) ; total outlier count (tOC) = somme des outliers sur les 168 régions par scan.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à :
- **Par région** → localisation (cartes d'outliers ; hippocampe gauche le plus fréquent : 47 %→60 %→72 % à 0/12/24 mois ; plus fort taux de changement) ; détection d'atypies individuelles (patterns hétérogènes entre patients).
- **Global par sujet (tOC)** → comparaison de groupes (hausse du tOC chez AD β=0,38 et MCI, pas chez contrôles) ; association au phénotype (mémoire β=−1,99, fonctions exécutives, amyloïde SUVR, tau SUVR, *APOE*, AC score) ; prédiction (Cox : +3 outliers sur 12 mois → +30,2 % de risque de conversion MCI→AD, HR=1,09).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : suivi individualisé de la trajectoire d'atrophie en AD ; le tOC et les cartes régionales pourraient servir d'outil pronostique (risque de conversion MCI→AD) et de mesure de progression pour les essais cliniques, là où les statistiques de groupe masquent l'hétérogénéité inter-patients.

## Biomarqueur identifié ?
**Verdict : Computationnel**

Biomarqueur computationnel/personnalisé en Alzheimer : a partir de cartes de déviation normatives, un décompte individuel d'outliers (total outlier count, tOC) est dérivé — profil multivarié sans région universelle. Le tOC augmente dans le temps chez les patients AD et chez les sujets MCI évoluant vers l'AD (r = 0,38, p = 9,0x10^-13), et son taux de variation corrèle avec la cognition, les marqueurs amyloïde/tau et l'allèle APOE e4. Métrique de déviation individualisée prédictive et validée.

> « Increased tOC over time (i.e., accumulation of outliers) was observed in the AD group (r = 0.38, p = 9.0 x 10^-13) »

## Mes réflexions
*(à compléter par moi)*
