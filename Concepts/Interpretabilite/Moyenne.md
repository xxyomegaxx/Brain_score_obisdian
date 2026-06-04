---
type: concept
categorie: interpretabilite
---

# Moyenne

## C'est quoi
Niveau d'interprétabilité intermédiaire où certaines composantes des scores (ex. déviations voxelwise) sont spatialement lisibles, tandis que d'autres (ex. composantes ICA multimodales) sont plus abstraites et moins directement interprétables sans expertise.

## Papiers
- [[Holz2023]] — Déviations voxelwise spatialement interprétables, mais les composantes LICA multimodales restent plus abstraites.
- [[Jing2023]] — Déviations par réseau nommé interprétables, mais sélection de features et clustering restent data-driven.
- [[LawryAguila2022]] — Modèle profond opaque, mais les déviations latentes sont re-décodées vers des régions cérébrales interprétables.
- [[Kumar2023b]] — Le modèle est une boîte noire mais ses sorties sont des cartes de déviation régionales directement lisibles.
- [[OliveiraSaraiva2023]] — Le réseau est opaque mais l'erreur de reconstruction par paire de réseaux rend les anomalies localisables.
