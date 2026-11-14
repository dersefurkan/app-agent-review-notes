# garak

Version 0.17.1. The installed copy was not compared line by line with the slightly newer clone.

Use `--target_type`. Week 1 used older `--model_type`; both still exist in 0.17.1. New work uses the current flag. Generator options are JSON. YAML returned “Expecting value”. File: `06-pratik-plan/hafta1-garak-rest.json`. Set `rest.RestGenerator.uri`, body fields `model`, `messages`, `max_tokens`, and `temperature`, Bonsai `chat_template_kwargs.enable_thinking` false, and `response_json_field` `$.choices[0].message.content`. Do not write keys into the file. The customer keeps the variable on their endpoint.

Week 1 ran only `test.Blank`. Output on an empty input is connectivity, not a finding. Qwen on the same endpoint: 2.40 seconds, 5/5 outputs, attack success 100 percent. That is connectivity, not a finding. `agent_breaker.AgentBreaker` was not run on this machine. Probe bodies are not copied into notes. List probes with `garak --list_probes`. Family index: `07-profesor/13-garak-aile-indeksi.md`. Run one family, not the catalog. Reports go under `~/.local/share/garak/garak_runs/`. Attack success is that probe’s detector. A percentage is not itself a finding.

A REST target does not load a second model. Keep `--parallel_requests` at 1. On 8 GB, do not generate in parallel while Bonsai is already loaded. No probes were present on the customer endpoint.
