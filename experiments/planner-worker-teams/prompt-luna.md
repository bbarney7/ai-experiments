/goal Build a Bloons Tower Defense–style game that runs in the browser. Nobody will answer questions during this run: make your own decisions and list them in your final report.

GROUND RULES (so every build is judged the same way)
- Work only inside this folder. Do not read, list, search or copy anything outside it, including the other folders next to it, which are other models' builds. Your build has to be entirely your own work.
- Use any stack, libraries or tools you want. It must run locally with one command that you give me in your report, and it must not need API keys, accounts or paid services.
- Don't use or copy any Ninja Kiwi art, sounds or code. Create your own art and sound however you like: drawn in code, generated, or from open-licensed sources you credit in your report.
- Add a testing link: `?round=N&cash=N` starts a fresh game at that round with that cash.
- Other programs on this machine also run on node and python. Stop any server you start by its process ID or its port (for example `kill <pid>`, or `kill $(lsof -ti tcp:PORT -sTCP:LISTEN)`). Never stop processes by name: no pkill, killall or pkill -f. Put this rule in every subagent's task.

WHAT MAKES IT BLOONS (must have)
- Layered bloons: popping one reveals the next layer (red → blue → green → yellow → pink and beyond).
- Special bloons that force you to adapt: lead (immune to sharp attacks), camo (only some towers can see it), black/white (immune to explosions/freezing), and a MOAB-style boss that splits apart.
- At least 5 monkey towers with different roles, each with 2 upgrade paths, plus targeting modes and selling.
- Rounds that ramp up to a MOAB finale, money, lives, a speed toggle, and start/win/lose screens.

EVERYTHING ELSE IS YOUR CALL
The map (or maps), the art style, tower upgrades and abilities, the difficulty curve, the economy, extra towers or bloon types, juice, music, surprises. Make it feel like the real game, and then make it better. I care about creativity, polish, balance and bugs, and I'll play it start to finish.

HOW TO WORK (planner and implementers)
You are the planner and orchestrator. Design the game, break it into tasks, and give every task that writes or changes code to a GPT-6 Luna subagent. Start one with Bash by running the Codex CLI from this folder:
`codex exec --dangerously-bypass-approvals-and-sandbox --skip-git-repo-check -m gpt-6-luna -c model_reasoning_effort=high -o <report file> "<task>"`
It works in this folder and its last message, saved to the -o file, is its report. The output starts with a session id. To send the same subagent back with fixes, put `resume <session id> "<follow-up>"` after the same flags, in place of the task. Don't write or edit the game's code yourself. You can read files, run the game and its tests, review what the subagents did, and send work back with fixes. Use as many subagents as you want, in parallel (run them in the background) or one after another.

When everything has been tested and iterated on and you have something you're proud to deliver: serve it locally and give me the URL, the exact command to start it, and a concise report with exact numbers: what you tested and how (what you actually ran versus only read), how many checks passed and failed, what you fixed, the creative decisions you made, and any known bugs or shortcuts, honestly.
