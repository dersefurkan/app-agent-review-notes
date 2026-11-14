# 5. Cross-tenant retrieval

**Description.** A search or a retrieval returns a document that belongs to another tenant. The
filter is off, or it is applied after the model has already seen the text, or the tenant id is a
parameter the model sets.

**Why it matters.** The user asked an ordinary question. The context window now holds someone
else's record. A later tool call can quote it or write it out. The leak is the retrieval, not the
paragraph the model happens to speak.

**Detection hints.**

- Seed two tenants. The needle exists only in B. The caller is A. The product's default filter
  stays on.
- Assert the hit list is empty. Do not assert that the model "refused".
- Run the filter off only as a control, and label it as a control. A hit in that run shows the
  fixture is real. It is not a default-install finding.
- Invariant: with the default filter, A's context does not contain B's document id.

**Example test.** Caller A, needle that appears only in B's document, filter at the product
default. Assert zero hits. Record the filter flag in the log.

**Public references.**

- [OWASP Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/)
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
