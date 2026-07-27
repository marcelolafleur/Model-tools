# skills/og/ — OG-Core skills for model users

The general-audience OG-Core skills: calibrate a country model, turn a finished run into the
standard deliverable, and explore/visualize/write up results on demand. Built 2026-07-27 from the
needs survey in `docs/skill-research/NOTES.md`; each was tested against real repos and outputs
before committing.

**The full practitioner set lives in the MUIOGO-AI repo** (`.claude/skills/`): it carries these
three *plus* the infrastructure skills for people who develop and maintain the models —
`og-run-preflight` (GO/NO-GO before any run), `og-solver-diagnosis` (root-cause protocol for sick
solves), `og-repo-fleet-sync` (one change across the country-repo fleet), `worktree-orchard`
(checkout-sprawl inventory), and `calibration-provenance` (trace any parameter to its source).
The three skills here are canonical in this repo and mirrored there; the five practitioner skills
are canonical there.

## The skills

| Skill | One line | Bundled script |
|---|---|---|
| [`og-country-calibration`](og-country-calibration/SKILL.md) | The calibration playbook: methods, pitfalls, and house rules for calibrating any OG-Core country model, single- or multi-industry | — |
| [`og-scenario-report`](og-scenario-report/SKILL.md) | OUTPUT_BASELINE/OUTPUT_REFORM → the standard charts+tables+narrative deliverable | `scenario_report.py` |
| [`og-analysis-studio`](og-analysis-studio/SKILL.md) | On-demand scenario design, free-form exploration, bespoke code-generated visualization and write-ups (not bound to the house formats) | — |

Together they cover the model-user journey: calibrate → run (your call, see the gates) →
standard report → bespoke analysis.

## Approval gates (binding on every skill in this family)

No skill in this directory ever takes an expensive or outward-facing action on its own. The
division of labor is: **skills propose, draft, and prepare; the user decides.** Concretely, a
skill may edit files, commit locally, and produce drafts — and must stop and ask before:

- **Pushing** to any remote, **creating** a PR, or **merging** anything (merges are always the
  user's, never proposed-and-executed). Drafting the PR text and showing the diff is the skill's
  job; the push and the PR are two separate approvals.
- **Launching long computations** — a TPI solve, a battery, a full example run, anything more
  than a couple of minutes. Propose the exact command, state the expected duration, let the user
  launch. A passing preflight is a *precondition* for a run, never an *authorization* of one.
- **Acting at fleet scale** — opening PRs (or pushing branches) across several repos is expensive
  and expansive; it happens only after the user has seen the full tracking table and per-repo
  diffs and has said which repos to act on. Never "one approval, N repos" unless the user
  explicitly approves the batch as a batch.
- **Deleting or destructive cleanup** — only ever emitted as commands for the user to run.

If a skill's instructions ever seem to conflict with this section, this section wins. (Skills
reference this as "the OG family README"; the same section ships with the MUIOGO-AI copy.)

## Installing

Per the shelf policy (NOTES.md → curation policy): these live here versioned and uninstalled;
install on demand, preferring the **project ring**:

```bash
# project-scoped (recommended): from this repo's root, into a country repo
cp -r skills/og/og-country-calibration ~/Projects/OG-PHL/.claude/skills/
cp -r skills/og/og-scenario-report     ~/Projects/OG-PHL/.claude/skills/
cp -r skills/og/og-analysis-studio     ~/Projects/OG-PHL/.claude/skills/

# personal (all projects)
cp -r skills/og/og-country-calibration ~/.claude/skills/
```

Restart / reload Claude Code after copying. `scenario_report.py` is numpy-only and runs with the
target repo's own venv as described in its SKILL.md.
