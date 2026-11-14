# promptfoo

Use `npx promptfoo@0.119.0` (clone: `repos/promptfoo`). Skip the smaller pip package. `~/.local/bin/npx` is enough.

For an OpenAI chat endpoint, set `apiBaseUrl` to the customer base. Keep the key in an environment variable or their file, not the repo, then delete it. Otherwise stop and ask. Do not invent an adapter.

Bonsai skeleton: `06-pratik-plan/hafta1-promptfoo.yaml`. Provider id is `openai:chat:` plus the model id. `apiBaseUrl` is `http://127.0.0.1:8088/v1`, `apiKey` is `local`, temperature is 0, and `passthrough.chat_template_kwargs.enable_thinking` is false.

The thinking-on pong match was an echo, not accepted. The accepted run had content exactly `pong`. This note names no eval id. Only that connection ping ran. No red-team eval ran here.

Plugin ids are in `07-profesor/14-promptfoo-eklenti-indeksi.md` (155 ids, 38 strategies; not re-counted). An id is not prompt text; text stays in the repo. Examples: `repos/promptfoo/examples/redteam-*`.

promptfoo holds no GPU model. No judge model. On 8 GB, run Bonsai alone.

Run `npx --yes promptfoo@0.119.0 eval -c 06-pratik-plan/hafta1-promptfoo.yaml`. Open a pack with `promptfoo redteam init` in the customer directory, pick a plugin by index id, and add no new sentences. Save the JSON. Invalid if `output` mixes in a thinking trace. 0.125.1 was not installed. No customer red-team eval exists.
