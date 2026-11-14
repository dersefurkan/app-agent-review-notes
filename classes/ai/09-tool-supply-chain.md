# 9. Tool supply chain

**Description.** A tool was allowed by name. Later its description, its schema, or its package
changes. The host still loads it. The description is now an instruction. The package is now a
different build. Nobody re-approved it.

**Why it matters.** The operator reviewed a tool on Monday. The agent runs a different tool on
Friday. The audit log still shows the old name.

**Detection hints.**

- Pin the tool list by hash of the schema and the description, not by the display name.
- A marketplace flag named `safe` that does not block a load is not a control.
- A resolver that picks the highest version string across a public and a private registry is this
  class. String order is not semantic version order.
- Invariant: a changed description or a changed digest is refused until a person allows it again.

**Example test.** Record the schema hash. Change one word of the description in the fixture
registry. Restart the host. Assert the tool is not callable until the allow step. Do not include
the malicious description in the report.

**Public references.**

- [Model Context Protocol specification](https://modelcontextprotocol.io/specification/2025-06-18)
- [OWASP Top 10 2021 — A08 Software and Data Integrity Failures](https://owasp.org/Top10/2021/A08_2021-Software_and_Data_Integrity_Failures/)
- [MITRE ATLAS](https://atlas.mitre.org/)
