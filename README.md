# Multi-AI Agent Skills

Bienvenue dans mon dépôt de compétences (**skills**) universelles pour agents IA de codage, compatibles avec **Google Antigravity**, **GitHub Copilot** et **OpenAI ChatGPT / Codex**.

Ce dépôt sert à concevoir, versionner et centraliser mes compétences selon le standard ouvert [Open Agent Skills](https://agentskills.io), afin d'étendre les capacités de mes assistants de développement sur tous mes environnements et projets.

---

## 🚀 Compétences disponibles

* **[Créateur de compétences (`createur-de-competences`)](./createur-de-competences/SKILL.md)** : Méta-compétence universelle pour concevoir, structurer et générer de nouvelles compétences multi-IA. Intègre un protocole de cadrage interactif dynamique par Rounds (fondé sur les 4 piliers de la *Definition of Ready*) et des fiches techniques modulaires dans son dossier `references/`.
* **[Grill-Me (`grill-me`)](./grill-me/SKILL.md)** : Mène une interview technique approfondie et contradictoire (inspirée de la méthode *AI Hero*) pour challenger une idée, explorer 2 à 3 alternatives d'architecture, débusquer les angles morts et verrouiller le design avant d'écrire la moindre ligne de code.
* **[UI/UX Pro Max (`ui-ux-pro-max`)](./ui-ux-pro-max/SKILL.md)** : Génère des systèmes de design intelligents et recommande des styles UI, des palettes de couleurs harmonieuses et des typographies adaptées à chaque type de produit.
* **[Générateur AGENTS.md (`agents-md-generator`)](./agents-md-generator/SKILL.md)** : Génère, audite et structure un fichier `AGENTS.md` standardisé à la racine d'un projet pour guider les agents IA (Antigravity, Copilot, Codex, Claude Code, Cursor). Détecte automatiquement la stack technique et formalise les commandes non interactives et conventions de code.
* **[Assistant Aura.build (`aura-build-assistant`)](./aura-build-assistant/SKILL.md)** : Assiste dans la conception de prompts optimisés pour l'IA d'Aura.build et dans l'importation propre du code généré (HTML, Tailwind CSS, JS) dans un dossier de staging local, avec option d'extraction SCSS.

---

## 🛠️ Structure d'une compétence

Chaque compétence est un package autonome logé dans son propre répertoire et structuré selon les meilleures pratiques du standard Open Agent Skills :

```text
nom-de-la-competence/
├── SKILL.md                 # (Obligatoire) Instructions principales, frontmatter YAML et déclencheurs
├── README.md                # (Optionnel) Documentation pour les développeurs humains
├── references/              # (Optionnel) Fiches techniques statiques chargées à la demande (Progressive Disclosure)
├── scripts/                 # (Optionnel) Scripts utilitaires exécutables (Bash, Python, etc.)
├── resources/               # (Optionnel) Templates, schémas JSON, snippets
└── examples/                # (Optionnel) Implémentations de référence ou exemples de résultats
```

### Frontmatter YAML universel
```yaml
---
name: nom-de-la-competence
description: Description courte à la 3ème personne avec mots-clés d'activation au début.
allowed-tools: shell       # Optionnel (reconnu par GitHub Copilot)
license: MIT               # Optionnel
---
```

---

## 💡 Comment utiliser ces compétences

Toutes les compétences de ce dépôt respectent des règles strictes de portabilité (chemins relatifs, formulations agnostiques des outils) et peuvent être installées indifféremment sur vos outils :

### 1. Avec Google Antigravity
- **Global (Machine) :** Clonez ou liez ce dépôt dans `~/.gemini/config/skills/` (ou `<appDataDir>/skills`).
- **Projet (Workspace) :** Placez la compétence dans `.agents/skills/<nom>/`.
- Antigravity découvrira automatiquement le fichier `SKILL.md` et activera la compétence selon le contexte ou vos demandes.

### 2. Avec GitHub Copilot (Cloud Agent, CLI, VS Code)
- **Projet :** Placez la compétence dans `.agents/skills/<nom>/` (recommandé) ou `.github/skills/<nom>/`.
- **Personnel / Global :** Placez la compétence dans `~/.agents/skills/<nom>/` ou `~/.copilot/skills/<nom>/`.
- Invoquez-la avec `@nom-de-la-competence` dans le chat Copilot ou laissez l'agent l'activer automatiquement.

### 3. Avec OpenAI ChatGPT & Codex (Desktop, Web, CLI)
- **Projet :** Placez la compétence dans `.agents/skills/<nom>/` (Codex scanne du répertoire courant jusqu'à la racine Git).
- **Utilisateur :** Placez la compétence dans `~/.agents/skills/<nom>/`.
- Invoquez-la avec `@nom-de-la-competence` (ChatGPT) ou `$nom-de-la-competence` / `/skills` (Codex CLI).

---

*Dépôt maintenu et versionné pour l'ingénierie assistée par IA.*
