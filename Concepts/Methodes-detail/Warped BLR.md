---
type: concept
categorie: methode-detail
---

# Warped BLR

## C'est quoi
Régression linéaire bayésienne avec warping de la vraisemblance : extension de la BLR standard qui applique une transformation (warping) à la variable réponse pour modéliser des distributions non-gaussiennes. Le warping SinhArcsinh (ou Box-Cox/affine) est appris conjointement aux paramètres du modèle, permettant d'estimer correctement les centiles extrêmes.

## Papiers
- [[Fraza2021]] — Méthode centrale : BLR augmentée d'un warping SinhArcsinh pour modéliser le non-gaussien.
- [[Bhome2024]] — Régression linéaire bayésienne avec warping pour modéliser les trajectoires normatives non gaussiennes age/sexe.
- [[Rutherford2022]] — Warped Bayesian Linear Regression (warping sinarcsinh/SHASH) via PCNtoolkit v0.20.
