# Spécificités OpenAI ChatGPT & Codex

Ce document de référence rassemble les conventions et bonnes pratiques propres à l'écosystème **OpenAI ChatGPT** (Desktop, Web, Work) et **Codex** (CLI, IDE) pour la conception de compétences (`skills`).

---

## 1. Emplacements de découverte

ChatGPT et Codex s'appuient sur le standard ouvert [Open Agent Skills](https://agentskills.io) et découvrent les compétences locales selon la hiérarchie suivante :

1. **Compétences au niveau du dépôt (`REPO`)** :
   - `$CWD/.agents/skills/<nom>/` (Répertoire de travail courant)
   - Chemins parents jusqu'à la racine : `$REPO_ROOT/.agents/skills/<nom>/`
   - *Codex explore automatiquement les dossiers parents jusqu'à la racine Git.*

2. **Compétences utilisateur (`USER`)** :
   - `$HOME/.agents/skills/<nom>/` (ou `~/.agents/skills/<nom>/`)
   - *Appliquées à tous les projets sur la machine de l'utilisateur.*

3. **Compétences administratives et système (`ADMIN` / `SYSTEM`)** :
   - `/etc/codex/skills/` (Déployées au niveau machine ou conteneur)

---

## 2. Optimisation du budget de contexte et Description

### A. La règle du budget initial (2% ou 8 000 caractères)
- Au démarrage, Codex charge une liste résumée de toutes les compétences découvertes (`name`, `description`, chemin).
- Cette liste ne doit pas dépasser **2% de la fenêtre de contexte** (ou environ 8 000 caractères).
- Si de nombreuses compétences sont installées, Codex tronque automatiquement la fin des descriptions.

### B. Règle d'or de rédaction : Le "Front-Loading"
- Placez **immédiatement au début de la description** l'objectif principal et les mots-clés déclencheurs majeurs.
- *Exemple recommandé :* `description: Convertit les fichiers SVG en PNG avec redimensionnement automatique. Utilisez lorsque l'utilisateur demande de convertir des images SVG.`
- Évitez les longues introductions superflues au début de la description.

---

## 3. Modes d'invocation

Les compétences peuvent être activées de deux manières :

1. **Invocation implicite (Automatique)** :
   - Le modèle analyse la requête de l'utilisateur et sélectionne la compétence appropriée en la comparant au champ `description`.
2. **Invocation explicite (Manuelle)** :
   - Dans ChatGPT (Desktop / Web / Work) : tapez `@nom-de-la-competence`.
   - Dans Codex CLI et l'extension IDE : tapez `$nom-de-la-competence` ou lancez `/skills`.

---

## 4. Packaging avancé en Plugin OpenAI (`agents/openai.yaml`)

Pour distribuer une compétence au-delà d'un projet local (ex: via le répertoire de plugins universel d'OpenAI pour le Web, le mobile et desktop), vous pouvez intégrer un fichier de configuration dans un sous-dossier `agents/` :

```text
mon-skill/
├── SKILL.md
├── scripts/
├── references/
└── agents/
    └── openai.yaml      # Métadonnées d'affichage, icône, connecteurs MCP
```

Dans `agents/openai.yaml`, vous pouvez définir :
- L'apparence visuelle dans le sélecteur de compétences de ChatGPT.
- Les dépendances vers des serveurs MCP ou des connecteurs tiers.
