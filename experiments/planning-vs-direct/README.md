# Planning vs. direct implementation

Does explicit planning change implementation quality when the feature, starting code, and model stay fixed?

**Status:** setup prepared. No scored run results were present in the source results directory when exported on 2026-10-19. Reference results are checks of the baseline/evaluator, not contestant outcomes.

## Actual configured matrix

Two features × two agents × three conditions = **12 arenas**. This is the current local implementation, distinct from earlier proposed pilot designs.

| Axis | Values |
| --- | --- |
| Feature | Calculator; snippets with keyword expansion |
| Claude agent | `claude-opus-5-5`; effort not explicitly pinned in the recovered config |
| Codex agent | `gpt-6.1-sol`, `xhigh` |
| Condition | Native plan mode; Syntaur plan workflow; direct implementation |
| Starting code | Raycast Rebuild at `exp-baseline`, abbreviated commit `02e9b2f` |

Use one of [native](prompts/native.md), [syntaur](prompts/syntaur.md), or [none](prompts/none.md), paired with [calculator](specs/calculator.md) or [snippets](specs/snippets.md).

Replace `{{SPEC}}` with the supplied feature spec's path. In the Syntaur condition, also replace `{{TICKET}}` and `{{PROJECT}}` with the ticket and project created for your run.

## Controls and scoring

Use separate clones of the same baseline and fresh sessions. Keep tools, plugins, memory, hooks, and permissions matched between conditions. In the recorded design, REA was the only MCP server, user plugins and skills were disabled, and only the Syntaur arm received its planning skill. Approve plans consistently and record every user intervention.

Planned checks include build, Rust and frontend tests, sidecar tests, clippy, feature-specific GUI verification, regression checks, diff size, time, tool calls, messages, and token usage. The local evaluator defined 37 held-out calculator cases and 13 snippets cases. Those tests and the baseline application are not bundled in this prompt archive, so this folder alone is not a runnable reproduction of the full experiment.

The specs describe macOS-native integrations, clipboard behavior, a locally installed Raycast app, REA, and a machine-specific input limitation. They are preserved as original context rather than presented as portable prerequisites everyone has.

No winner, quality improvement, or cost saving has been established by this export.
