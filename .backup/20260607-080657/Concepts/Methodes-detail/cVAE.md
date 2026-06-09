---
type: concept
categorie: methode-detail
---

# cVAE

## C'est quoi
Autoencodeur variationnel conditionnel (conditional VAE) : modèle génératif profond qui étend le VAE standard en intégrant des covariables conditionnelles (ex. âge, volume intracrânien) dans l'encodeur et le décodeur. Permet de séparer la variabilité d'intérêt des effets confondants directement au sein du modèle, sans pré-traitement externe.

## Papiers
- [[LawryAguila2022]] — Autoencodeur variationnel conditionné sur âge et ICV (latent=10) ; comparé à une GPR (PCNToolkit) qu'il surpasse en séparation et en coût.
