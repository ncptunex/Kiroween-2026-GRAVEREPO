<img width="1911" height="1040" alt="Screenshot 2026-11-26 132533" src="https://github.com/user-attachments/assets/b8a7c54d-500b-489e-94a0-d1412f944922" /><img width="1912" height="1135" alt="Screenshot 2026-11-26 143014" src="https://github.com/user-attachments/assets/9fb8f519-03d5-44fc-9122-6699a158d94e" /># GRAVEREPO

**Dig up your forgotten code.**

GRAVEREPO turns a GitHub account's public repositories into a small, friendly graveyard. Each repository with no recent updates becomes a tombstone. You can look at the evidence, get a suggested plan for picking it up again, tick off steps as you go, and watch the graveyard grow into a garden.

Inactivity is a signal, not proof. A quiet repository may be finished, stable, paused or moved. GRAVEREPO never says why a repository went quiet, and it never calls one "dead". It shows what GitHub shows, labels its own readings as suggestions, and treats every repository and its owner with respect.

## Project Links

- **Live Demo:** https://graverepo.vercel.app/
- **Demo Video:** [Watch the GRAVEREPO demo on YouTube](https://youtu.be/fCC1IBQNSBU)
- **Development Blog:** [From Forgotten Code to a Digital Graveyard: Building GRAVEREPO with Kiro](https://graverepo.wordpress.com/2026/11/26/from-forgotten-code-to-a-digital-graveyard-building-graverepo-with-kiro/)
- **GitHub Repository:** https://github.com/ncptunex/Kioween-2026-GRAVEREPO

## Screenshots

### Graveyard Dashboard
<img width="1912" height="1135" alt="Screenshot 2026-11-26 143014" src="https://github.com/user-attachments/assets/c492c272-2436-4d9c-9425-e6da0e8a2108" />
<img width="1917" height="1136" alt="Screenshot 2026-11-26 132310" src="https://github.com/user-attachments/assets/964c2fe9-2fe4-4c2b-b156-7685097e7c5e" />
<img width="1916" height="1123" alt="Screenshot 2026-11-26 132333" src="https://github.com/user-attachments/assets/2245b7a1-2fa6-4062-b084-9dfac8afe921" />

### Necropsy
<img width="1911" height="1132" alt="Screenshot 2026-11-26 132424" src="https://github.com/user-attachments/assets/92dacd56-f48a-44b6-b4e4-6f4e79df1000" />
<img width="1836" height="772" alt="Screenshot 2026-11-26 132436" src="https://github.com/user-attachments/assets/13aadd73-7162-4165-872b-75410c551bbf" />

### Resurrection Plan
<img width="1912" height="935" alt="Screenshot 2026-11-26 132446" src="https://github.com/user-attachments/assets/5d458780-e1a8-4fe8-813d-e43108303ef4" />

### Rising
<img width="1915" height="1132" alt="Screenshot 2026-11-26 132505" src="https://github.com/user-attachments/assets/e4cf96c0-ad6f-4572-87a0-bca977d94039" />


### The Living
<img width="1907" height="1126" alt="Screenshot 2026-11-26 132517" src="https://github.com/user-attachments/assets/39dfa52c-bee6-428b-85e1-98e53267e8b7" />
<img width="1911" height="1040" alt="Screenshot 2026-11-26 132533" src="https://github.com/user-attachments/assets/15a598d1-643f-4f67-814d-ecf21ec41168" />



## Features

- **GitHub user and organisation search.** Enter a username or organisation name to list its public repositories. Lists are capped at 300 repositories, and the app says when a list is partial or truncated.
- **Digital Graveyard.** Each repository is a tombstone with a plain-text condition label (for example Resting, Dormant, Archived, Empty or Recently updated) next to the fact behind it, such as the last update date. Status is never shown by colour alone.
- **Necropsy.** The first ritual stage. It lists observable facts about one repository: last update, latest commit, archived or fork status, README, open issues, recent authors, branches, automated checks and dependency file. If something couldn't be checked, it says "couldn't be checked" and never fills in a zero.
- **Resurrection Plan.** A suggested plan built only from what the Necropsy observed, using fixed rules. The same data always gives the same plan. Each step reads "Because {fact}, you could {step}" and traces back to its finding. It is a suggestion, not a diagnosis.
- **Rising.** Your own progress through the plan. You tick steps, and the garden grows to match. Progress is the steps you ticked, not changes GRAVEREPO detected on GitHub.
- **The Living.** Repositories whose ritual you completed. "Revived" is a local label that means you finished the ritual in GRAVEREPO. It does not mean the GitHub repository changed.

## Demo mode

The demo graveyard is always available from the landing screen. It is a bundled snapshot of real public GitHub data, captured by hand and committed to the repository, so it needs no network, no GitHub account and no token.

- You can complete the whole ritual on demo data: Necropsy, Plan, Rising, mark as revived, then see it in The Living. This makes no requests to GitHub.
- It keeps working if your connection drops after the page has loaded.
- It runs through the same validation and conversion code as live data.
- It is always labelled as a demo, with its capture date. It is never presented as the result of a username you searched.

## Privacy and data handling

- **No login.** You never sign in to GitHub, and GRAVEREPO has no accounts of its own.
- **Public data only.** It reads public GitHub information. Private repositories are excluded even if GitHub returns them.
- **Read-only.** GRAVEREPO never edits, fixes or repairs a repository.
- **Local progress.** Your ticked steps and revived repositories are saved in your browser's `localStorage`, on this device only.
- **No backend and no database.** The app is static. The browser talks directly to GitHub.
- **Rate limits.** Live searches use the unauthenticated GitHub REST API, which allows a limited number of requests per hour for each network address. When the limit is reached, GRAVEREPO says so, shows a saved copy if it has one, and points you to the demo.
- **No tracking.** There are no analytics, cookies, remote fonts or third-party assets at runtime. Email addresses are never stored or read.

## Technology

| Area | Choice |
|---|---|
| UI | React 19 |
| Build tool | Vite 8 |
| Language | TypeScript |
| Styling | Plain CSS, with theme tokens in `src/styles/tokens.css` |
| Runtime validation | Zod |
| Tests | Vitest and fast-check (property-based tests) |
| Browser storage | `localStorage` |

Exact versions are in `package.json` and `package-lock.json`.

The code is split into four layers with one-way dependencies:

| Folder | Job |
|---|---|
| `src/data/` | All GitHub communication, validation, saved copies and demo loading |
| `src/ritual/` | Pure rules for conditions, findings, the plan and progress |
| `src/state/` | Application state that connects the layers |
| `src/screens/`, `src/components/` | The interface |

## Getting started

You need Node.js and npm. No GitHub token or environment variables are required.

```bash
git clone https://github.com/ncptunex/Kiroween-2026-GRAVEREPO.git
cd Kiroween-2026-GRAVEREPO
npm install
npm run dev
```

Open the local address that Vite prints. Choose the demo graveyard, or search for a public GitHub username or organisation.

### npm commands

| Command | What it does |
|---|---|
| `npm run dev` | Starts the Vite development server |
| `npm run build` | Type-checks, then builds the production app into `dist/` |
| `npm run preview` | Serves the production build locally |
| `npm run typecheck` | Runs the TypeScript type check without building |
| `npm test` | Runs the test suite once with Vitest |
| `npm run scan-tokens` | Scans the project for GitHub token patterns |
| `npm run capture-demo` | Re-captures the demo snapshot from GitHub. Maintainers only. It reads a token from a local environment variable and needs network access. Not needed to run or build the app. |

Builds and tests never contact GitHub.

## Built with Kiro

GRAVEREPO was built for Kiroween 2026 using Kiro and spec-driven development. The `.kiro` folder is part of the repository.

- **Specs** in `.kiro/specs/` define the work before it is built. Each has requirements, a design and a task list:
  - `github-data-layer`
  - `resurrection-ritual`
  - `graveyard-dashboard`
- **Steering** in `.kiro/steering/` holds the rules Kiro follows on every task:
  - `design-system.md`: visual and interaction direction
  - `voice-and-honesty.md`: wording and honesty rules
  - `tech.md`: technical conventions
- **Hooks** in `.kiro/hooks/` run the token scan when files are saved.
- **Journal.** Daily notes on how Kiro was used are in `docs/kiro-journal.md`. The schedule is in `docs/roadmap.md`.

## Credits

Created by Chan Jie Lin for Kiroween 2026.

## Licence

Released under the [MIT License](LICENSE). Copyright (c) 2026 Chan Jie Lin.
