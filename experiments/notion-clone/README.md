# Build a Notion-style app

Can a coding agent build a useful Notion-style team app from one detailed prompt, including a real backend and authentication?

**Status:** original builds completed. This folder recovers the Fable build's goal-file prompt; it does not claim an independently recovered byte-identical Astra prompt.

## Watch

- [Is GPT-6 Astra AGI? I Had It Build Notion](https://www.youtube.com/watch?v=n_rz6KYmy9k)
- [Fable 5.1 vs GPT-6 Astra: Same Prompt, 6.5x the Cost](https://www.youtube.com/watch?v=VhmEGMG2xgY)

## Prompt and setup

Use [prompt.md](prompt.md). The original Fable session referenced this source file in its goal hook on 2026-09-12. This export replaces only the identifiers below; instructions and even source typos remain unchanged.

| Placeholder | Replace with |
| --- | --- |
| `{{WORKSPACE}}` | Absolute path to a fresh, dedicated project directory |
| `{{FIREBASE_PROJECT_ID}}` | Your dedicated Firebase project for authentication |
| `{{SUPABASE_PROJECT_ID}}` | Your dedicated Supabase project, if using Supabase |
| `{{COMPARISON_WORKSPACE_NAME}}` | Name of any other contestant's workspace that must stay off limits |

Place your authorized configuration inside the workspace as described in the prompt. The public repo supplies no credentials or live cloud configuration. Keep privileged server credentials out of browser code and commits.

The tested setup used a fresh directory and dedicated Firebase and Supabase resources. Installed design skills and existing Notion clone repositories were disallowed; general-purpose UI and editor libraries were allowed. The primary model planned and coordinated cheaper implementation subagents. Grade functional, visual, and interaction fidelity to a real Notion replacement.

The recovered prompt explicitly permits public product research, screenshots, and demos. A later script describes internet use more narrowly as documentation-only; the actual recovered prompt is authoritative for this export.

Exact agent versions and a full independent acceptance-test report are not included here.

## Recorded outcome

Both runs produced applications. The published comparison described Fable's result as better, with a substantially higher estimated token cost. This seed contains the prompt and method, not the application source or a newly audited financial comparison.

See [follow-ups.md](follow-ups.md) for reconstruction limits.
