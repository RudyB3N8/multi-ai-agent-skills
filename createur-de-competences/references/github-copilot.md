# Spécificités GitHub Copilot

Ce document de référence rassemble les conventions et métadonnées spécifiques à **GitHub Copilot** (Cloud Agent, Copilot CLI, VS Code Agent mode, etc.) pour la création de compétences (`skills`).

---

## 1. Emplacements de découverte

GitHub Copilot prend en charge plusieurs emplacements de répertoires :

1. **Compétences au niveau du projet (Repo-specific)** :
   - `.agents/skills/<nom>/` (Standard recommandé et multi-IA)
   - `.github/skills/<nom>/` (Convention historique GitHub)
   - `.claude/skills/<nom>/` (Compatibilité Claude Code)

2. **Compétences personnelles / globales (Machine-wide)** :
   - `~/.agents/skills/<nom>/` (Standard partagé multi-IA)
   - `~/.copilot/skills/<nom>/` (Spécifique GitHub Copilot)

> **Recommandation :** Privilégier `.agents/skills/<nom>/` (projet) ou `~/.agents/skills/<nom>/` (global) pour garantir que la compétence soit lisible simultanément par Antigravity, Copilot et ChatGPT/Codex.

---

## 2. Métadonnées YAML Frontmatter propres à Copilot

En plus des champs universels `name` et `description`, Copilot supporte les métadonnées optionnelles suivantes :

```yaml
---
name: nom-de-la-competence
description: Description concise avec déclencheurs clairs.
allowed-tools: shell
license: MIT
---
```

### A. Le champ `allowed-tools`
- Permet de pré-approuver les outils nécessaires sans demander de confirmation interactive à l'utilisateur à chaque appel.
- Outils fréquents : `shell` ou `bash`.
- **Règle de sécurité :** N'inclure `allowed-tools: shell` que si vous connaissez et contrôlez l'intégralité des scripts de la compétence. Si omis, Copilot demandera simplement l'approbation manuelle de l'utilisateur avant d'exécuter un terminal.
- *Les autres IA (Antigravity, Codex) ignorent ce champ sans erreur s'il est présent.*

### B. Le champ `license`
- Indique la licence applicable à la compétence (ex: `MIT`, `Apache-2.0`). Particulièrement utile pour les compétences destinées à être publiées ou partagées.

---

## 3. Exécution de scripts dans Copilot

Copilot charge automatiquement tous les fichiers présents dans le répertoire de la compétence et les met à disposition de l'agent.
- Pour exécuter un script localisé dans `scripts/` ou à la racine de la compétence, décrivez la commande dans le corps Markdown en chemin relatif :
  ```markdown
  Pour exécuter l'analyse, lancez le script `./scripts/analyse.sh` depuis le répertoire de la compétence avec le chemin du fichier cible en premier argument.
  ```

---

## 4. Distribution avec GitHub CLI (`gh skill`)

GitHub CLI (version 2.90.0+) intègre la commande native `gh skill` :
- `gh skill search <sujet>` : Recherche de compétences publiques.
- `gh skill preview <owner>/<repo> <skill>` : Inspecte le `SKILL.md` et les fichiers sans installer.
- `gh skill install <owner>/<repo> <skill>` : Installe une compétence dans `.agents/skills` ou `.github/skills`.
- `gh skill update` : Met à jour les compétences installées grâce aux métadonnées de provenance ajoutées automatiquement au frontmatter.
