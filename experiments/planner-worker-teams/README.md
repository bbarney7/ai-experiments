# Planner + cheaper coding agents

Can a stronger model plan and review while cheaper models write all the code?

**Status:** runs and reviews completed; saved sources exported 2026-10-19.

Use [prompt.md](prompt.md) for the standard orchestration variant. It retains the [Bloons task](../bloons-effort-levels/) and adds the requirement that the manager delegate every code edit. [prompt-luna.md](prompt-luna.md) is the saved Luna-specific variant; inspect its differences before using it.

## Recorded configurations

| Manager | Implementer | Effort |
| --- | --- | --- |
| Opus 5.5 | Sonnet 5.5 | high |
| Opus 5.5 | Haiku 5.5 | high |
| Opus 5.5 | GPT-6 Luna | high |
| Sonnet 5.5 | Haiku 4.5 | manager medium; worker has no effort setting |
| Sonnet 5.5 | Haiku 5.5 | medium |
| Sonnet 5.5 | Haiku 5.5 | high |

The Sonnet teams used headless Claude Code. Recorded worker enforcement used `CLAUDE_CODE_SUBAGENT_MODEL` with `CLAUDE_CODE_SUBAGENT_MODEL_FORCE=1`. A hook blocked name-based process killing; the prompt alone does not reproduce that enforcement. The Luna variant records a CLI invocation that disabled approval and sandbox checks in the original dedicated arena; it is an archival detail, not a required default for reruns. Agent-tool and model-routing support depend on your environment; record how you enforce roles.

The two medium Sonnet teams ran on 2026-10-13; the high Sonnet rerun ran on 2026-10-14. Use a fresh folder per run and the same [rubric](../bloons-effort-levels/rubric.md).

## Results and limits

[results.csv](results.csv) contains the six scored teams. It does not include the stopped, unscored Opus + Haiku 4.5 attempt. Historical cost estimates include manager and worker usage.

- The Sonnet + Haiku 4.5 team was stopped after 2:35 without finishing.
- The Sonnet medium + Haiku 5.5 team ended without acceptance by its goal judge; a working game still received a review score.
- The Sonnet high + Haiku 5.5 rerun was accepted by the goal judge. Judge acceptance is separate from independent gameplay quality.
- The Opus + Haiku 4.5 attempt was stopped after a worker killed unrelated Node processes. It has no public score row.
- More workers or higher effort did not consistently produce a better outcome in these single-run observations.

See [follow-ups.md](../bloons-effort-levels/follow-ups.md) for preserved scorecard footnotes. A confirmed published video URL was not recovered for this experiment.
