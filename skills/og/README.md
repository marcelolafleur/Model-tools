# skills/og/ — the OG-Core workflow family

Workflow skills for the OG-Core country-model practice (OG-USA/PHL/ZAF/IDN/BRA/ETH/FJI and
ogclews-link), built 2026-07-27 from the needs survey in `docs/skill-research/NOTES.md`. Each was
tested against the real repos/materials before committing (see the per-skill commit messages).

The family's calibration playbook, [`og-country-calibration`](og-country-calibration/SKILL.md),
predates the rest and is the companion to all of them — several skills below cross-reference its
sections by name.

## The skills

| Skill | One line | Bundled script |
|---|---|---|
| [`og-country-calibration`](og-country-calibration/SKILL.md) | The calibration playbook: methods, pitfalls, and house rules for calibrating any OG-Core country model, single- or multi-industry | — |
| [`og-run-preflight`](og-run-preflight/SKILL.md) | Mandatory GO/NO-GO before any model run: branch+HEAD, import-shadowing (3 vectors), per-worktree venvs | `preflight.py` |
| [`og-solver-diagnosis`](og-solver-diagnosis/SKILL.md) | Root-cause protocol for non-convergent/suspicious SS & TPI solves, with the family's real failure taxonomy | — |
| [`og-repo-fleet-sync`](og-repo-fleet-sync/SKILL.md) | One change → N country repos: playbook, detection sweep, tracking table, per-repo branches; never pushes unasked | — |
| [`og-scenario-report`](og-scenario-report/SKILL.md) | OUTPUT_BASELINE/OUTPUT_REFORM → the standard charts+tables+narrative deliverable | `scenario_report.py` |
| [`og-analysis-studio`](og-analysis-studio/SKILL.md) | On-demand scenario design, free-form exploration, bespoke code-generated visualization and write-ups (not bound to the house formats) | — |
| [`worktree-orchard`](worktree-orchard/SKILL.md) | Read-only inventory of checkouts/worktrees/backup dirs; merged vs diverged vs dirty; cleanup as printed commands only | `orchard.py` |
| [`calibration-provenance`](calibration-provenance/SKILL.md) | Trace any parameter back through notebooks/CSVs to its authoritative source; record the chain | — |

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

If a skill's instructions ever seem to conflict with this section, this section wins.

## Installing

Per the shelf policy (NOTES.md → curation policy): these live here versioned and uninstalled;
install on demand. OG skills are domain-scoped, so prefer the **project ring** — install into the
repos where they apply, not globally:

```bash
# project-scoped (recommended): from this repo's root, into a country repo / ogclews-link
cp -r skills/og/og-country-calibration ~/Projects/OG-PHL/.claude/skills/
cp -r skills/og/og-run-preflight       ~/Projects/OG-PHL/.claude/skills/
cp -r skills/og/og-solver-diagnosis    ~/Projects/OG-PHL/.claude/skills/

# personal (all projects) — for the cross-project ones (worktree-orchard especially)
cp -r skills/og/worktree-orchard        ~/.claude/skills/
cp -r skills/og/og-repo-fleet-sync      ~/.claude/skills/
cp -r skills/og/og-run-preflight        ~/.claude/skills/
cp -r skills/og/og-solver-diagnosis     ~/.claude/skills/
cp -r skills/og/og-scenario-report      ~/.claude/skills/
cp -r skills/og/calibration-provenance  ~/.claude/skills/
```

Restart / reload Claude Code after copying. Bundled scripts are stdlib-or-numpy-only and run with
the target repo's own venv where stated in each SKILL.md.
