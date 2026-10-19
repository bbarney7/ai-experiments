# Adding an experiment

Use a short kebab-case folder under `experiments/`. Copy `templates/experiment/` for new work.

Include the question, starting state, actual model identifier and effort, tool versions when known, allowed resources, prompt provenance, evaluation method, follow-ups, outcome, and video link if published. Mark unknown fields as not recorded.

Put copyable instructions in `prompt.md`; put explanations in the README. For multiple conditions, use `prompts/` and describe how to choose one. Keep tests' input data separate from the answer key.

Before publishing, check local links, remove credentials and private data, document any redactions, and compare copied prompts against their source. New synthetic examples must be labeled as examples rather than original benchmark inputs.

When updating an existing experiment, preserve the tested version and explain the change. Keep result snapshots dated, and do not silently mix later runs into an earlier video's scorecard.
