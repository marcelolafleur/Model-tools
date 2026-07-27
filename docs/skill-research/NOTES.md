# Skill Research Lab

Started: 2026-07-27, branch `skill-research-lab`

Goal: identify and collect the most advanced/useful Claude Code skills for all
aspects of Marcelo's work, grounded in what the local repos actually need.

## Research streams

1. **Local needs survey** — scan of ~/Projects to characterize recurring work
   and friction points → candidate skill needs.
2. **Nate Herk / AI Automation Society** — evaluate his free skill collection
   (youtube.com/@nateherk, skool.com/ai-automation-society).
3. **Ecosystem map** — official (anthropics/skills) and major community
   collections; ranked shortlist for this user.

## Findings

### Stream 1: Local needs survey (complete, 2026-07-27)

~119 top-level dirs, ~120 GB. Seven clusters: (1) OG-Core country models —
center of gravity, ~40 dirs; (2) ogclews-link energy coupling + MUIO/OGUI;
(3) og-lab AI-accelerated tooling (JAX, emulator, LLM country-builder);
(4) SDG/LLM classification (huge, dormant, worst-organized); (5) Genealogy
engine + ancestra venture (mature); (6) UN DESA publications/admin (WSR,
DESA-groups entity base, ePAS); (7) one-offs (photofix, wingman, TV pilot,
financial, soccer).

**Top friction points found:**
- Manual model-run preflight (import shadowing burned a full battery 2026-07-07;
  the ritual lives as prose in ~/.claude/CLAUDE.md and ogclews AGENTS.md)
- Solver-convergence debugging reinvented ad hoc (og-country-tests: 2.9 GB of
  `*_J1_*` bisect scripts and 15 hand-named logs)
- Fleet-wide change propagation across ~20 country repos by hand
  (PANDAS3_IMPORT_FIX_PLAYBOOK.md is a written instance; conda→uv drift is the
  cost of not having it)
- Checkout sprawl: 22 registered worktrees + `_bak`/`copy`/`holding pen` dirs
- Calibration provenance: 24 loose notebooks derive params later hard-coded
  into country repos with no trace back to sources
- `un_api_token.txt` sitting in the working trees of 3+ repos
- Every scenario run terminates in the same hand-built baseline-vs-reform
  charts/tables/narrative deliverable
- 23 near-duplicate AGENTS.md briefs drifting; no .claude/skills, agents,
  commands, or hooks in any repo
- Three separate LaTeX pipelines (ogclews slides/paper, family book) with
  committed build litter
- Annual ePAS/accomplishment report rebuilt from scratch 6 years running

The survey's 15 ranked candidate skills are folded into the shortlist below.

### Stream 2: Nate Herk / AI Automation Society (complete, 2026-07-27)

**Who:** n8n-automation YouTuber (30M+ views) who pivoted hard to Claude Code in
late 2025. Runs the free AI Automation Society on Skool (~400K members) and a
paid "Plus" tier (~$99-129/mo) that is an agency-building program, not deeper
technical content.

**The free skills** (real SKILL.md-format, MIT, public GitHub, no signup):
- [AIS-OS](https://github.com/nateherkai/AIS-OS) (~1K stars) — "AI Operating
  System" starter kit: 3 skills (`/onboard` interview wizard, `/audit` weekly
  gap analysis, `/level-up` weekly automation-opportunity interview) wrapped
  around trademarked "Three Ms" / "Four Cs" frameworks.
- [a-bunch-of-skills](https://github.com/nateherkai/a-bunch-of-skills) —
  3 skills: `infographic-builder` (hard-wired to his brand + KIE AI key),
  `skill-builder` (overlaps Anthropic's skill-creator), `visualizations`
  (Excalidraw-style explainer PNGs via image gen).
- [token-dashboard](https://github.com/nateherkai/token-dashboard) (647 stars)
  — Python tool turning Claude Code JSONL transcripts into local token/cost
  analytics. Arguably his most useful repo for a power user.

**Verdict: mostly skippable.** Correctly-built but beginner/solopreneur-oriented;
six skills total, nothing for economics modeling, data science, or document
pipelines. Possible keepers: `token-dashboard` (tool, not skill) and maybe
`visualizations` as a niche recipe. His n8n template library is irrelevant to a
Claude Code workflow.

### Stream 3: Ecosystem map (complete, 2026-07-27)

**Official:**
- [anthropics/skills](https://github.com/anthropics/skills) — canonical repo:
  document skills (docx/pdf/pptx/xlsx), example skills (mcp-builder,
  webapp-testing, canvas-design, claude-api), Agent Skills spec + template.
- [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official)
  — curated plugin directory, pre-configured in Claude Code; LSP plugins,
  code-review, security-review, etc. Browse via `/plugin` → Discover.
- Authoring reference: docs.claude.com agent-skills best-practices.

**Top community collections:**
- [pedrohcgs/claude-code-my-workflow](https://github.com/pedrohcgs/claude-code-my-workflow)
  — **best single match**: Pedro Sant'Anna (Emory econ), 52 skills / 18 agents
  for academics: /lit-review, /review-paper --peer, /simulation-study,
  /audit-reproducibility, /respond-to-referees, AEA replication compliance,
  LaTeX/Beamer + R.
- [obra/superpowers](https://github.com/obra/superpowers) — the gold standard
  for engineering-discipline skills (systematic-debugging, using-git-worktrees,
  writing-skills, TDD, verification-before-completion). Overlaps fable-mode/tdd
  in places; cherry-pick.
- [K-Dense-AI/claude-scientific-skills](https://github.com/K-Dense-AI/claude-scientific-skills)
  — 154 "AI Scientist" skills; economist-relevant subset: EDA, statsmodels /
  scikit-learn / PyMC / SHAP, time-series forecasting, Polars/Dask, GeoPandas,
  scientific writing. Per-skill install via `npx skills add`.
- [ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills)
  — 1000+ skill directory; broad not strict. [travisvn list](https://github.com/travisvn/awesome-claude-skills)
  is tighter. [VoltAgent](https://github.com/VoltAgent/awesome-claude-code-subagents)
  for subagents.
- [trailofbits/skills](https://github.com/trailofbits/skills) — reputable
  security-audit skills.

**Niche picks relevant to Marcelo:** [claude-deep-research-skill](https://github.com/199-biotechnologies/claude-deep-research-skill)
(8-phase research, source credibility scoring), [hameefy/claude-latex-skill](https://github.com/hameefy/claude-latex-skill),
[SNL-UCSB/paper-writing-skill](https://github.com/SNL-UCSB/paper-writing-skill),
[tapestry](https://github.com/michalparkola/tapestry-skills-for-claude-code)
(document-collection knowledge networks), [sliday/genealogy-research](https://github.com/sliday/genealogy-research)
(GPS methodology, 80+ databases), [flonat/flonat-research](https://github.com/flonat/flonat-research)
(academic infra patterns).

**Quality criteria** (for vetting anything before install): progressive
disclosure (SKILL.md < ~500 lines, references split out), precise *when-to-use*
trigger descriptions, bundled scripts over prose for deterministic work,
non-obvious process knowledge only, ideally evals. Read third-party SKILL.md +
scripts before installing — they run with your permissions.

**Tooling:** `/plugin marketplace add <owner/repo>`; Vercel `npx skills add
<owner/repo>` / `npx skills find` (cross-agent, skills.sh directory);
`gh skill install` (gh CLI ≥2.90); spec at agentskills.io.

**Already covered by current setup (skip):** Anthropic document skills, dataviz,
skill-creator, code-review/pr-review-toolkit, CLAUDE.md management, memory-bank
skills (built-in memory covers it).

## Shortlist (synthesis: needs × availability)

### Tier 1 — Collect now (external, high fit, reputable)

1. **pedrohcgs/claude-code-my-workflow** — Pedro Sant'Anna's 52-skill academic
   econ template (/lit-review, /review-paper --peer, /simulation-study,
   /audit-reproducibility, /respond-to-referees, LaTeX/Beamer + R). Directly
   serves the paper/report/simulation loop; also a pattern library for our own
   OG skills. https://github.com/pedrohcgs/claude-code-my-workflow
2. **superpowers cherry-picks** (obra) — `systematic-debugging` (→ the J1-style
   solver-debugging loop), `using-git-worktrees` (→ the 22-worktree sprawl),
   `verification-before-completion`, `writing-skills`. Skip the TDD/planning
   ones that overlap fable-mode/tdd. https://github.com/obra/superpowers
3. **K-Dense scientific subset** — exploratory-data-analysis, statsmodels,
   time-series-forecasting, GeoPandas; per-skill `npx skills add`.
   https://github.com/K-Dense-AI/claude-scientific-skills
4. **claude-deep-research-skill** — 8-phase research w/ source credibility
   scoring; UN/policy research and ancestra alike.
   https://github.com/199-biotechnologies/claude-deep-research-skill
5. **hameefy/claude-latex-skill** — compilable LaTeX/Beamer discipline for the
   three LaTeX pipelines. https://github.com/hameefy/claude-latex-skill

### Tier 2 — Evaluate (promising, needs vetting)

- **tapestry** (document-collection → knowledge network) for DESA-groups
  entities/records/maps. https://github.com/michalparkola/tapestry-skills-for-claude-code
- **SNL-UCSB/paper-writing-skill** (draft→evaluate→compress) vs. what
  family-history-narrative already does for prose.
- **trailofbits/skills** — security audit; overkill? but reputable.
- **sliday/genealogy-research** — GPS methodology, 80+ databases; complements
  the prose skills on the research side.
- **flonat/flonat-research** — mine for infra patterns (hooks+rules), not
  necessarily install.
- **nateherkai/token-dashboard** — tool not skill; local token/cost analytics.
- **Nate Herk skills proper** — skip (beginner-oriented; see Stream 2).

### Tier 3 — Build our own (no external equivalent; from the needs survey)

Ranked by frequency × pain × how badly served:
1. `og-run-preflight` — mechanize the mandatory import/branch/venv preflight
2. `og-solver-diagnosis` — structured non-convergence protocol (adapt
   superpowers systematic-debugging as the skeleton)
3. `og-repo-fleet-sync` — one change → N country repos, tracked
4. `og-scenario-report` — baseline/reform outputs → charts+tables+narrative
5. `worktree-orchard` — inventory/reconcile checkout sprawl
6. `calibration-provenance` — trace params back through notebooks to sources
7. `repo-brief-sync` — canonical AGENTS.md + per-repo deltas
8. `un-report-chapter` — WSR/policy .docx loop w/ Zotero UN-resolutions style
9. `gedcom-pipeline` — guard the family-base.ged → enrich → exports invariants
10. `secret-sweep` — token scan before commit/push (wrap gitleaks;
    `un_api_token.txt` currently in 3+ working trees)
11. `epas-cycle`, `desa-thread-to-entities`, `sdg-classify-batch`,
    `latex-deck-build`, `pdf-corpus-extract` — backlog

## Installed / decided

- 2026-07-27: **fable-mode updated** — pulled origin/main revision (Opus 5
  routing table, benchmark-grounded scores), installed to
  `~/.claude/skills/fable-mode/`, verified identical.
- 2026-07-27: **Curation policy adopted — three rings, not install-everything:**
  1. *Global core* (`~/.claude/skills/`): cross-project skills only, cap ~15-20,
     prune when a skill hasn't triggered in months.
  2. *Project-scoped* (each repo's `.claude/skills/`): domain skills live where
     they apply (OG skills → OG repos), so they load only in relevant sessions.
  3. *The shelf* (this repo's `skills/`): the curated, versioned library —
     collected and documented but NOT installed; install on demand per ring 1/2.
  Rationale: every installed skill's description loads into every session
  (trigger pollution + context cost), and skills run with full permissions
  (vet before install). Model-tools is the adjustable curated list.
- 2026-07-27: **OG skill family commissioned** — dedicated session prompt at
  `docs/skill-research/OG-SKILLS-SESSION-PROMPT.md`; will build in a worktree
  on branch `og-skills` under `skills/og/`.
- 2026-07-27: Nate Herk skills — **pass** (see Stream 2); revisit only
  `token-dashboard` (tool).
- 2026-07-27: **OG skill family BUILT** — six skills landed in `skills/og/` on
  branch `og-skills` (Tier-3 items 1–6 of the shortlist): `og-run-preflight`
  (+ `preflight.py`, tested GO on OG-PHL and NO-GO on a deliberately wrong cwd),
  `og-solver-diagnosis` (superpowers systematic-debugging skeleton, credited,
  + failure taxonomy mined from og-country-tests — which turned out to be
  mostly *successful* validation runs, so the taxonomy blends observed classes
  with the documented ZAF fiscal-runaway/oscillation modes), `og-repo-fleet-sync`
  (PANDAS3 playbook generalized; detection sweep dry-run: all 7 repos already
  clean, positive control via ZAF git history), `og-scenario-report`
  (+ `scenario_report.py`, dry-run against OG-PHL-Example; survey confirmed the
  de-facto standard is exactly `macro_table` + `plot_all` and the gaps are
  input-param diagnostics, multi-reform tables, narrative), `worktree-orchard`
  (+ read-only `orchard.py`; found OG-PHL's hidden `.claude/worktrees` worktree),
  `calibration-provenance` (+ notebook map; two chains verified to the digit —
  ZAF gamma live-API drift, r_gov re-centering arithmetic exact). Install policy:
  shelf → project ring per `skills/og/README.md`. **Side-finding to act on:**
  live UN bearer JWTs are hardcoded in cells of `test_pop_api.ipynb`,
  `undata_test.ipynb`, `undata_test-ETH.ipynb`, and
  `notebooks/usaid_testing/un_api_token.txt` is non-empty — rotate/scrub before
  any sharing. Remaining Tier-3 backlog: `repo-brief-sync`, `un-report-chapter`,
  `gedcom-pipeline`, `secret-sweep` (now more urgent given the JWT finding), and
  the rest.
