# Spécificités Google Antigravity

Ce document de référence rassemble les règles, conventions et bonnes pratiques propres à l'écosystème **Google Antigravity (AGY)** pour la conception et le déploiement de compétences (`skills`).

---

## 1. Emplacements de découverte et priorités

Antigravity découvre automatiquement les compétences en parcourant l'arborescence des dossiers selon l'ordre de précédence suivant (du plus prioritaire au moins prioritaire) :

1. **Compétences du projet (Workspace Project)** :
   - Chemin standard : `.agents/skills/<nom>/` (à la racine du projet ou dans les dossiers parents jusqu'à la racine Git).
   - Variantes tolérées : `.agent/skills/`, `_agents/skills/`.
   - *Usage : Compétences partagées avec l'équipe via le contrôle de version (Git).*

2. **Compétences déclarées dans les configurations** :
   - Fichiers `skills.json` ou `plugins.json` dans le workspace.

3. **Compétences globales (Machine / Utilisateur)** :
   - Chemin par défaut : `~/.gemini/config/skills/<nom>/`
   - *Usage : Compétences personnelles de l'utilisateur accessibles dans tous les espaces de travail Antigravity.*

4. **Compétences intégrées (Built-in)** :
   - Compétences natives fournies par l'IDE Antigravity.

---

## 2. Principes clés d'Antigravity

### A. Divulgation progressive (Progressive Disclosure)
- L'IDE Antigravity n'injecte au départ que le `name` et la `description` des compétences disponibles dans le prompt de base de l'agent.
- Le fichier `SKILL.md` complet n'est chargé en mémoire que si l'agent décide d'activer la compétence (matching sémantique via la description) ou si l'utilisateur l'invoque.
- **Règle pour la description :** Rédiger la description à la **3ème personne** avec des mots-clés d'intention clairs (ex: *"Génère des tests unitaires...", "Conçoit et optimise des prompts..."*).

### B. Formats de liens dans l'IDE
- Dans l'environnement Antigravity, les liens absolus utilisant le schéma `file:///` sont rendus cliquables dans l'éditeur.
- **Pour une portabilité multi-IA :** Privilégier des liens relatifs (ex: `[mon-script](scripts/mon-script.sh)` ou `references/guide.md`). L'agent Antigravity sait parfaitement résoudre ces chemins relatifs depuis le répertoire de la compétence.

### C. Interactions avec les compétences d'accompagnement
Antigravity dispose de compétences d'aide à la conception :
- `planification` : Permet de générer les artefacts natifs Antigravity 2.0 (`implementation_plan.md`, `task.md`) avant d'exécuter des modifications complexes.
- `brainstorming` : Permet d'explorer les exigences utilisateur avant la conception.

---

## 3. Packaging avancé (Plugins et Hooks)

Au-delà d'un dossier de compétence autonome, Antigravity permet de regrouper plusieurs compétences au sein d'un **Plugin** :
- Répertoire : `plugins/<nom_plugin>/`
- Fichier descripteur : `plugin.json` (métadonnées, déclaration des skills et MCP servers).
- Déclencheurs de cycle de vie : `hooks.json` (exécute des scripts ou commandes à des étapes clés comme `pre-tool` ou `post-turn`).
