# Modèle de référence : AGENTS.md

> Ce template sert de structure de départ pour générer un fichier `AGENTS.md` percutant, synthétique et optimisé pour la consommation de tokens par les agents IA. Les sections entre crochets `[...]` doivent être personnalisées selon le projet.

---

```markdown
# Instructions du Projet pour les Agents IA

## 1. Contexte & Architecture
- **Description :** [Courte description en 2-3 phrases de la finalité du projet et du domaine métier].
- **Stack principale :** [Ex: TypeScript 5.x, Node.js 20+, React 18, TailwindCSS, PostgreSQL / Prisma].
- **Architecture :** [Ex: Monorepo Turborepo / Clean Architecture / Architecture modulaire en microservices].
- **Arborescence clé :**
  - `src/core/` : [Cœur de logique métier]
  - `src/components/` : [Composants UI réutilisables]
  - `src/server/` : [API et accès base de données]
  - `tests/` : [Suites de tests unitaires et intégration]

## 2. Commandes Vitales
> Toutes les commandes doivent s'exécuter en mode non interactif et silencieux.

| Action | Commande | Notes / Contexte |
| :--- | :--- | :--- |
| **Installation** | `npm install` | Utiliser impérativement `npm ci` en CI |
| **Lancement Dev** | `npm run dev` | Serveur local accessible sur `http://localhost:3000` |
| **Tests complets**| `npm test -- --watchAll=false` | Ne jamais lancer en mode watch interactif |
| **Test unitaire ciblé** | `npm test -- path/to/file.test.ts` | Privilégier le ciblage de fichier pendant le dev |
| **Linting & Check** | `npm run lint` | Valide ESLint et le typage TypeScript (`tsc --noEmit`) |
| **Formatage** | `npm run format:check` | Prettier en vérification sans écriture |
| **Build Prod** | `npm run build` | Vérifie l'intégrité globale du bundle |

## 3. Conventions de Code & Standards
- **Typage & Rigueur :** [Ex: Strict mode TypeScript activé. Bannir `any`, préférer `unknown` avec type guards].
- **Paradigme :** [Ex: Fonctions pures et composants fonctionnels, immutabilité des états].
- **Gestion d'erreurs :** [Ex: Utiliser le pattern Result ou des classes d'erreur applicatives dédiées. Pas de `console.log` en production].
- **Nommage :**
  - Fichiers et dossiers : `kebab-case` (ou `PascalCase` pour les composants UI).
  - Variables et fonctions : `camelCase`.
  - Types et interfaces : `PascalCase` (ne pas préfixer les interfaces par `I`).
- **Imports :** [Ex: Utiliser impérativement les alias configurés (`@/components/...`) plutôt que des chemins relatifs profonds `../../`].

## 4. Garde-fous & Sécurité (Ce qu'il faut TOUJOURS / JAMAIS faire)
- ❌ **JAMAIS :** Ne jamais commiter de secrets, clés API ou fichiers d'environnement (`.env*`).
- ❌ **JAMAIS :** Ne jamais modifier directement les fichiers de schéma générés automatiquement (ex: `prisma/schema.prisma` -> passer par les migrations).
- ❌ **JAMAIS :** Ne pas ajouter de nouvelles dépendances npm sans confirmation explicite de l'utilisateur ou sans scanner de sécurité.
- ❌ **JAMAIS :** Ne pas désactiver les règles ESLint ou les vérifications de type via des commentaires de suppression (`@ts-ignore`, `eslint-disable`) sans justification technique documentée.
- ✅ **TOUJOURS :** Exécuter les tests ciblés et le linter avant de valider toute modification de code.
- ✅ **TOUJOURS :** Préserver les commentaires et la documentation existante dans les fichiers modifiés.

## 5. Workflow de validation (Définition de Terminé / DoD)
Avant de considérer une tâche comme achevée et de notifier l'utilisateur :
1. Vérifier que le code compile sans avertissement ni erreur de types.
2. Exécuter les tests unitaires couvrant les fichiers modifiés et s'assurer qu'ils passent tous avec succès.
3. Vérifier le formatage et le linting.
4. Fournir un résumé concis des modifications accompagnées des liens vers les fichiers impactés.
```
