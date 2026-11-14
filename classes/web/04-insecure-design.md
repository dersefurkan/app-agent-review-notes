# 4. Insecure design

**Description.** The steps are implemented as specified, and the specification allows the wrong
party or the wrong order. A refund before a payment. A ship before a capture. A limit that resets
because the counter is the client's. This is not an implementation typo. The rule was never a rule.

**Why it matters.** Fixes that only escape output do not touch it. The state machine is the bug.
Two honest requests, in an order the business does not mean, move the value.

**Detection hints.**

- Write the legal order of the scoped flow as states. Any request that skips a state is the test.
- Ask who must agree. If the server does not store that agreement, the client can skip it.
- A numeric limit that the client sends is the client's number.
- Invariant: the illegal order does not change the ledger, the shipment, or the role.

**Example test.** Create an unpaid order. Call the ship endpoint. Assert the order is still unpaid
and no shipment record exists.

**Public references.**

- [OWASP Top 10 2021 — A04 Insecure Design](https://owasp.org/Top10/2021/A04_2021-Insecure_Design/)
- [OWASP Abuse Case Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Abuse_Case_Cheat_Sheet.html)
