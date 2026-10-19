# Synthetic ticket generation

Exact generator function recovered from the original harness source. `batch` supplies label-first specs (description, persona, length, mood, typos, channel and tangent). This file documents the method; it does not include benchmark inputs or run the generator.

```python
def prompt(batch):
    specs = "\n".join(
        f'{j}. true issue: "{s["desc"]}" | writer: {s["persona"]} | length: {s["length"]} | mood: {s["mood"]} | '
        f'{s["typos"]} | via {s["channel"]} | {s["tangent"]}' for j, s in enumerate(batch))
    return f"""You are writing realistic customer support messages for testing a ticket router.
The company is Planwell, a project-management app for small teams (tasks, boards, docs, time tracking,
integrations with Slack/Google/GitHub, a mobile app; plans are Free, Team and Business, billed monthly or yearly).

Write one message per spec below. Rules:
- The message's main problem MUST be the given true issue, so a careful human agent would route it there.
- Never name the category or copy its description wording; describe the situation the way a real customer would.
- Match the writer, length, mood, typo level and channel. Invent specific, varied details (amounts, dates, names,
  device types, feature names). Do not reuse the same numbers or phrasing across messages.
- If the spec says to mention a second issue, keep it clearly secondary.

Specs:
{specs}

Output ONLY a JSON array, one object per spec, in order: [{{"n": 0, "message": "..."}}, ...]"""
```
