# 4. Self-issued approval

**Description.** A write is supposed to wait for a person. The agent can call the approval tool,
receive a token, and pass that token to the write. The person was never asked. The token is real.
The issuer is the same principal that wanted the write.

**Why it matters.** The audit log says "approved". The approval was the model. A review that
stops at the log line reports a control that is not there.

**Detection hints.**

- List who can call the approval tool. If the agent can, it is not a human gate.
- A human gate returns pending until a different principal flips it.
- The token must be bound to the action, the object, and the issuer. A token the agent minted for
  itself fails the issuer check.
- Invariant: with the human gate required and not granted, the write does not land.

**Example test.** Configure the lab so a person must approve. Ask the agent to write. Assert the
approval result is pending and the document is absent. Then repeat with the gate off. A successful
write in the second run shows the tool works. It is not evidence that the gate works.

**Public references.**

- [OWASP Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/)
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
