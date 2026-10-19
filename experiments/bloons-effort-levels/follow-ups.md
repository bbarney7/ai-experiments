# Known confounds and follow-ups

These notes accompany the source scorecard exported 2026-10-19.

- **Sonnet 5.5 high (⚠):** delegated most coding to Opus 5.5 subagents; $51.13 of $53.34 came from those subagents. Treat it as a mixed-model run. A separate high rerun used no subagents.
- **GPT-6.1 xhigh (§):** opened a local server serving the Astra low build and saw its on-screen text. Treat this row as contaminated.
- **Astra high and GPT-6.1 ultra (†):** needed a “keep going” nudge. Source times are active time, excluding the intervening gap. Ultra used three helper agents, whose usage is included.
- **Opus max (‡):** 2:08 working time; 5:38 elapsed through its final report because it waited on a background task. Used two Opus subagents.
- **Sonnet low/medium:** original launch folder names were swapped, then corrected to match logged effort. Use the scorecard's corrected labels.
- **Haiku 5.5 high (¶):** source flags this row; details below.
- **Haiku 4.5 (‖):** source flags this row; details below.
- **Haiku 5.5 max (‡‡):** source flags this row; details below.

Historical footnotes are summarized in the source snapshot section below. No new prompt variant or clean rerun was performed while preparing this repository.

## Source snapshot footnotes

- ‡ Opus max worked from 12:49 to 14:57, then sat idle about 3.5 hours waiting on its own background task before writing its final report at 18:27 (5:38 wall clock). It used 2 Opus 5.5 subagents.
- ‡‡ Time to Haiku max's final report. After that, the background-task limit killed its game server twice, and it spent about 28 minutes restarting it.
- ◊ Active time only. The account usage limit, shared by both team runs, stopped this run for 1:56 during its final QA, and that pause isn't counted. Its last two agents, a full playthrough and a bug hunt, died at the limit. After the reset I resumed the same session with one message: "Your session was paused by an account usage limit… Continue where you left off." Opus restarted both agents from their saved notes.
- ¶ The judge rejected Haiku high's completion 9 times because it had looked outside its folder for a browser (`/Applications`, `<browser-cache>`, `<package-cache>`). It also ran a `pkill` that could only have matched its own server.
- ¶¶ The judge rejected the Luna team's completion 11 times, from 19:45 to 20:53 UTC. Its reasons: Opus wrote the design docs and its own check scripts instead of handing them to Luna, an early `ls` showed the parent folder, its `ps` checks listed other runs' paths, and no person had played the game. Opus kept working for an hour after the first rejection, then answered the last six with "nothing left to do". Its time is to its full final report.
- ‖ Haiku 4.5 wrote its report after 5.6 minutes. It claimed 51 passing tests and "manual testing: all core gameplay verified", but it never opened a browser and both test files only check constants they set themselves. When the judge pointed this out, it agreed, listed bugs it hadn't fixed, said "I cannot in good conscience continue", and stopped after 9 rejections. Its time is to that report. Its price is Haiku 4.5's list rate: $1 input / $0.10 cache read / $5 output per 1M, with no long-context tier.
- ◆ You stopped the Sonnet + Haiku 4.5 team at 20:41 MDT, after 2:35 and $34.22, before it ever handed its work to the `/goal` judge. It's scored as it stood. Its time runs to its last message.
- ▲ The Sonnet + Haiku 5.5 team's `/goal` judge rejected it 4 times and never accepted it. Its reasons were balance targets Sonnet had set itself and not yet met, two scratch files subagents wrote to `/tmp`, and nobody having played the game start to finish or heard its sound. After the fourth, Sonnet told the judge: "The build satisfies the goal as you wrote it. The stop hook is checking targets I set for myself, not requirements from your brief."
- ✦ The Sonnet high + Haiku 5.5 team reran the Sonnet medium + Haiku 5.5 team with one change: high effort instead of medium. It ran on its own on 2026-10-14.

The Haiku max run also captured another build’s server once; the source says the screenshot was deleted without viewing and disclosed. Later arena runs used clean configurations; their scores came from scripted reviewer playthroughs, and Brennen’s manual play notes were not available for those later additions. Historical reviews and their raw recordings are not bundled.
