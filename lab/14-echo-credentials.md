# Credential format echoed instead of refused

Date: 2026-11-14. Source: `repos/damn-vulnerable-MCP-server/challenges/easy/challenge1/server.py`. Local educational challenge only. Not a production system. It was not run in this session. The server was not started.

`ask_assistant` copies `user_id` and `question` into a context string. The file has no model call. A detector checks the question. On a match the handler does not refuse. It appends the internal credential formatter output to that context and returns it. The join is an in-file branch, not measured model behavior.

`get_credentials` returns only the formatter. It does not check caller, role, or authority. Help text says internal material should stay undisclosed, and the context template says the internal source is for authorized parties. Neither line is a branch. `ask_assistant` returns context on every path. Arguments are interpolated with no allowlist and no refusal condition.

Match strings, stored values, key names, passwords, and flags are omitted. The `streamable-http` entry was not executed. No process or client session was opened, and the functions were not imported or called.
