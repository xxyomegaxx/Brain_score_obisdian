# CLAUDE.md — Vault Obsidian (revue de littérature, modélisation normative IRM)

## Contexte du vault

Ce vault Obsidian sert de **revue de littérature** pour un projet de modélisation
normative sur IRM cérébrale. Tu **ne lis jamais de PDF** et tu **n'analyses aucun
papier** toi-même : l'analyse est faite par un autre assistant, qui produit un
*bloc de transfert*. Ton rôle se limite à **matérialiser ce bloc dans le vault**.

L'ingestion d'un bloc passe par la commande **`/ingest`** (voir
`.claude/commands/ingest.md`). En dehors de cette commande, tu peux répondre à des
questions sur le vault (où se trouve une note, quelle catégorie va dans quel
dossier, etc.) en t'appuyant sur la structure ci-dessous. Tu ne me redemandes pas
d'autorisation pour les opérations prévues, et tu n'écris **rien en dehors** de ce
que ces instructions prévoient.

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

## Correspondance `categorie` → dossier

| `categorie`         | Dossier                        |
|---------------------|--------------------------------|
| `theme`             | `Concepts/Themes/`             |
| `methode-cat`       | `Concepts/Methodes-categorie/` |
| `methode-detail`    | `Concepts/Methodes-detail/`    |
| `population`        | `Concepts/Population/`         |
| `type-irm`          | `Concepts/Type-IRM/`           |
| `modalite-detail`   | `Concepts/Modalites-detail/`   |
| `interpretabilite`  | `Concepts/Interpretabilite/`   |
| `dataset`           | `Concepts/Datasets/`           |
| `application`       | `Concepts/Applications/`       |
| `niveau-score`      | `Concepts/Niveau-score/`       |
| `usage-score`       | `Concepts/Usage-score/`        |

## Règles de nommage

- Le **nom de fichier** d'une note-concept = la valeur `concept` + `.md`
  (ex. `concept: "GPR"` → `GPR.md`).
- Obsidian résout `[[GPR]]` par nom de fichier quel que soit le dossier ; garde
  donc les noms **uniques** dans tout le vault.

---

## Garde-fous (toujours valables)

- Tu n'écris **que** dans `Papers/` et `Concepts/`. Aucun autre dossier.
- Tu ne supprimes **jamais** de note ni de ligne (sauf remplacer une ligne
  `- [[<id>]]` existante par sa version à jour — cf. idempotence dans `/ingest`).
- Tu ne modifies **jamais** la définition (« C'est quoi ») d'une note-concept
  existante, ni son YAML, ni aucun autre contenu hors de la section `## Papiers`.
- Tu ne crées **que** les notes-concepts listées dans le bloc de transfert — pas
  d'autres.
- Si une `categorie` est inconnue (absente du tableau ci-dessus), ne devine pas :
  signale-la dans le rapport et n'écris pas cette note.
- Le `usage` est recopié **fidèlement** depuis le bloc de transfert ; tu ne le
  réécris pas.
- Encodage UTF-8, fins de ligne `\n`, pas de reformatage des notes existantes.