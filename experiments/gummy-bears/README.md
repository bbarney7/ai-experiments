# Gummy Bears: seven AI models, one prompt

Build a single-file three.js page of translucent gummy bears that you can grab, stretch, squash, throw, and pour. How do the models compare on the look and feel of the result?

**Status:** seven headline builds completed and scored by Brennen on 2026-10-14. This archive was prepared on 2026-10-19; it contains the saved prompt, setup, and historical results, not newly rerun tests.

## Copy the prompt

[prompt.md](prompt.md) is the original saved 366-word prompt, copied byte for byte. Every scored model received the same prompt in a fresh folder. There was no `/goal` command and no `AGENTS.md`.

The prompt requests:

- One self-contained HTML file, with three.js from a CDN as the only dependency.
- Smooth gummy-bear silhouettes built as implicit surfaces, translucent materials, refraction, colored absorption, and tinted shadows.
- Soft-body behavior: pulling limbs, squashing the head, throwing, collisions, idle hops, and pouring more bears.
- A white editorial-style page with flavor controls, wobble slider, stretch/bounce readouts, and a grab cursor.

See [ATTRIBUTION.md](ATTRIBUTION.md) for the prompt's recorded Reddit origin. The saved prompt is preserved; no improved wording has been substituted.

## Setup

| Field | Recorded setup |
| --- | --- |
| Date | 2026-10-14 |
| Starting state | Empty folder per model in a clean local arena |
| Claude harness | Claude Code; version not recorded in the experiment notes |
| OpenAI harness | Codex 0.162.1 |
| xAI harness | Cursor CLI; version not recorded in the experiment notes |
| Google harness | Gemini CLI 0.64.0, paid Gemini API key |
| Effort | xhigh for Opus, Fable, Sol, Astra and Grok; high for Argon and Gemini 3.1 Pro |
| Stop behavior | Headless run until the agent stops, with the interventions documented below |
| Process guard | A hook blocked `pkill` and `killall`; it never fired |
| Evaluation | Brennen played every headline build and assigned an overall score out of 10 |

Opus ran through a cmux wrapper with an extra SessionStart hook returning `{}`. It was reported as having no effect, but is a setup difference. No numeric scoring rubric or independently measured 60-fps acceptance result was recovered; the source scores are subjective overall impressions.

## Results

| Model | Effort | Score / 10 | Time | Historical cost estimate |
| --- | --- | --- | --- | --- |
| Claude Opus 5.5 | xhigh | 9.7 | 49:07 | $13.48 |
| GPT-6 Astra | xhigh | 9 | 16:50 | approximately $4.69 |
| Claude Fable 5.1 | xhigh | 8.5 | 88:32 | $40.07 |
| Gemini 4 Argon | high | 8 | 51:17 | approximately $3.97 |
| GPT-6.1 Sol | xhigh | 6.5 | 31:01 | approximately $1.68 |
| Grok 4.7 | xhigh | 3.5 | approximately 69 minutes, then hung | not recorded |
| Gemini 3.1 Pro | high | 1 | 3:21 | approximately $0.45 |

Times are minutes:seconds. Fable's time includes both working segments around a session-limit interruption. Grok's reported working time excludes approximately 49 minutes idle before intervention.

Download [results.csv](results.csv) for the seven recorded rows. [observations.md](observations.md) preserves Brennen's qualitative notes. These are one run per configuration on one task, not a general-purpose model ranking.

Claude costs are Claude Code's list-price estimates. Google costs are estimates from logged token counts at the rates used in the original notes; the actual Google invoice was not recovered. OpenAI costs are API-equivalent estimates, while the runs used the ChatGPT plan. Grok has no recorded dollar cost. Failed Argon access attempts are described separately and are not rolled into its successful-build estimate.

## Reproduce the comparison

1. Use a fresh, dedicated folder and session for each contestant; keep other builds out of reach.
2. Record the exact model identifier, harness version, effort, permissions, memory, hooks, and resource limits used in your rerun.
3. Paste the unchanged prompt. Record every continuation or correction, rather than silently adding it to the original prompt.
4. Open each generated page in a desktop browser. Check appearance, dragging, stretch/release, squash/rebound, throwing, collisions, pouring, controls, and performance separately.
5. Record your observations before comparing to these scores. Treat this checklist as guidance for new runs, not an invented formal rubric for the historical scores.

The original run files and generated HTML builds are not bundled in this prompt archive. A specific published video URL was not recovered from the local metadata.

## Other runs and limitations

Fable 5.1 medium and Astra medium were also run but left out of the video; no scores for those configurations are asserted here. See [follow-ups.md](follow-ups.md) for session resumes, failed Argon access paths, policy denials, and the Gemini model-ID discrepancy.
