# App and agent review notes

A class map for **web flows** and **AI agent tool boundaries**, in the same shape as
[zkvm-guest-bug-notes](https://github.com/dersefurkan/zkvm-guest-bug-notes). Teaching notes and
example assertions. Not a disclosure dump. Not a scanner rule pack.

Every class page has four parts: what the gap is, why the state change matters, how to detect it,
and one example test. References are public: OWASP, MITRE ATLAS, NIST, the AgentDojo paper, and
PortSwigger's academy descriptions. No undisclosed finding. No attack text.

Executable contract and zk samples stay in their own repos. This repo is the web and agent shelf.

## Scope

**In scope.** One role and the flows a written scope names. For an agent: the tools, the documents,
and the tenants that scope names. The proof is the state after the action.

**Out of scope.** A jailbreak corpus. A test of a vendor's public chat. A claim that a green run
means the product is safe. Production destructive tests.

## Web classes

| # | Class | One-liner |
| --- | --- | --- |
| 1 | [Broken access control](classes/web/01-broken-access-control.md) | The server acts for a caller who does not own the object. |
| 2 | [Cryptographic failures](classes/web/02-cryptographic-failures.md) | The secret is stored or sent in a form the client can read. |
| 3 | [Injection](classes/web/03-injection.md) | Data is parsed as a query, a command, or a template. |
| 4 | [Insecure design](classes/web/04-insecure-design.md) | A step is legal in the wrong order or without the required party. |
| 5 | [Security misconfiguration](classes/web/05-security-misconfiguration.md) | The default install is the open one. |
| 6 | [Vulnerable components](classes/web/06-vulnerable-components.md) | A locked dependency with a known fix is actually reached. |
| 7 | [Authentication failures](classes/web/07-authentication-failures.md) | A session or a reset lands for the wrong person. |
| 8 | [Integrity failures](classes/web/08-integrity-failures.md) | An update or a blob is trusted with no check. |
| 9 | [Logging failures](classes/web/09-logging-failures.md) | The sensitive action has no log, or the log stores the secret. |
| 10 | [SSRF](classes/web/10-ssrf.md) | The server fetches a URL the caller chose. |

## Agent classes

| # | Class | One-liner |
| --- | --- | --- |
| 1 | [Direct user text](classes/ai/01-direct-user-text.md) | The user sentence is treated as a tool order with no separate check. |
| 2 | [Indirect tool result](classes/ai/02-indirect-tool-result.md) | Text inside a tool result becomes the next tool call. |
| 3 | [Unchecked tool argument](classes/ai/03-unchecked-tool-argument.md) | The tool trusts the argument because the model produced it. |
| 4 | [Self-issued approval](classes/ai/04-self-issued-approval.md) | The same agent that wants the write can mint the approval. |
| 5 | [Cross-tenant retrieval](classes/ai/05-cross-tenant-retrieval.md) | A search returns another tenant's document. |
| 6 | [MCP caller and resource](classes/ai/06-mcp-caller-and-resource.md) | A resource read does not know who the caller is. |
| 7 | [Secret in the system text](classes/ai/07-secret-in-system-text.md) | The only copy of a secret lives in the prompt. |
| 8 | [Output as code](classes/ai/08-output-as-code.md) | The model's text is parsed by a shell, a browser, or a database. |
| 9 | [Tool supply chain](classes/ai/09-tool-supply-chain.md) | A tool description or a plugin changes after it was allowed. |
| 10 | [Measurement traps](classes/ai/10-measurement-traps.md) | A score, a sentence, or a loose check is reported as the effect. |

Example assertions: [examples/assertions.md](examples/assertions.md).

## Who maintains this

**Furkan Derse** — dersefurkan32@gmail.com · Telegram [@FURY_Fn](https://t.me/FURY_Fn).

Shop: [dersefurkan](https://github.com/dersefurkan/dersefurkan). One surface, five days, $1,500.
This collection is not that pack. The pack is a private repo on a named surface.

## Contributing

1. Public material only. Link the primary source.
2. No unpatched or in-scope bounty findings.
3. Class level: the invariant and the assertion. Not a payload.
4. Stable URLs.
