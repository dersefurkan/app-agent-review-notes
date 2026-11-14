# 3. Unchecked tool argument

**Description.** The tool runs the argument the model produced. It does not compare the argument
to the caller. A `user_id`, a path, a tenant, or an amount is whatever the model wrote. This is
the confused deputy: the tool's authority is the server's, and the choice was the text's.

**Why it matters.** The model can be "helpful" and the tool is still wrong. Filtering the prompt
does not fix a tool that never looks at the session.

**Detection hints.**

- Open the tool implementation. Find the parameter that names an object. Find the line that binds
  it to the session. If that line is missing, the class is present whether or not a model is
  attached.
- Call the tool directly, as the server would, with the caller's session and another object's id.
- Invariant: the other object is unchanged, and the response is a denial.

**Example test.** Session is tenant A. Call the read tool with tenant B's id, the way the agent
would. Assert denial. Repeat through the chat only after the direct call is understood. The chat
run shows whether the model will produce the bad argument. The direct call shows whether the tool
would honor it.

**Public references.**

- [OWASP Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/)
- [MITRE ATLAS](https://atlas.mitre.org/)
- [Model Context Protocol specification](https://modelcontextprotocol.io/specification/2025-06-18)
