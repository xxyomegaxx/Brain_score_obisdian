---
id: Marquand2019
titre: "Conceptualizing mental disorders as deviations from normative functioning"
auteur_principal: "Andre F. Marquand"
annee: 2019
journal: "Molecular Psychiatry"
doi: "10.1038/s41380-019-0441-1"
date_ajout: 2026-06-07
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
  - "[[Fonctionnel]]"
interpretabilite: "[[Haute]]"
pertinence: 5
biomarqueur: "Non"
methode_detail:
  - "[[GPR]]"
  - "[[HBR]]"
  - "[[Régression polynomiale]]"
  - "[[Régression quantile]]"
modalite_detail:
  - "[[sMRI]]"
  - "[[fMRI]]"
niveau_score:
  - "[[Par région]]"
  - "[[Global par sujet]]"
usage_score:
  - "[[Stratification]]"
  - "[[Détection d'atypies]]"
  - "[[Localisation]]"
tags_libres: ["revue", "cadre conceptuel", "hétérogénéité", "growth charts", "incertitude aléatoire/épistémique"]
fichier_source: "Marquand et al., Molecular Psychiatry 24:1415-1424 (2019)"
---
![[Marquand2019.svg|649]]
## TL;DR
Revue de référence qui pose le **cadre conceptuel** de la modélisation normative : un modèle statistique qui mappe des variables démographiques/cliniques vers une mesure biologique (souvent IRM) et fournit, comme les courbes de croissance pédiatriques, une inférence au **niveau de l'individu** sur son écart à la norme. Elle propose une grille unificatrice (choix des variables, séparation des sources de variation aléatoire vs épistémique, capacité d'inférence individuelle), survole les méthodes (processus gaussien, régressions hiérarchique/polynomiale/quantile…) et l'usage clinique pour parser l'hétérogénéité au-delà des études cas-témoins.

## Contributions
1. Formalise la modélisation normative comme alternative aux études cas-témoins, en modélisant la variation individuelle (statistiques de 2ᵉ ordre) plutôt que la moyenne du groupe. [Mod. normative]
2. Propose une taxonomie unificatrice des approches selon trois critères : choix des variables, séparation des sources de variation, et capacité d'inférence individuelle. [Mod. normative]
3. Distingue l'incertitude aléatoire (variabilité réelle entre sujets, d'intérêt) de l'incertitude épistémique (manque de données, nuisance) — clé pour une stratification valide. [Mod. normative]
4. Relie la modélisation normative aux approches voisines (clustering, « brain age ») et survole son emploi clinique pour parser l'hétérogénéité. [Biomarqueurs]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Revue conceptuelle fondatrice du cadre de modélisation normative. |
| Méthode | Stats classiques | Passe en revue des régressions statistiques (GPR, hiérarchique, polynomiale, quantile…). |
| Population | Les deux | Cadre fondé sur une cohorte de référence saine appliquée à des cohortes cliniques. |
| Type IRM | Structurel + Fonctionnel | Exemples portant sur l'épaisseur corticale (structurel) et l'activité cérébrale (fonctionnel). |
| Interprétabilité | Haute | Cadre explicite avec Z-scores et inférence individuelle interprétable. |
| Pertinence (1–5) | 5 | Référence conceptuelle centrale pour tout projet de modélisation normative. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : une mesure biologique quantitative (« readout »), typiquement dérivée de l'IRM (ex. épaisseur corticale, activité régionale) ; niveau région/voxel ; revue (pas de jeu de données unique).
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : âge et sexe le plus souvent, ou variables cliniques/comportementales ; mapping pouvant être inversé (« brain age » : prédire l'âge depuis le cerveau) ; niveau sujet ; non-linéarités explicitement discutées comme un critère de choix du modèle.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : cadre en quatre étapes (choix cohorte/variables → estimation du modèle → validation hors-échantillon, ex. validation croisée → application à une cohorte cible). Méthodes survolées : régression par processus gaussien, modèles hiérarchiques, régression polynomiale, régression quantile, régression à vecteurs de support. Granularité : un modèle par localisation cérébrale possible.

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : Z-score analytique (écart à la norme normalisé par l'incertitude prédictive) ; signé ; seuil non prescrit (revue). Souligne l'importance d'estimer précisément les centiles extrêmes et de séparer variabilité aléatoire et épistémique.

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : niveau **par région** (cartes de déviation par localisation) et **global par sujet** (profil individuel d'écart) ; finalités : parser l'hétérogénéité (stratification), détecter des atypies individuelles, localiser les écarts ; alternative aux moyennes de groupe peu informatives.

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : survol de la littérature appliquant la modélisation normative aux conditions cliniques ; argumente que les déviations individuelles, n'ayant pas besoin de se chevaucher entre patients, capturent mieux l'hétérogénéité que « le patient moyen », ouvrant vers une psychiatrie de précision.

## Biomarqueur identifié ?
**Verdict : Non**

Article de revue/perspective (etiquete Review Article) presentant les fondements conceptuels de la modelisation normative et un cadre unificateur des approches, avec recommandations. Aucune analyse empirique ni resultat discriminatif n'est realise dans ce papier ; il synthetise la litterature existante. Aucun biomarqueur n'y est demontre.

> « Here, we provide a unifying review of the theory and application of normative modelling for understanding the biological and clinical heterogeneity underlying mental disorders »

## Mes réflexions
*(à compléter par moi)*
