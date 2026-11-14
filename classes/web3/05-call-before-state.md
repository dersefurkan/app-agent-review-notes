# 5. External call before state update

**Description.** A function sends ether or calls an untrusted address before it records the withdrawal or the share burn. The callee can enter the function again and see the old state.

**Why it matters.** One balance can be withdrawn twice. The class is the order of the lines. A guard that is set after the call does not guard the call.

**Detection hints.**

- For every external call in a value-moving function, the state write that consumes the credit must appear above the call.
- A reentering call in a test must observe the updated balance, or the test fails.
- Invariant: the sum of payouts for one credit is that credit.

**Example test.** A test callee calls back into withdraw. Assert the second payout is zero and the user’s balance was already reduced before the first call returned.

**Public references.**

- [SWC-107 Reentrancy](https://swcregistry.io/docs/SWC-107).
