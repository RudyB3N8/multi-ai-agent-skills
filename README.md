# Antigravity Skills

Bienvenue dans mon dépôt de compétences (skills) personnalisées pour **Google Antigravity**, l'assistant IA de codage.

Ce dépôt sert à stocker, versionner et partager les différentes compétences que je crée pour étendre les capacités d'Antigravity.

## 🚀 Compétences disponibles

*   **[Créateur de compétences (`createur-de-competences`)](./createur-de-competences/SKILL.md)** : Compétence universelle (méta-compétence) pour concevoir, structurer et générer de nouvelles compétences multi-IA (Google Antigravity, GitHub Copilot, ChatGPT/Codex) selon le standard Open Agent Skills.
*   **[UI/UX Pro Max (`ui-ux-pro-max`)](./ui-ux-pro-max/SKILL.md)** : Génère des systèmes de design intelligents et recommande des styles UI, palettes de couleurs et typographies adaptés à chaque projet.
*   **[Grill-Me (`grill-me`)](./grill-me/SKILL.md)** : Mène une interview technique approfondie et contradictoire (grilling) pour explorer les alternatives d'architecture, débusquer les angles morts et verrouiller le design avant de coder.
*   **[Assistant Aura.build (`aura-build-assistant`)](./aura-build-assistant/SKILL.md)** : Assiste l'utilisateur dans la conception de prompts optimisés pour l'IA d'Aura.build et dans l'importation propre du code généré (HTML, Tailwind CSS, JS) dans un dossier de staging local, avec option d'extraction SCSS.

## 🛠️ Structure d'une compétence

Chaque compétence (skill) est stockée dans son propre dossier et contient au minimum :

*   `SKILL.md` : Le fichier principal contenant les instructions, le frontmatter YAML (nom, description) et le comportement attendu de l'agent.
*   (Optionnel) `scripts/` : Des scripts utilitaires pour étendre les capacités de la compétence.
*   (Optionnel) `examples/` : Des exemples d'implémentation ou de modèles pour guider l'agent (comme le `code-reviewer` dans le créateur de compétences).
*   (Optionnel) `resources/` : Des ressources supplémentaires (fichiers de configuration, templates, etc.).

## 💡 Comment utiliser ces compétences

Pour utiliser ces compétences avec votre propre instance d'Antigravity :

1.  Clonez ce dépôt dans votre dossier de compétences Antigravity (par défaut, il s'agit souvent de `<chemin_vers_appDataDir>/skills`).
2.  Assurez-vous qu'Antigravity a accès en lecture à ce dossier.
3.  Antigravity détectera automatiquement les dossiers contenant un fichier `SKILL.md` valide et pourra s'en servir lorsque le contexte de votre tâche s'y prêtera.

---
*Dépôt généré et maintenu avec l'aide d'Antigravity.*
