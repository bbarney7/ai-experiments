# AI models build Bloons TD

Does a larger model or higher reasoning effort build a better browser game from the same prompt?

**Status:** builds and reviews completed. This is a dated archive of the saved prompt and expanded scorecard, exported 2026-10-19. The expanded scorecard contains later additions beyond the original video.

## Try it

1. Start in an empty, dedicated folder with no access to other contestants' builds.
2. Paste [prompt.md](prompt.md). Record the actual model, effort, tools, and any `/goal` completion hook.
3. Do not answer questions during the run. Record any intervention separately.
4. Play the game, review the code, and independently verify important behavior.
5. Score graphics, complexity, quality, and creativity using [rubric.md](rubric.md).

The prompt requires a local browser game with layered balloons, special resistances, five or more towers with two upgrade paths, a boss finale, and a `?round=N&cash=N` testing link. Models choose their own stack, scope beyond the requirements, and creative direction.

## Results

[results.csv](results.csv) contains 34 individually scored builds from the saved rankings. [Planner/worker teams](../planner-worker-teams/) contains six additional scored teams from the same rankings. These are recorded historical scores, not new reruns. The original model set included Claude Opus, Sonnet and Fable, plus GPT-6 Sol, GPT-6.1 Sol and GPT-6 Astra; later rows include Haiku and Luna.

Costs are API-equivalent estimates from recorded usage, including cached rereads and subagents. The source says these runs used subscriptions. Time is hours:minutes; footnote markers on rows matter—see [follow-ups.md](follow-ups.md). Exact harness versions were not recovered.

A confirmed published video URL was not recovered from the local video metadata.

## Important limitations

- The saved prompt includes a later process-cleanup rule. Earlier runs may predate that wording; this is not a claim of byte-identical prompts across every run.
- The original layer wording says red → blue → green → yellow → pink. Some agents interpreted that literally, making a popped balloon stronger. It is preserved here.
- Personal Claude instructions, memory, hooks, and plugins were present in original runs.
- Some runs used other models as subagents. Two needed a continuation message, and one saw another build through a running local server.
- Scores are subjective; generated passing-test claims are not independent proof.

Read [follow-ups.md](follow-ups.md) before treating rows as controlled comparisons.
