# Clamly Help

Source for [help.clamly.app](https://help.clamly.app), the user guides for [Clamly](https://clamly.app). Built with [Mintlify](https://mintlify.com): `docs.json` is the site config, every page is an `.mdx` file, and `style.css` adds the Clamly look on top of the `maple` theme.

Mintlify ignores this README, so it never becomes a page.

## Preview and check

```bash
npm i -g mint        # Mintlify CLI
mint dev             # local preview at http://localhost:3000
mint validate        # docs.json and MDX must parse
mint broken-links    # every internal link must resolve
```

Publishing happens through the Mintlify GitHub app: every push to the deploy branch (`main`) goes live at help.clamly.app.

## Layout

| Path | What it holds |
| --- | --- |
| `docs.json` | Theme, colours, fonts, navbar, footer, sidebar navigation |
| `style.css` | Paper-and-periwinkle touches the config cannot express |
| `index.mdx` | The help home page |
| `getting-started/`, `study/`, `ai/`, `together/`, `progress/`, `account/`, `privacy/`, `help/` | One folder per sidebar group (English) |
| `ro/`, `de/`, `fr/` | Romanian, German and French, mirroring the English tree page for page |
| `sources/` | Pages scraped from clamly.app, kept for reference |

## Languages

English is the default and lives at the root. Every English page has a translation at the same path under `ro/`, `de/` and `fr/`, and `docs.json` lists all four under `navigation.languages`, each with its own sidebar group names, navbar and footer.

- **Change an English page, change its three translations in the same commit.** A translation that describes last month's app is worse than none.
- **UI labels stay in English** in every language, in bold, because the Clamly app itself is English-only. Translate the sentence around them, not the button.
- **Error messages stay in English** too, quoted exactly as the app shows them, so people can match what is on their screen.
- **Translated pages link to pages in their own language** (`/de/ai/usage`, never `/ai/usage`) and link to whole pages, not `#anchors`, because translated headings produce different anchor ids.
- French uses non-breaking spaces before `? ! : ;` and inside « ». German quotes are „…“, Romanian „…”.

Old URLs from the previous version of this site (`/introduction`, `/study-tools/*`, `/collaboration/*` and so on, in all four languages) redirect to their new pages through `redirects` in `docs.json`.
| `logo/` | The `clamly help` wordmark, drawn from Junicode glyph outlines so it needs no font |
| `fonts/` | Junicode, copied from `apps/web/public/` in the Clamly repo |
| `icons/` | Phosphor duotone icons (MIT), filled `#6477E0` so they read in light and dark mode |

## Brand

Same tokens as `apps/web/src/app/globals.css` in the Clamly repo.

| Token | Value | Used for |
| --- | --- | --- |
| Periwinkle | `#8DA2FB` | Brand colour, dark-mode links, wordmark |
| Periwinkle ink | `#4A5CC0` | Light-mode links and buttons. `#8DA2FB` is only 2.1:1 on the cream background; this is 5.1:1 |
| Paper | `#F2F0E3` | Light background |
| Ink | `#191919` | Dark background |
| Junicode | self-hosted | Headings |
| Bricolage Grotesque | Google Fonts | Body text |

## Writing rules

These follow the rules the Clamly app holds its own copy to.

- **No em-dashes.** Use a colon, a comma or a new sentence.
- **Second person** for instructions. Where the founder speaks (contact, FAQ), **first person singular**: Clamly is built by one student, not a team.
- **Name UI labels exactly as the app shows them**, in bold: **Generate Quiz**, not "the generate button".
- **Phosphor icons only**, never sparkle or star icons. Mintlify's sidebar only accepts Font Awesome, Lucide or Tabler, so the sidebar has no icons; cards use the SVGs in `icons/`.
- **Every number comes from the code.** Prices, limits and costs are copied from the Clamly repo, not from memory. When one changes there, change it here.

## Keeping in sync with Clamly

Where each page's facts live in the [Clamly repo](https://github.com/MrLamaker/Clamly):

| Page | Source of truth |
| --- | --- |
| `account/plans-and-billing`, `ai/usage` | `packages/shared/src/constants/index.ts` (`PLANS`, `UPLOAD_LIMITS`, `RAG_RETRIEVAL_LIMITS`), `apps/web/src/components/pricing-tiers.tsx` |
| `ai/usage`, `ai/chat` (unit costs) | `apps/api/src/routes/ai.routes.ts` (`tryConsumeAiUsage` calls), `apps/api/src/services/plan.service.ts` (`getChatMessageCost`), `apps/api/src/services/chat.service.ts` |
| `ai/overview` (coverage) | `AI_COVERAGE_POLICIES` and `AI_DOC_CHAR_LIMITS` in `packages/shared/src/constants/index.ts` |
| `ai/study-pack`, `ai/study-planner` | `STUDY_PACK_*` and `STUDY_PLANNER_*` in `packages/shared/src/constants/index.ts`, `EARLY_FEATURES` in `apps/api/src/lib/early-access.ts` |
| `ai/chat` (modes) | `PERSONALITY_BLOCKS` in `apps/api/src/services/chat.service.ts` |
| `study/quizzes` | `QUIZ_MODES` in `packages/shared/src/constants/index.ts`, `packages/shared/src/utils/import.ts` |
| `study/flashcards` | `apps/web/src/app/(dashboard)/dashboard/flashcards/page.tsx`, `apps/api/migrations/2026-09-21-flashcards-fsrs.sql` |
| `study/notes` | `apps/web/src/components/notes/`, `NOTE_ASSIST_LANGUAGES` in `packages/shared/src/validators/index.ts` |
| `study/exams` | `apps/api/src/services/google-calendar.service.ts` |
| `progress/streaks-and-achievements` | `ACHIEVEMENTS` in `packages/shared/src/constants/index.ts`, `apps/api/src/services/streak.service.ts` |
| `together/groups` | `apps/api/src/services/group-permissions.ts` |
| `account/sign-in-and-security` | `twoFactor(...)` in `apps/api/src/auth.ts`, `apps/web/src/components/settings/two-factor-section.tsx` |
| `account/settings` | `apps/web/src/app/(dashboard)/dashboard/settings/page.tsx` |
| `account/pearl` | `apps/pearl/src/app/rules/page.tsx` |
| `privacy/*` | `apps/web/src/app/privacy/page.tsx` and `docs/dpia.md` |
| `account/plans-and-billing` (refunds) | `apps/web/src/app/terms/page.tsx` |
