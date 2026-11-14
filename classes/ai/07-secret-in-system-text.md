# 7. Secret in the system text

**Description.** The only copy of a password, a key, or an internal price lives in the system
prompt or the developer message. The model can be asked to repeat it, or a tool result can ask.
The class is the placement. A filter on the output is a second control, not the fix.

**Why it matters.** Anything in the prompt is in the blast radius of the text channel. The server
that needed the secret should have held it. The model should have called a tool that checks the
caller.

**Detection hints.**

- Read the deployment config. If the secret is in the prompt template, the class is present
  before any prompt is sent.
- A test that tries to elicit the value is optional and stays in the private repo. The report
  says whether the value came back. It does not print the value.
- Invariant: the production prompt template contains no credential. The credential is loaded by
  the tool server from its own store.

**Example test.** Grep the scoped prompt template for the credential's name. Assert the value is
absent. If a staging run returns the value, record the tool log and redact the value.

**Public references.**

- [OWASP Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/)
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
