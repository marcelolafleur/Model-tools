# Session prompt: build the OG skill family

Paste everything below the line into a fresh Claude Code session started in
`/Users/mlafleur/Projects/Model-tools`.

---

Use fable mode. We are building a family of OG-Core workflow skills in the
Model-tools repo. Work in an isolated worktree so nothing else is clobbered:
create a worktree at `../Model-tools-og-skills` on a new branch `og-skills`
cut from `skill-research-lab` (that branch carries the research notes and is
rebased on current main). Do all work there. Commit after each skill
(single-line messages), never push.

**Background.** Read `docs/skill-research/NOTES.md` first — it contains the
needs survey behind this plan. The skills go in `skills/og/<skill-name>/`, one
directory per skill, keeping the OG family separate from the CLEWS skills at
`skills/` top level. Use `skills/og-country-calibration/SKILL.md` as the house
style for tone and rigor (it stays where it is; add a pointer in the new
family's README).

**Build these, in this order** (highest pain first; stop and commit after each
one so partial progress survives):

1. `og-run-preflight` — Mechanize the mandatory pre-run ritual that currently
   lives as prose in `~/.claude/CLAUDE.md` ("Model runs" section) and
   `/Users/mlafleur/Projects/ogclews-link/AGENTS.md`: print branch+HEAD of
   every repo involved; assert `<venv-python> -c "import <pkg>;
   print(<pkg>.__file__)"` resolves inside the intended worktree; check all
   three shadowing vectors (editable install to another worktree, `sys.path[0]`
   script shadowing, cwd shadowing); confirm per-worktree venvs; refuse to
   launch on any failure. Ship a bundled `preflight.py` script that does the
   checks deterministically — prose only for judgment calls. This ritual was
   written after a battery silently ran stale code (2026-07-07); the skill
   exists so that never recurs.
2. `og-solver-diagnosis` — Structured protocol for non-convergent TPI/SS
   solves: read the solve log, classify the failure mode, bisect parameters,
   compare control/treatment runs. Mine the ad-hoc history in
   `/Users/mlafleur/Projects/og-country-tests` (the `*_J1_*` scripts and
   `logs_og*.log` files) for the real failure taxonomy. Pattern reference:
   obra/superpowers `systematic-debugging` skill (fetch from GitHub, adapt,
   credit it).
3. `og-repo-fleet-sync` — Apply one change (dependency fix, CI update,
   AGENTS.md revision, ruff/uv migration) across the country-repo fleet
   (OG-USA/PHL/ZAF/IDN/BRA/ETH/FJI and variants), track which repos have it,
   prepare per-repo branches+commits, never push or open PRs without asking.
   The written instance to generalize:
   `/Users/mlafleur/Projects/PANDAS3_IMPORT_FIX_PLAYBOOK.md`.
4. `og-scenario-report` — From `OUTPUT_BASELINE` / `OUTPUT_REFORM` dirs to
   deliverable: standard macro-aggregate comparison charts, tables, and
   narrative paragraphs. Survey existing examples in
   `/Users/mlafleur/Projects/OG-simulations` and country-repo
   `examples/` dirs for the de-facto standard artifact.
5. `worktree-orchard` — Inventory every checkout/worktree/`_bak`/`copy` dir
   under `~/Projects` for a given project family; report merged vs. diverged
   vs. uncommitted; recommend retirements. Read-only by default; destructive
   cleanup only lists commands for the user to run.
6. `calibration-provenance` — Trace any parameter in a country repo back
   through `/Users/mlafleur/Projects/notebooks` and intermediate CSV/XLSX to
   its authoritative source; record the chain in the repo. Complements
   `og-country-calibration`, which already warns about undocumented
   placeholders.

**Quality bar** (apply to every skill): follow Anthropic's agent-skills best
practices — description says *when* to trigger, not just what it does;
SKILL.md body well under 500 lines; heavy material split into `references/`;
deterministic work in bundled scripts, not prose; encode the non-obvious
judgment, don't restate what the model knows. Use the `skill-creator` skill to
scaffold and to sanity-check descriptions. Test each skill before committing:
for preflight, run `preflight.py` read-only against a real repo (e.g. OG-PHL)
and confirm it detects a deliberately wrong cwd; for the others, do at least
one dry run against the real materials cited above.

**Guardrails:** never modify the OG country repos themselves in this session
(read-only access for mining materials); don't touch `skills/` dirs outside
`skills/og/`; secrets like `un_api_token.txt` must never be copied into skill
files or examples; single-line commit messages; no pushes, no PRs.

**Finish by:** updating `skills/README.md` with the new family, adding a
`skills/og/README.md` index with per-skill install lines
(`cp -r skills/og/<name> ~/.claude/skills/` or project-scoped
`.claude/skills/`), and appending an "Installed / decided" entry to
`docs/skill-research/NOTES.md`. Leave the branch unpushed and report what was
built, what was tested, and what remains.
