---
id: OliveiraSaraiva2023
titre: "Normative model detects abnormal functional connectivity in psychiatric disorders"
auteur_principal: "Duarte Oliveira-Saraiva"
annee: 2023
journal: "Frontiers in Psychiatry"
doi: "10.3389/fpsyt.2023.1068397"
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
  - "[[Fonctionnel]]"
interpretabilite: "[[Moyenne]]"
pertinence: 4
biomarqueur: "Candidat"
methode_detail:
  - "[[AE normatif]]"
modalite_detail:
  - "[[fMRI]]"
dataset:
  - "[[CoRR]]"
  - "[[UCLA LA5c]]"
  - "[[COBRE]]"
application:
  - "[[Schizophrénie]]"
  - "[[Trouble bipolaire]]"
  - "[[TDAH]]"
niveau_score:
  - "[[Global par sujet]]"
  - "[[Par réseau]]"
usage_score:
  - "[[Détection d'atypies]]"
  - "[[Comparaison de groupes]]"
  - "[[Localisation]]"
tags_libres: []
fichier_source: 
---
![[OliveiraSaraiva2023.svg|679]]
## TL;DR
Un autoencodeur entraîné seulement sur des sujets sains apprend un patron « normal » de connectivité fonctionnelle ; l'erreur de reconstruction par sujet et par paire de réseaux révèle des anomalies spécifiques à la schizophrénie, au trouble bipolaire et au TDAH, mais ces signatures de groupe ne tiennent pas au niveau individuel.

## Contributions
1. Modèle normatif par autoencodeur entraîné sur sains ; l'erreur de reconstruction = mesure de déviation. [Mod. normative]
2. Paires de réseaux mal reconstruites distinctes par trouble (ganglions de la base en BD/SCZ, salience–précunéus en TDAH). [Biomarqueurs]
3. Patrons retrouvés concordants avec la littérature clinique. [Biomarqueurs]
4. Généralisation confirmée sur base indépendante (COBRE) pour la schizophrénie. [Mod. normative]
5. Les différences de groupe s'effondrent au niveau individuel → médecine de précision. [Scores-méd. personnalisée]

## Classification
| Dimension | Valeur | Justification |
|---|---|---|
| Thème principal | Mod. normative | Construit et valide un modèle normatif par autoencodeur. |
| Méthode | IA | Apprentissage profond (autoencodeur). |
| Population | Les deux | Sains pour l'entraînement, patients pour le test. |
| Type IRM | Fonctionnel | rs-fMRI, connectivité fonctionnelle. |
| Interprétabilité | Moyenne | Modèle opaque, mais erreur par paire de réseaux localise les anomalies. |
| Pertinence (1–5) | 4 | Normatif + biomarqueurs ; fonctionnel, sans brainscore prédictif. |

## Étape 1 — Données d'entrée
**Features (y)** — quoi · niveau · nb de points : coefficients de corrélation de Pearson entre les séries temporelles BOLD de 14 réseaux fonctionnels (template de Shirer et al.) ; niveau = paires de réseaux ; 91 features par sujet (demi-matrice 14×14, diagonale exclue).
**Covariables (x)** — lesquelles · niveau · effets non-linéaires : aucune covariable ; l'autoencodeur ne reçoit ni âge ni sexe (limite explicite) ; standardisation z-score avec moyenne/écart-type du H-Train ; effets non-linéaires non applicables.

## Étape 2 — Modélisation normative
Méthode · granularité · validation : autoencodeur (Keras) à 3 couches cachées 91-46-13-46-91, leaky ReLU, dropout 0,5, L2 1e-5, He init, perte MSE, 1000 epochs, Adam (lr 0,0005) ; granularité = un modèle global sur les 91 features de connectivité ; validation par 10-fold cross-validation ; entraînement sur 366 sujets sains (655 sujets au total après contrôle qualité).

## Étape 3 — Scores déviants
Type · niveau · direction · seuillage : MSEs = erreur quadratique moyenne de reconstruction par sujet (sur 91 features) ; MSEf = erreur quadratique moyenne par paire de réseaux ; direction = valeur absolue |sortie − entrée| ; seuillage = binarisation au seuil = 1 correspondant aux 20 % plus hautes valeurs du vecteur de différences fusionné, puis degré (théorie des graphes).

## Étape 4 — Utilisation des scores
Niveau · but · corrélé/comparé à : (a) Global par sujet → comparaison entre groupes par test de Mann-Whitney (patients vs sains : p < 0,05 sur UCLA ; non significatif sur COBRE) et détection d'atypies (patients déviant plus que les sains) ; (b) Par réseau → localisation des paires de réseaux anormales propres à chaque trouble, et comparaison de groupes via soustraction de la matrice MSEf des sains. Aucune association directe score–phénotype/symptômes n'est réalisée (signalée comme non explorée).

## Application clinique
Lien avec symptômes / diagnostics / sous-groupes : patrons de connectivité distincts par trouble, concordants avec la littérature ; modèle généralisable (COBRE). Mais les différences de groupe ne résistent pas à l'analyse individuelle (hétérogénéité forte) → plaide pour une médecine de précision centrée sur les changements de réseaux propres à chaque patient plutôt qu'une classification de groupe.

## Biomarqueur identifié ?
**Verdict : Candidat**

Modèle normatif (autoencodeur) sur la connectivité fonctionnelle au repos, testé sur schizophrénie, trouble bipolaire et TDAH : les patients dévient davantage de la norme et des patrons de connectivité anormaux par groupe sont identifiés. Mais les auteurs reconnaissent que les différences de groupe ne tiennent pas à l'échelle individuelle, l'échantillon est petit, et aucune métrique de discrimination quantitative validée (AUC) n'est rapportée. Preuve préliminaire/non validée -> Candidat.

> « The group-level differences did not withstand individual-level analysis implying that psychiatric disorders are highly heterogeneous. »

## Mes réflexions
*(à compléter par moi)*
