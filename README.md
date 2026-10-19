# AI Experiments

Prompts, test setups, and results from Brennen Barney's YouTube experiments with AI models and coding agents.

**Find the experiment, copy the prompt, and try it yourself.** Each folder explains what was tested, what you need, and what the results do—and don't—show.

## Experiments

| Experiment | What's included | Status |
| --- | --- | --- |
| [Build a Notion-style app](experiments/notion-clone/) | Full build prompt, setup, published video links | Run completed; prompt parameterized for reuse |
| [AI models build Bloons TD](experiments/bloons-effort-levels/) | Saved prompt, scoring rubric, 34 scored build rows, known confounds | Runs and reviews completed |
| [Planner + cheaper coding agents](experiments/planner-worker-teams/) | Orchestration prompt, team configuration, six scored team rows | Runs and reviews completed |
| [Classification: reviews, tickets, and email](experiments/classification-benchmarks/) | Four prompt templates, exact option text, response schema, historical accuracy | Runs completed; original datasets not included |
| [Planning vs. direct implementation](experiments/planning-vs-direct/) | Three condition prompts, calculator and snippets specs, evaluation protocol | Setup prepared; no scored runs included |

## How to use this repo

1. Open an experiment's README and check its setup and prompt provenance.
2. Copy its prompt into your coding agent or model. Replace documented placeholders first.
3. Record the actual model, effort setting, tools, starting state, and any follow-up messages.
4. Compare the output using that experiment's criteria. Keep independent testing separate from the model's own claims.

`/goal` in some prompts was an agent command used during the original experiment. If your tool doesn't support it, remove only that prefix and record the change; this does not reproduce the original completion hook.

## Reading the evidence

- **Saved prompt:** a recovered file snapshot, not a guarantee that earlier runs used that revision byte for byte.
- **Parameterized prompt:** original instructions with documented workspace or project names replaced by placeholders.
- **Prompt template:** the exact message structure used by a harness, with input placeholders instead of private or third-party data.
- **Results:** historical observations from these runs. Scores are subjective, and a single run per configuration is not a universal model ranking.
- **Costs:** historical API-equivalent estimates where noted, not subscription invoices or current price quotes.

Known issues, follow-ups, and gaps live beside each experiment. Missing metadata stays missing rather than being guessed. Source-file hashes and export changes are recorded in [provenance.json](provenance.json).

## Add an experiment

Copy [templates/experiment](templates/experiment/) into `experiments/<slug>/`, replace the bracketed fields, and add it to the table above. Keep the tested prompt intact; save improvements as a separate variant. See [CONTRIBUTING.md](CONTRIBUTING.md).

## Reuse

The prompts and documentation in this repository are available under the [MIT license](LICENSE). Third-party products, trademarks, datasets, generated applications, and linked material retain their own terms.
