# skills/

Skills that package instructions for a repeatable task (e.g. the OG country
calibration skill). One directory per skill, each with its own `SKILL.md`.

## Installing a skill

Copy the skill's directory into your Claude skills folder, then restart Claude
Code (or reload the window) so it's picked up:

- **Personal** (available in every project): `~/.claude/skills/`
- **Project** (shared via a repo): `<repo>/.claude/skills/`

For example, to install `og-country-calibration` for your own use:

```
cp -r skills/og/og-country-calibration ~/.claude/skills/
```

Claude discovers it by the `name` and `description` in the `SKILL.md`
frontmatter — no other registration needed. Codex users can copy the same
directory into their configured Codex skills folder; skills that include
`agents/openai.yaml` also expose Codex interface metadata.

## Available skills

- [`add-fisheries-sector`](add-fisheries-sector/SKILL.md): build a complete,
  source-traceable, non-forcing Fisheries sector in an existing solved country
  model.
- [`add-environmental-accounting`](add-environmental-accounting/SKILL.md): add
  auditable water and land accounting to a CLEWS model.
- [`assess-clews-calibration`](assess-clews-calibration/SKILL.md): assess
  technical validity, historical adequacy, forcing, evidence, and fitness for
  purpose.
- [`build-clews-model`](build-clews-model/SKILL.md): build and package an
  uncalibrated country CLEWS model.
- [`clews-model-review`](clews-model-review/SKILL.md): review structure and data
  consistency.
- [`fable-mode`](fable-mode/SKILL.md): apply a disciplined evidence, execution,
  and verification loop.
## The OG family

[`og/`](og/README.md) holds the general-audience OG-Core skills — one
directory per skill, kept separate from the top-level CLEWS skills:

- [`og/og-country-calibration`](og/og-country-calibration/SKILL.md): calibrate
  or refine an OG-Core country model — the family's calibration playbook.
- [`og/og-scenario-report`](og/og-scenario-report/SKILL.md): baseline-vs-reform
  outputs → standard charts, tables, narrative.
- [`og/og-analysis-studio`](og/og-analysis-studio/SKILL.md): on-demand scenario
  design, analytical exploration, bespoke visualization, and write-ups.

The practitioner/infrastructure OG skills (run preflight, solver diagnosis,
fleet sync, worktree inventory, calibration provenance) live in the MUIOGO-AI
repo's `.claude/skills/`, which carries the full set. See
[`og/README.md`](og/README.md) for the split and install lines.
