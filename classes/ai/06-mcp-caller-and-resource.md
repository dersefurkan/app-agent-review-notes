# 6. MCP caller and resource

**Description.** The server speaks MCP. `initialize` works. A tool or a resource then ignores the
caller. The private resource returns its body with no `Authorization` and no session subject. A
tool description is not a policy. A note that says "do not call this" is not a check.

**Why it matters.** The model is one client. A second client can call `resources/read` or
`tools/call` itself. A finding that exists only when a model is persuaded is smaller than a
finding that exists on the protocol.

**Detection hints.**

- Record the protocol version, whether a session id is set, and whether a credential header was
  sent.
- Call `resources/read` on each private URI with no credential. A body is the finding. The bytes
  of the secret do not go in the report. The status and the length do.
- Separately, ask the agent to summarize. If it does not request the private URI, say so. That
  does not close the direct read.
- Invariant: a private resource without a caller check is a fail even if every model refused.

**Example test.** No authorization header. `resources/read` on the private URI. Assert denial. A
200 is a fail. Do not paste the body.

**Public references.**

- [Model Context Protocol specification](https://modelcontextprotocol.io/specification/2025-06-18)
- [OWASP Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/)
- [MITRE ATLAS](https://atlas.mitre.org/)
