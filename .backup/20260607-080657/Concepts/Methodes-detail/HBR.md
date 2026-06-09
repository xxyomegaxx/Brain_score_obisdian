---
type: concept
categorie: methode-detail
---

# HBR

## C'est quoi
Hierarchical Bayesian Regression : cadre bayésien hiérarchique permettant d'estimer des paramètres de modèles normatifs à plusieurs niveaux (sujet, site, population). Utilisé pour l'apprentissage par transfert multi-site, il recalibre un modèle normatif pré-entraîné vers de nouveaux sites sans ré-entraînement complet, via des priors appris sur la cohorte de référence.

## Papiers
- [[Bhome2024]] — Apprentissage par transfert hiérarchique bayésien pour recalibrer le modèle de référence aux sites de l'étude.
- [[DeBoer2024]] — Méthode centrale, étendue à une vraisemblance SHASH avec reparamétrisation SHASH_b pour le sampling MCMC.
- [[Zabihi2024]] — Régression bayésienne hiérarchique non gaussienne appliquée aux composantes UMAP, âge en régresseur et sexe en batch.
