# Clamly Help: instructions for AI agents

This is the Mintlify source for [help.clamly.app](https://help.clamly.app), the user guides for Clamly, a study app for students. `README.md` has the full layout, brand tokens and the map from each page to the Clamly source file it mirrors. Read it before editing.

## About this project

- Pages are MDX with YAML frontmatter; configuration is `docs.json`
- Four languages: English at the root, and `ro/`, `de/`, `fr/` mirroring it page for page
- Run `mint validate` and `mint broken-links` before committing

## Terminology

- The product is **Clamly**. The AI features are **Clamly AI** and **Clamly Chat**
- Plans are **Free**, **Starter** and **Pro**
- Name UI labels exactly as the app shows them, in English and in bold, in every language: **Generate Quiz**, **Save as flashcards**, **Cancel subscription**
- Say "AI usage units" for AI costs, never credits or tokens

## Style preferences

- Never use em-dashes or en-dashes. Use a colon, a comma or a new sentence
- Second person ("you") for instructions. Where the founder speaks (contact, FAQ, the home page note), use first person singular: Clamly is built by one student, not a team
- Sentence case for headings
- Icons: Phosphor SVGs from `icons/` only. Never sparkle or star icons
- Every price, limit and cost comes from the Clamly code, never from memory

## Content boundaries

- Do not document removed features (coins, shop, leaderboard, GitHub sign-in) except to say they were removed
- Do not name the AI provider or other sub-processors. The public privacy policy describes them by category
- Do not document admin-only features
- Changing an English page means changing its three translations in the same commit
