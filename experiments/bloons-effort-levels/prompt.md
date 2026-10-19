/goal Build a Bloons Tower Defense–style game that runs in the browser. Nobody will answer questions during this run: make your own decisions and list them in your final report.

GROUND RULES (so every build is judged the same way)
- Work only inside this folder. Do not read, list, search or copy anything outside it, including the other folders next to it, which are other models' builds. Your build has to be entirely your own work.
- Use any stack, libraries or tools you want. It must run locally with one command that you give me in your report, and it must not need API keys, accounts or paid services.
- Don't use or copy any Ninja Kiwi art, sounds or code. Create your own art and sound however you like: drawn in code, generated, or from open-licensed sources you credit in your report.
- Add a testing link: `?round=N&cash=N` starts a fresh game at that round with that cash.
- Other programs on this machine also run on node and python. Stop any server you start by its process ID or its port (for example `kill <pid>`, or `kill $(lsof -ti tcp:PORT -sTCP:LISTEN)`). Never stop processes by name: no pkill, killall or pkill -f.

WHAT MAKES IT BLOONS (must have)
- Layered bloons: popping one reveals the next layer (red → blue → green → yellow → pink and beyond).
- Special bloons that force you to adapt: lead (immune to sharp attacks), camo (only some towers can see it), black/white (immune to explosions/freezing), and a MOAB-style boss that splits apart.
- At least 5 monkey towers with different roles, each with 2 upgrade paths, plus targeting modes and selling.
- Rounds that ramp up to a MOAB finale, money, lives, a speed toggle, and start/win/lose screens.

EVERYTHING ELSE IS YOUR CALL
The map (or maps), the art style, tower upgrades and abilities, the difficulty curve, the economy, extra towers or bloon types, juice, music, surprises. Make it feel like the real game, and then make it better. I care about creativity, polish, balance and bugs, and I'll play it start to finish.

When everything has been tested and iterated on and you have something you're proud to deliver: serve it locally and give me the URL, the exact command to start it, and a concise report with exact numbers: what you tested and how (what you actually ran versus only read), how many checks passed and failed, what you fixed, the creative decisions you made, and any known bugs or shortcuts, honestly.
