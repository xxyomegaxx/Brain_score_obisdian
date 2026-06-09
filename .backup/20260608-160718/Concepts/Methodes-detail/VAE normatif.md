---
type: concept
categorie: methode-detail
---

# VAE normatif

## C'est quoi
Modèle normatif fondé sur un auto-encodeur variationnel (VAE) : le réseau apprend la distribution latente des données cérébrales de sujets sains, puis quantifie la déviation d'un individu par l'écart entre son observation et la reconstruction attendue. Permet une inférence normative non linéaire et probabiliste sans supposer de distribution paramétrique sur les features.

## Papiers
- [[Kumar2023b]] — Étend NormVAE à deux modalités via une fusion latente Product-of-Experts (mmVAE).
