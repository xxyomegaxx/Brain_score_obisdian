---
id: Kumar2023b
titre: "Normative Modeling using Multimodal Variational Autoencoders to Identify Abnormal Brain Volume Deviations in Alzheimer's Disease"
auteur_principal: Sayantan Kumar
annee: 2023
journal: "Proc SPIE Int Soc Opt Eng (vol. 12465)"
doi: 10.1117/12.2654369
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
biomarqueur: "Computationnel"
methode_detail:
  - "[[VAE normatif]]"
modalite_detail:
  - "[[sMRI]]"
dataset:
  - "[[UK Biobank]]"
  - "[[ADNI]]"
application:
  - "[[Alzheimer]]"
niveau_score:
  - "[[Par région]]"
  - "[[Global par sujet]]"
usage_score:
  - "[[Localisation]]"
  - "[[Comparaison de groupes]]"
  - "[[Association au phénotype]]"
tags_libres: []
fichier_source: 
---
![[Kumar2023b.svg|697]]

## TL;DR
Un auto-encodeur variationnel multimodal (mmVAE) fusionne l'IRM T1 et T2 par Product-of-Experts pour apprendre le volume cérébral des sujets sains ; appliqué à Alzheimer, il produit des cartes de déviation plus sensibles aux stades de la maladie et mieux corrélées à la cognition qu'un modèle unimodal.

## Contributions
1. Premier modèle normatif multimodal (mmVAE) capturant la distribution conjointe T1/T2 pour quantifier les écarts de volume cérébral. [Mod. normative]
2. Déviations multimodales plus sensibles à la stadification (pente plus forte SMC→EMCI→LMCI→AD) que l'unimodal. [Mod. normative]
3. Meilleure corrélation des déviations individuelles avec la cognition (ADAS13, RAVLT) que la base unimodale. [Scores-méd. personnalisée]
4. Identification de régions à déviation fréquemment significative, candidates biomarqueurs d'Alzheimer. [Biomarqueurs]
5. Fusion latente par Product-of-Experts, cadre probabiliste généralisable. [Mod. normative]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Construit et valide un modèle normatif sur contrôles sains. |
| Méthode | IA | Auto-encodeur variationnel profond. |
| Population | Les deux | Entraîné sur sains, appliqué sur patients AD. |
| Type IRM | Structurel | T1 et T2, deux séquences structurelles. |
| Interprétabilité | Moyenne | Boîte noire mais cartes de déviation régionales lisibles. |
| Pertinence (1–5) | 5 | Cœur du sujet : normatif + scores + biomarqueurs. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : volumes de régions cérébrales issus de FreeSurfer v5.1, normalisés par le volume intracrânien (ICV) puis mis à l'échelle MinMax [0,1] ; niveau régional ; T1 = 64 régions corticales (atlas Desikan–Killiany) + 31 sous-corticales (Aseg), T2 = 16 régions hippocampiques ; analyses rapportées sur « 115 régions » (la somme énoncée 64+31+16=111 n'est pas réconciliée dans le texte — écart non précisé).
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge (one-hot, 44 positions, 47–91 ans) et sexe (one-hot, 2 positions), fournis aux décodeurs comme conditionnement ; effets modélisés implicitement par le réseau ; le but est de retirer les déviations dues aux covariables pour ne garder que la pathologie.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : mmVAE avec encodeurs/décodeurs spécifiques par modalité ; fusion des espaces latents par Product-of-Experts (produit de gaussiennes, éq. 2–3) ; latent = 64 ; couches FC 512-256-128-64 ; perte = ELBO (reconstruction par modalité + KL). Entraînement sur 9633 contrôles sains UK Biobank (split 80/20), puis fine-tuning par transfert sur ADNI ; CN ADNI (n=269) répartis 70 % entraînement/validation, 15 % held-out pour estimer μnorm/σnorm, 15 % test. Adam, lr=1e-5, batch=256, 500 époques. Baseline = VAE unimodal (modalités concaténées).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : Z-score par région et par patient, dij = (dij − μnorm)/σnorm, où dij est l'écart entre volume original et reconstruit (texte : « absolute signed difference » — direction signée/absolue ambiguë dans le papier), normalisé via la cohorte saine held-out ; significativité à p < 0.05 avec correction FDR (Benjamini–Hochberg).

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : (1) **Par région** — djmean (moyenne sur patients, éq. 7) pour localiser les régions anormales (fréquence de significativité) et comparer les cartes régionales entre stades (fig. 3). (2) **Global par sujet** — dimean (moyenne sur ~115 régions, éq. 6) pour la comparaison de groupes/stadification (pentes et comparaisons par paires pFDR < 0.05, fig. 2) et l'association au phénotype (corrélation de Pearson avec ADAS13 et RAVLT, fig. 4). Aucune prédiction ni stratification effectivement réalisée (citées en perspectives).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : sévérité des déviations croissante le long des stades d'Alzheimer (SMC→EMCI→LMCI→AD) et lien avec la cognition ; clustering futur en sous-types neuroanatomiques data-driven et classification AD vs sains évoqués comme perspectives.

## Biomarqueur identifié ?
**Verdict : Computationnel**

Modèle normatif mmVAE (autoencodeur variationnel multimodal) entraîné sur sujets sains, produisant des cartes de déviation (Z-scores) individualisées pour l'Alzheimer ; déviations hétérogènes, sans région universelle. Résultat réalisé : les cartes mmVAE sont plus sensibles au stade de la maladie, mieux corrélées à la cognition et révèlent davantage de régions à déviation significative que la référence unimodale -> biomarqueur computationnel. (Texte intégral PMC inaccessible (captcha) ; classification fondée sur le résumé de l'article SPIE.)

> « Deviation maps generated by mmVAE are more sensitive to disease staging within AD, have a better correlation with patient cognition and result in higher number of brain regions with statistically significant deviations compared to the unimodal baseline model. »

## Mes réflexions
*(à compléter par moi)*
