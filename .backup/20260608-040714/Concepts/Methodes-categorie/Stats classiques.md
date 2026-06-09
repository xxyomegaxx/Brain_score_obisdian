---
type: concept
categorie: methode-cat
---

# Stats classiques

## C'est quoi
Famille de méthodes statistiques paramétriques et non paramétriques classiques (régressions, modèles mixtes, modèles additifs) reposant sur des hypothèses explicites de distribution et estimées par maximum de vraisemblance ou méthodes des moindres carrés, sans recours à l'apprentissage automatique.

## Papiers
- [[Bethlehem2020]] — Repose sur LOESS, modèles mixtes et z-scores ; aucune méthode d'apprentissage automatique.
- [[Bethlehem2022]] — Modèle GAMLSS paramétrique avec polynômes fractionnaires, sans apprentissage automatique.
- [[Bhome2024]] — Modèle normatif par régression bayésienne warped, puis tests Mann-Whitney, régressions linéaires et correction FDR.
- [[Bozek2023]] — Ajustement statistique de courbes de percentiles (GAMLSS), sans apprentissage profond.
- [[Chen2021]] — Passe en revue les approches statistiques de trajectoires (GLMM, GAMM, GAMLSS) et les centiles, sans apprentissage profond.
- [[DeBoer2024]] — Régression bayésienne hiérarchique (HBR) à inférence MCMC ; pas d'apprentissage profond pour le modèle normatif.
- [[DiBiase2022]] — Recourt à la régression quantile, à l'ACP et au clustering hiérarchique de Ward plutôt qu'à de l'apprentissage profond.
- [[Dinga2021]] — Approche statistique paramétrique (modèles additifs, maximum de vraisemblance pénalisé), sans apprentissage automatique.
- [[Dorfschmidt2025]] — Modélisation par GAMLSS (polynômes fractionnaires, effet de site), sans apprentissage profond.
- [[Elleaume2025]] — Warped Bayesian Linear Regression (PCNtoolkit), modèle statistique sans apprentissage profond.
- [[Kia2020]] — Méthode statistique bayésienne paramétrique (HBR), sans apprentissage profond.
- [[Lawn2024]] — Norme estimée par régression de la connectivité sur âge et sexe (méthode statistique, non profonde).
- [[Lawrence2021]] — Effets d'âge estimés par polynômes fractionnaires et courbes centiles par régression quantile, sans apprentissage automatique.
- [[Lv2021]] — Emploie la régression quantile avec bootstrap, sans méthode d'apprentissage automatique.
- [[Marquand2019]] — Passe en revue des approches statistiques de régression pour la modélisation normative.
- [[Parker2025]] — Modèle normatif GAMLSS paramétrique (cadre BrainChart), sans apprentissage profond.
- [[Rutherford2022]] — Utilise une régression linéaire bayésienne (BLR) avec warping plutôt qu'un modèle profond.
- [[Wolfers2018]] — Modèle normatif estimé par régression par processus gaussien (statistique, non profond).
- [[Xie2025]] — Modèle normatif par régression linéaire (âge, sexe) puis apprentissage supervisé classique sur les déviations.
