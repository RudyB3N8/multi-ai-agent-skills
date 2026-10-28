# Bonnes Pratiques de Rédaction pour AGENTS.md

Ce guide détaille les principes fondamentaux pour concevoir un fichier `AGENTS.md` hautement efficace, frugal en tokens et directement exploitable par tous les agents IA de codage modernes.

---

## 1. Différence fondamentale : README.md vs AGENTS.md

| Critère | `README.md` (Humains) | `AGENTS.md` (Agents IA) |
| :--- | :--- | :--- |
| **Cible** | Développeurs, contributeurs, recruteurs | Modèles de langage et agents autonomes |
| **Style** | Didactique, explicatif, soigné visuellement | Télégraphique, déclaratif, factuel, structuré |
| **Contenu** | Badges, captures d'écran, tutoriels pas-à-pas | Commandes exactes, flags non interactifs, interdits stricts |
| **Tolérance au verbiage** | Acceptable (intro, motivation, storytelling) | Zéro tolérance (chaque mot consomme du contexte) |

---

## 2. Le principe d'économie de tokens (*Token-Efficiency*)

Le fichier `AGENTS.md` est généralement chargé à l'initialisation de chaque session d'agent ou inclus de façon répétée dans les prompts système.

* **Taille cible optimale :** Entre **50 et 130 lignes** (soit environ 400 à 900 tokens).
* **Au-delà de 150 lignes :** Le fichier commence à diluer les instructions critiques et à gaspiller le budget de contexte de l'agent.
* **Privilégier la concision :**
  * Remplacer les longs paragraphes par des listes à puces à un seul niveau ou des tableaux synthétiques.
  * Bannir les formules de politesse ou les introductions narratives ("Dans le cadre de ce projet, notre équipe s'efforce de...").
  * Utiliser des formulations directes : *"Format de date : ISO-8601 uniquement"*.

---

## 3. Les 5 Anti-patterns majeurs à proscrire

### 1. Les conseils génériques creux
* ❌ *Mauvais :* "Écris du code propre, lisible, modulaire et performant." *(L'agent est déjà entraîné pour cela ; cela consomme des tokens sans valeur ajoutée).*
* ✅ *Efficace :* "Fonctions limitées à 30 lignes max. Pas d'états partagés mutables."

### 2. Les commandes interactives ou bloquantes
Les agents s'exécutent dans des sous-shells non interactifs. Une commande bloquante peut geler la session.
* ❌ *Mauvais :* `npm test` *(Lance Jest en mode watch interactif et attend une saisie clavier).*
* ✅ *Efficace :* `npm test -- --watchAll=false` ou `CI=true npm test`.
* ❌ *Mauvais :* `npx prisma migrate dev` *(Peut demander une confirmation interactive).*
* ✅ *Efficace :* `npx prisma migrate deploy` ou commandes avec `-y` / `--non-interactive`.

### 3. La duplication de la documentation d'API
* ❌ *Mauvais :* Recopier les schémas de 25 endpoints REST ou toute la spec OpenAPI dans `AGENTS.md`.
* ✅ *Efficace :* Indiquer le chemin exact du schéma : *"Spécification OpenAPI : `docs/api/openapi.yaml`"*. L'agent le consultera uniquement s'il en a besoin (divulgation progressive).

### 4. Les règles contradictoires avec l'outillage
Ne pas spécifier dans `AGENTS.md` des règles de formatage qui s'opposent à la configuration de Prettier ou d'ESLint du projet.
* Si le projet a un `.prettierrc`, mentionner simplement : *"Formatage : strict respect du fichier `.prettierrc` via `npm run format:check`"*.

### 5. Les chemins absolus
* Ne jamais mentionner de chemins absolus (ex: `/home/user/dev/projet/src`) car ils cassent la portabilité entre machines, conteneurs Docker et membres de l'équipe. Utiliser impérativement des chemins relatifs à la racine du dépôt.

---

## 4. Multi-agents et interopérabilité

Le nom `AGENTS.md` est le standard de facto adopté par un nombre croissant d'outils :
- **Google Antigravity** : Reconnaît `AGENTS.md` ou `GEMINI.md` à la racine ou dans le workspace pour charger le contexte de règles.
- **OpenAI Codex CLI / ChatGPT** : Scanne la racine du projet à la recherche de `AGENTS.md`.
- **GitHub Copilot** : Utilise `AGENTS.md` comme contexte additionnel pour les instructions de repo.
- **Cursor / Claude Code / Windsurf** : Interprètent directement `AGENTS.md` comme fichier de règles de premier plan.

### En cas de coexistence de fichiers historiques :
Si un projet contient déjà un `GEMINI.md`, `CLAUDE.md` ou `.cursorrules` :
1. Centraliser les règles socles dans `AGENTS.md`.
2. Conserver les fichiers historiques uniquement s'ils exploitent des fonctionnalités hautement spécifiques à leur plateforme (ex: balises XML spécifiques de Claude ou format JSON propriétaire de Cursor).
3. Faire pointer ces fichiers vers `AGENTS.md` pour éviter toute désynchronisation.
