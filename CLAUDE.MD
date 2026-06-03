# CLAUDE.md — Agent de maintenance du vault Obsidian (revue de littérature)

## Rôle

Tu maintiens un **vault Obsidian** qui sert de revue de littérature pour un projet de modélisation normative sur IRM cérébrale. Tu ne lis **jamais** de PDF et tu n'analyses aucun papier toi-même. Ton unique tâche : à partir d'un **bloc de transfert** que je te colle (produit par un autre assistant), tu (1) crées la note du papier et (2) mets à jour toutes les notes-concepts pour tisser les liens.

Tu ne me redemandes pas d'autorisation. Tu n'écris **rien en dehors** de ce que ces instructions prévoient.

---

## Structure du vault

```
Papers/                       ← une note par papier (nom = <id>.md)
Concepts/
├── Themes/                   ← categorie: theme
├── Methodes-categorie/       ← categorie: methode-cat
├── Methodes-detail/          ← categorie: methode-detail
├── Population/               ← categorie: population
├── Type-IRM/                 ← categorie: type-irm
├── Modalites-detail/         ← categorie: modalite-detail
├── Interpretabilite/         ← categorie: interpretabilite
├── Datasets/                 ← categorie: dataset
├── Applications/             ← categorie: application
├── Niveau-score/             ← categorie: niveau-score
└── Usage-score/              ← categorie: usage-score
```

**Correspondance `categorie` → dossier** (utilise-la pour situer/créer chaque note-concept) :

| `categorie`         | Dossier                       |
|---------------------|-------------------------------|
| `theme`             | `Concepts/Themes/`            |
| `methode-cat`       | `Concepts/Methodes-categorie/`|
| `methode-detail`    | `Concepts/Methodes-detail/`   |
| `population`        | `Concepts/Population/`        |
| `type-irm`          | `Concepts/Type-IRM/`          |
| `modalite-detail`   | `Concepts/Modalites-detail/`  |
| `interpretabilite`  | `Concepts/Interpretabilite/`  |
| `dataset`           | `Concepts/Datasets/`          |
| `application`       | `Concepts/Applications/`      |
| `niveau-score`      | `Concepts/Niveau-score/`      |
| `usage-score`       | `Concepts/Usage-score/`       |

Le **nom de fichier** d'une note-concept = la valeur `concept` + `.md` (ex. `concept: "GPR"` → `GPR.md`). Obsidian résout `[[GPR]]` par nom de fichier quel que soit le dossier ; garde donc les noms **uniques** dans tout le vault.

---

## Entrée : le bloc de transfert

Je te colle un bloc délimité par `--- DÉBUT HANDOFF ---` et `--- FIN HANDOFF ---`, contenant :
1. un bloc ```markdown``` = la **note complète du papier** (à sauver telle quelle) ;
2. un bloc ```yaml``` `liens:` = la liste des concepts à relier, chacun avec `concept`, `categorie`, `usage`.

---

## Procédure (exécute dans cet ordre)

### Étape 1 — Note du papier
1. Lis le champ `id` dans le YAML de la note.
2. Écris le contenu markdown **verbatim** dans `Papers/<id>.md`.
   - Si le fichier existe déjà → c'est une ré-analyse : **écrase** la note et signale-le dans le rapport final.

### Étape 2 — Notes-concepts (pour chaque entrée de `liens`)
Pour chaque concept :
1. Détermine le chemin : `<dossier de la categorie>/<concept>.md`.
2. **Si la note-concept n'existe pas**, crée-la avec le gabarit ci-dessous.
   - Pour la section « C'est quoi » : si tu connais le concept avec certitude (méthode, modalité, dataset standard), écris une **définition neutre d'1 à 3 phrases**. Sinon, écris exactement : `> [!todo] Définition à rédiger.`
3. **Ajoute le papier** sous la section `## Papiers` :
   - Ligne à insérer : `- [[<id>]] — <usage>`
   - **Idempotence** : si une ligne commençant par `- [[<id>]]` existe déjà dans la section, **remplace-la** par la nouvelle (ne crée pas de doublon).
   - Insère les lignes en gardant l'ordre alphabétique des `id` (facultatif mais préféré).
4. **Ne touche jamais** à la section « C'est quoi » d'une note existante, ni à son YAML, ni à aucun autre contenu. Tu n'ajoutes/modifies que des lignes sous `## Papiers`.

### Étape 3 — Rapport
Termine par un résumé en 3 lignes :
```
Papier : Papers/<id>.md (créé | écrasé)
Concepts créés : [[…]], [[…]]
Concepts mis à jour : [[…]], [[…]], …
```

---

## Gabarit d'une note-concept (création uniquement)

```markdown
---
type: concept
categorie: <categorie>
---

# <concept>

## C'est quoi
<définition neutre 1–3 phrases, ou « > [!todo] Définition à rédiger. »>

## Papiers
- [[<id>]] — <usage>
```

---

## Garde-fous (à ne jamais enfreindre)

- Tu n'écris **que** dans `Papers/` et `Concepts/`. Aucun autre dossier.
- Tu ne supprimes **jamais** de note ni de ligne (sauf remplacer une ligne `- [[<id>]]` existante par sa version à jour, cf. idempotence).
- Tu ne modifies **jamais** la définition (« C'est quoi ») d'une note-concept existante.
- Tu ne crées **que** les notes-concepts listées dans `liens` — pas d'autres.
- Si une `categorie` est inconnue (absente du tableau), ne devine pas : signale-la dans le rapport et n'écris pas cette note.
- Le `usage` est recopié **fidèlement** depuis le bloc de transfert ; tu ne le réécris pas.
- Encodage UTF-8, fins de ligne `\n`, pas de reformatage des notes existantes.