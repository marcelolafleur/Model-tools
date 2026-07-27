# skills/og/ — the OG-Core workflow family

Workflow skills for the OG-Core country-model practice (OG-USA/PHL/ZAF/IDN/BRA/ETH/FJI and
ogclews-link), built 2026-07-27 from the needs survey in `docs/skill-research/NOTES.md`. Each was
tested against the real repos/materials before committing (see the per-skill commit messages).

The family's calibration playbook, [`og-country-calibration`](../og-country-calibration/SKILL.md),
lives one level up (it predates this directory) and is the companion to all of these — several
skills below cross-reference its sections.

## The skills

| Skill | One line | Bundled script |
|---|---|---|
| [`og-run-preflight`](og-run-preflight/SKILL.md) | Mandatory GO/NO-GO before any model run: branch+HEAD, import-shadowing (3 vectors), per-worktree venvs | `preflight.py` |
| [`og-solver-diagnosis`](og-solver-diagnosis/SKILL.md) | Root-cause protocol for non-convergent/suspicious SS & TPI solves, with the family's real failure taxonomy | — |
| [`og-repo-fleet-sync`](og-repo-fleet-sync/SKILL.md) | One change → N country repos: playbook, detection sweep, tracking table, per-repo branches; never pushes unasked | — |
| [`og-scenario-report`](og-scenario-report/SKILL.md) | OUTPUT_BASELINE/OUTPUT_REFORM → the standard charts+tables+narrative deliverable | `scenario_report.py` |
| [`worktree-orchard`](worktree-orchard/SKILL.md) | Read-only inventory of checkouts/worktrees/backup dirs; merged vs diverged vs dirty; cleanup as printed commands only | `orchard.py` |
| [`calibration-provenance`](calibration-provenance/SKILL.md) | Trace any parameter back through notebooks/CSVs to its authoritative source; record the chain | — |

## Installing

Per the shelf policy (NOTES.md → curation policy): these live here versioned and uninstalled;
install on demand. OG skills are domain-scoped, so prefer the **project ring** — install into the
repos where they apply, not globally:

```bash
# project-scoped (recommended): from this repo's root, into a country repo / ogclews-link
cp -r skills/og/og-run-preflight    ~/Projects/OG-PHL/.claude/skills/
cp -r skills/og/og-solver-diagnosis ~/Projects/OG-PHL/.claude/skills/

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
