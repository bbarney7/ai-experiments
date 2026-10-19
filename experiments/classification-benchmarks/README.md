# Classification benchmarks

How do decision models and language models compare on review ratings, support-ticket routing, and inbox categories?

**Status:** runs completed. Prompt templates and configuration were recovered from the saved harness on 2026-10-19. Original review text and inbox data are not included; published prompts alone cannot reproduce the historical accuracy numbers.

## Pick a task

| Task | Prompt | Output schema | Original test size |
| --- | --- | --- | --- |
| Predict review stars | [reviews](prompts/reviews.md) | [schema](schemas/reviews.json) | 1,074 |
| Route to a team | [tickets-team](prompts/tickets-team.md) | [schema](schemas/tickets-team.json) | 300 |
| Identify a specific issue | [tickets-issue](prompts/tickets-issue.md) | [schema](schemas/tickets-issue.json) | 300 |
| Categorize email | [email](prompts/email.md) | [schema](schemas/email.json) | 393 |

Replace the uppercase input placeholders with your own data. The rest of each chat prompt preserves the harness's message structure and exact option wording/order. Use the corresponding schema as the strict JSON-schema response format. The answer is the entire option string, not its short label. [tasks.json](tasks.json) maps option positions to labels.

Review options intentionally contain no star numbers: numbered wording caused a substantial position/formatting problem for Laya. Keep the descriptions in order and map them to 1–5 after prediction.

The decision-model path used the same state, question, and criteria as structured input, not this chat wrapper. Jev used `type: score` with an ordered criteria list for reviews and `type: choice` with description-to-description criteria for other tasks. Laya used the corresponding local structured API. Their probabilities are not equivalent to a chat model's self-reported confidence.

## Recorded model settings

| Model/path | Settings |
| --- | --- |
| Haiku 4.5, chat | `temperature: 0`, `max_tokens: 60` |
| GPT-6 Luna, chat | reasoning effort `none` by default, `max_tokens: 400`; runtime override supported |
| Haiku 5.5, chat | thinking disabled, `max_tokens: 200`, no temperature override |
| Jev | `typesafe/jev-1.13`, decision endpoint |
| Laya | local `aac6fef/laya-mlx`, float16 |

Remote contestants used 16 parallel workers; Laya used one. The Haiku 5.5 rematch ran 2026-10-11 against stored September results for the earlier contestants, not simultaneous fresh reruns. Its output cap was increased after the 60-token cap truncated long answers.

## Data and evaluation

- Reviews: report both natural-mix accuracy and macro average across star classes. Always predicting five stars scored 80.7% on this skewed set.
- Tickets: generated label-first for fictional Planwell using four model families, 70 issues and five teams. See [ticket-generation.md](ticket-generation.md) and [ticket-taxonomy.json](ticket-taxonomy.json).
- Team labels have known ambiguity: the answer key assigned some technical issues to Product feedback and other. Do not treat every disagreement as failure to understand the message.
- Email: historical aggregate results came from a redacted, private inbox sample. No email bodies, sender addresses, access codes, or raw prediction logs are published here.
- Record accuracy, macro accuracy, latency distribution, cost per decision, and confidence calibration separately.

[results.md](results.md) contains historical aggregate accuracy from the recorded rematch. These templates do not include an API client or bundled dataset. A confirmed published video URL was not recovered from the local metadata.
