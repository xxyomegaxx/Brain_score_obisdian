---
type: concept
categorie: methode-detail
---

# Autoencodeur 3D semi-supervisé

## C'est quoi
Réseau de neurones convolutif encodeur-décodeur opérant sur des volumes 3D (ex. volumes IRM), entraîné avec un coût mixte : erreur de reconstruction non supervisée et erreur de prédiction supervisée de variables cibles (ex. âge, sexe). Produit un espace latent à la fois compressé et biologiquement ancré, décodable vers l'espace voxel d'origine.

## Papiers
- [[Zabihi2024]] — Architecture conv. 3D avec joint optimization reconstruction + prédiction âge/sexe (λ=0,05).
