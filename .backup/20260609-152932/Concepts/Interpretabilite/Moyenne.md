---
type: concept
categorie: interpretabilite
---

# Moyenne

## C'est quoi
Niveau d'interprétabilité intermédiaire où certaines composantes des scores (ex. déviations voxelwise) sont spatialement lisibles, tandis que d'autres (ex. composantes ICA multimodales) sont plus abstraites et moins directement interprétables sans expertise.

## Papiers
- [[Ho2025]] — Le cVAE est moins transparent que les centiles mais fournit des z-scores et des distributions interprétables.
- [[Holz2023]] — Déviations voxelwise spatialement interprétables, mais les composantes LICA multimodales restent plus abstraites.
- [[Jing2023]] — Déviations par réseau nommé interprétables, mais sélection de features et clustering restent data-driven.
- [[Kumar2023b]] — Le modèle est une boîte noire mais ses sorties sont des cartes de déviation régionales directement lisibles.
- [[Lawn2024]] — Z-scores localisables mais l'enrichissement moléculaire est un proxy indirect des neurotransmetteurs.
- [[LawryAguila2022]] — Modèle profond opaque, mais les déviations latentes sont re-décodées vers des régions cérébrales interprétables.
- [[OliveiraSaraiva2023]] — Le réseau est opaque mais l'erreur de reconstruction par paire de réseaux rend les anomalies localisables.
- [[Pinaya2019]] — Modèle profond ; métrique de déviation globale moins directement interprétable que les z-scores paramétriques.
