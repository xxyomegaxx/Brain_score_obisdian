---
type: synthese
titre: "État de l'art — modélisation normative en neuro-imagerie"
date: 2026-06-09
corpus: 41 papiers (vault Papers/)
---

# État de l'art — modélisation normative en neuro-imagerie

> Synthèse générée à partir des 41 notes du vault. Chaque affirmation renvoie aux papiers `[[id]]`. Chiffres repris des notes ; « non rapporté » si absent. Les verdicts biomarqueur ne sont posés que sur 8/41 notes (back-fill en cours) — la section 3 est donc partielle.

## 1. Vue d'ensemble
Le domaine est **méthodologiquement mûr** — le cadre conceptuel est posé par [[Marquand2016]] (au-delà du cas-témoin) et la revue [[Marquand2019]] — et en **pleine expansion clinique**. Trois tendances nettes :
- **Statistique → apprentissage profond** : 27 papiers en stats classiques, 7 en IA, 6 hybrides. Le deep learning monte ([[Pinaya2019]], [[Wiegert2025]], [[Ho2025]]).
- **Structurel → multimodal** : sMRI domine (33), puis fMRI (12) et dMRI (6).
- **Groupe → individu** : l'objet central est la **déviation individuelle**, avec un constat récurrent d'**hétérogénéité inter-patients** (peu de chevauchement entre patients).

Modèles/jeux de référence : **Brain charts** [[Bethlehem2022]], **PCNtoolkit** [[Rutherford2022]] / [[Rutherford2022b]] ; datasets dominants UK Biobank (16), HCP (10), ABCD/CamCAN/ADNI (5 chacun), ENIGMA (4).

Points saillants : (1) la robustesse dépend fortement de la **taille et des covariables** de la référence [[Elleaume2025]] ; (2) la **non-gaussianité** est désormais bien gérée (warping/SHASH) [[Fraza2021]], [[DeBoer2024]] ; (3) peu de **biomarqueurs simples universels** — les marqueurs sont surtout **computationnels/personnalisés**.

## 2. Méthodes de modélisation normative

### Statistiques classiques (majoritaires)
- **GPR** (processus gaussiens, 11) — bayésien non-paramétrique, incertitude explicite ; **limite : coût ~cubique, non scalable**. Fondateur [[Marquand2016]] ; appliqué par [[Wolfers2018]], [[Zabihi2019]], [[Wolfers2020]], [[Holz2023]], [[Kumar2023]].
- **BLR / Warped BLR** (8) — régression bayésienne + *likelihood warping* (SHASH) ; **scalable big data + non-gaussien**. Méthode de [[Fraza2021]] ; cœur de [[Rutherford2022]], [[Elleaume2025]], [[Verdi2024]], [[Bhome2024]], [[DeBoer2024]].
- **HBR** (9) — bayésien hiérarchique, gère les **effets de site / federated / transfert**. [[Kia2020]] (multi-sites), extensions non-gaussiennes [[DeBoer2024]], [[Ho2025]].
- **GAMLSS** (9) — location/scale/shape, non-linéaire, sélection auto. [[Dinga2021]], [[Bethlehem2022]], [[Bozek2023]], [[Chen2021]], [[Parker2025]].
- **Régression quantile / polynomiale, LMS, MFPR, centiles** — alternatives plus simples. [[Lv2021]], [[Lawrence2021]], [[DiBiase2022]].

### IA / apprentissage profond
- **Autoencodeurs normatifs** : AE (erreur de reconstruction) [[Pinaya2019]] (premier), [[OliveiraSaraiva2023]] ; **espace latent** [[Wiegert2025]] (256D, magnitude+direction) ; **cVAE** [[Ho2025]], [[LawryAguila2022]] ; **VAE** [[Kumar2023b]] ; autoencodeur 3D semi-supervisé [[Zabihi2024]].
- **Force** : capture des patterns distribués non-linéaires sur le cerveau entier ; **limite** : interprétabilité moindre (souvent « Moyenne »).

### Hybride
6 papiers combinent réduction de dimension / ICA + normatif (ex. [[Lawn2024]], [[Jing2023]], [[Kumar2023]]).

| Méthode | Forces | Limites | Papiers |
|---|---|---|---|
| GPR | incertitude, non-linéaire | non scalable (O(n³)) | [[Marquand2016]], [[Wolfers2018]], [[Zabihi2019]] |
| Warped BLR | scalable, non-gaussien | warping paramétrique | [[Fraza2021]], [[Rutherford2022]], [[Elleaume2025]] |
| HBR | multi-sites, federated, transfert | coût MCMC | [[Kia2020]], [[DeBoer2024]], [[Ho2025]] |
| GAMLSS | location/scale/shape flexible | suppose distribution paramétrique | [[Dinga2021]], [[Bethlehem2022]] |
| AE / (c)VAE | patterns distribués, cerveau entier | peu interprétable | [[Pinaya2019]], [[Wiegert2025]], [[Ho2025]] |

## 3. Biomarqueurs trouvés (verdicts sur 8/41)
- **Computationnels / personnalisés** (profils de déviation, pas une région universelle) : [[Shao2024]] (dépression — cartes de probabilité normative, AUC 0,71–0,78 > GMV brut), [[Pinaya2019]] (schizophrénie/autisme — erreur de reconstruction), [[Verdi2024]] (Alzheimer — z régionaux + comptage d'outliers, suivi de progression).
- **Candidats** (marqueur proposé, preuve préliminaire ou non validée) : [[Marquand2016]] (TDAH, fondateur), [[Wolfers2018]] (schizophrénie/bipolaire — déviations très hétérogènes), [[Zabihi2019]] (autisme), [[Lin2024]] (schizophrénie, effet pharmacologique).
- **Non** : [[Mitchell2025]] (revue/cadre TBI, aucun marqueur empirique).

**Constat transversal** : à travers les pathologies les mieux couvertes — schizophrénie (14 papiers), Alzheimer (9), autisme (8), TDAH (8), dépression (4), épilepsie (3) — la littérature converge vers l'idée qu'**aucune région n'est anormale chez la majorité des patients** ; les biomarqueurs exploitables sont donc surtout **individualisés/computationnels** plutôt que des marqueurs simples universels.

## 4. Agrégation des déviations → score patient *(section clé)*
**Niveaux** : Par région (35), Global par sujet (26), Par réseau (5 : [[Holz2023]], [[Jing2023]], [[Lin2024]], [[OliveiraSaraiva2023]], [[Xie2025]]).

Façons d'agréger trouvées dans le corpus :
1. **Z-score par ROI** — brique de base, quasi universelle (niveau région).
2. **Total Outlier Count (tOC) / comptage de déviations extrêmes** (typiquement z < −1,96) — un score par sujet = nb de régions outliers. [[Verdi2024]], [[Bhome2024]], [[Elleaume2025]] ; seuillage extrême aussi chez [[Wolfers2018]], [[Bethlehem2022]], [[Bozek2023]], [[Rutherford2022]], [[Zabihi2019]], [[Parker2025]], [[Chen2021]], [[Lawrence2021]]. → détection d'atypies, comparaison de groupes.
3. **Cartes de probabilité normative (NPM)** — profil individuel de déviations. [[Shao2024]]. → localisation, prédiction.
4. **Distance / magnitude (± direction) dans un espace latent** — score global appris. [[Wiegert2025]] (magnitude **et** direction, 256D), [[Pinaya2019]] (erreur de reconstruction), [[OliveiraSaraiva2023]], [[LawryAguila2022]], [[Kumar2023]], [[Ho2025]], [[Zabihi2024]]. → détection d'atypies, prédiction.
5. **Scores par réseau** (connectivité fonctionnelle statique/dynamique) — agrégation par réseau plutôt que par ROI. [[Lin2024]] (aFCS/fFCS, 17 réseaux Yeo), [[Jing2023]], [[Xie2025]], [[OliveiraSaraiva2023]]. → association au phénotype, stratification.
6. **Combinaison déviations + scores polygéniques (PRS)** — fusion imagerie/génétique. [[Wiegert2025]], [[DiBiase2022]]. → prédiction améliorée.
7. **Classification ML sur le vecteur de déviations** (SVC, etc.) — le vecteur z devient l'entrée d'un classifieur. [[Shao2024]], [[Elleaume2025]], [[Mito2025]], [[Xie2025]], [[Ge2024]], [[Lawn2024]], [[Marquand2016]], [[DeBoer2024]], [[Kumar2023b]], [[Zabihi2024]]. → prédiction/diagnostic.

| Agrégation | Niveau | Finalité | Papiers |
|---|---|---|---|
| z-score par ROI | région | base | (universel) |
| tOC / comptage d'extrêmes | global/sujet | détection d'atypies, comparaison | [[Verdi2024]], [[Bhome2024]], [[Elleaume2025]] |
| Cartes de probabilité normative | région→sujet | localisation, prédiction | [[Shao2024]] |
| Distance/magnitude latente (±direction) | global/sujet | détection, prédiction | [[Wiegert2025]], [[Pinaya2019]], [[Ho2025]] |
| Scores par réseau (FC) | réseau | association, stratification | [[Lin2024]], [[Jing2023]], [[Xie2025]] |
| Déviations + PRS | global/sujet | prédiction | [[Wiegert2025]], [[DiBiase2022]] |
| Classifieur ML sur vecteur z | région→sujet | prédiction/diagnostic | [[Shao2024]], [[Mito2025]], [[Xie2025]] |

## 5. Gaps & pistes pour le prochain papier
- **Pas de consensus sur l'agrégation optimale** : tOC vs moyenne des |z| vs magnitude latente vs classifieur ML coexistent sans comparaison systématique. → **Opportunité forte : benchmarker les schémas d'agrégation pour un même score patient**, sur une cohorte commune.
- **Validation externe / reproductibilité** encore rares ; l'**harmonisation multi-sites** (HBR/federated [[Kia2020]], [[DeBoer2024]]) reste un verrou.
- **Interprétabilité** des marqueurs computationnels (latents profonds) faible → besoin d'explicabilité (attribution région↔score).
- **Sous-exploitation du multimodal et du niveau réseau** (seulement 5 papiers « par réseau ») → fusionner structurel + fonctionnel + diffusion.

**Pistes concrètes :**
1. Un **score patient hybride** combinant tOC (extrêmes), magnitude **et direction** latentes, et signature par réseau.
2. Un **benchmark d'agrégations** (région→sujet) à finalité diagnostique/pronostique, validé hors-échantillon.
3. Intégration **imagerie + PRS** (dans la lignée de [[Wiegert2025]], [[DiBiase2022]]).
4. Score **multimodal par réseau** (structurel + FC).
5. Couche d'**interprétabilité** reliant le score global aux régions contributrices.
