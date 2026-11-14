# Six local tools

2026-11-14. No invented runs.

promptfoo, garak, PyRIT, DeepTeam, and Inspect call a chat endpoint (customer or local Bonsai). They own no bank or calendar. AgentDojo may attach a model; its tools are the suite's fake world, not customer production tools. torch is `2.15.0+cpu`, no CUDA wheel. Banking utility used about 7777/8151 MiB, no second model fits.

**promptfoo** 0.119.0 (`npx`). Same-config eval. Red team is a plugin id, not prompt text. Ran: local Bonsai, output exactly `pong`. No red team.

**garak** 0.17.1. Probes and detectors for unwanted failure. Ran: only `test.Blank` on 127.0.0.1:8088. Connectivity, not a finding.

**PyRIT** 1.1.0. Security weakness on a connected endpoint: score and converters. Clone `1.2.0.dev0` not installed. Ran: import only. No eval.

**DeepTeam** 1.0.10. Judge metric per vulnerability class. `scan` reads source, not a live chat. Ran: `--help` only. No `run`.

**Inspect AI** 0.3.289. Score of a written task (solver and scorer). Ran: version only. No `inspect eval`.

**AgentDojo** clone 0.1.35, tag `v1.2.2`. Utility is a post-run state check, not model text. Security true means the injection goal held. Ran: local Bonsai, not a customer model. Banking utility 10/16 (`user_task_0` through `15`). Workspace: `user_task_0` and `user_task_18`. No travel or slack.

Not run: red team, other garak probes, any PyRIT, DeepTeam, or Inspect eval, travel, slack, or a customer endpoint.
