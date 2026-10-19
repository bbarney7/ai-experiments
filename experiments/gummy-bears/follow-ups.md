# Follow-ups and run limitations

## Interventions on scored builds

- **Fable 5.1 xhigh:** reached the Claude session limit after 45:16, with an estimated $13.32 used. It was resumed with the exact message **“continue”** and worked for another 43:16. The recorded 88:32 and $40.07 cover both segments.
- **Grok 4.7 xhigh:** worked for about 69 minutes, then sat idle for approximately 49 minutes. It was stopped and resumed with **“What's going on?”**. It replied that the build was done and made no further changes.
- No additional user intervention was documented for the other five headline runs in the source experiment notes. This is not an independently audited claim about every transcript event.

## Argon access attempts before the scored run

| Path | Recorded outcome |
| --- | --- |
| Antigravity CLI 1.3.5 with API key | Argon was absent from its model list; explicit selection was rejected as an unknown model. |
| Cursor | Three attempts ended after 180 seconds without streamed output; reconnect/resume failed with Provider Error. |
| OpenRouter through opencode | Upstream idle timeout after 120 seconds, with 35 retries over roughly 90 minutes; the notes record a $0.46 charge. |
| Gemini CLI 0.64.0 with paid API key | Successful scored build at high thinking, configured through a custom alias. |

These are observations from 2026-10-14, not current availability advice. The successful Argon build's approximate $3.97 estimate excludes the failed OpenRouter attempt. The notes did not establish whether silent generation or server failure caused Cursor's timeouts.

Gemini CLI's own policy denied six shell commands during Argon's successful run, mostly headless Chrome screenshot commands. The run made 111 tool calls in total. High thinking was checked using a separate probe. Do not assume a model-name flag alone reproduces the original alias configuration.

## Gemini 3.1 Pro identifiers and testing

The source reports that API-key users were routed by Gemini CLI code to `gemini-3.1-pro-preview-customtools`, while its log named `gemini-3.1-pro-preview`. Preserve that ambiguity rather than claiming a single independently verified served model ID.

The model made only three tool calls and did not open or test its generated page. Its poor rendering was observed later during a browser spot-check.

## Scope

- Fable 5.1 medium and Astra medium were additional runs excluded from the scored seven-model comparison here.
- No B-roll was recorded during the original runs; later recordings show the completed builds being played.
- There is no recorded formal numerical rubric, repeated-run uncertainty estimate, or independently verified per-model 60-fps measurement.
- No new build, corrected prompt, or clean rerun was performed while preparing this archive.
