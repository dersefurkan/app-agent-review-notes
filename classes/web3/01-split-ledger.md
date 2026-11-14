# 1. Split ledger

**Description.** One deposit is supposed to credit two stores: a cash ledger and a share ledger, or a vault and a queue. One write lands. The other does not. The protocol’s story of the balance and the code’s stores disagree.

**Why it matters.** Withdrawals read one store and redemptions read the other. The gap is value that exists in the story and not in the cash, or cash that no share can claim.

**Detection hints.**

- Name the two stores the deposit must touch. Read both after one call.
- A test that only checks the return value does not see the second store.
- Invariant: after a deposit of X, store A increased by X and store B increased by the matching units. After a full withdrawal, both are back.

**Example test.** Deposit a known amount. Assert both balances. Withdraw all. Assert both are unchanged from the start. The broken variant fails the second store. The patch makes both asserts hold.

**Public references.**

- The teaching repo [split-ledger-vault-demo](https://github.com/dersefurkan/split-ledger-vault-demo).
- [SWC-105 Unprotected Ether Withdrawal](https://swcregistry.io/docs/SWC-105) is a different bug. It is listed so the withdrawal check is not confused with a split ledger.
