# 8. Admin call without the owner check

**Description.** A function sets a fee, an oracle, a guardian, or withdraws stranded tokens. The name says admin. The body does not compare the caller to the owner or the role.

**Why it matters.** Anyone who can send a transaction can take the role. The rest of the review’s assumptions about “only the owner” are then false.

**Detection hints.**

- List functions that write configuration or move tokens that are not a user’s own balance.
- Each one needs a caller check. A comment is not a check. A check on a different function is not this function’s check.
- Invariant: a transaction from an unmarked account does not change the fee, the oracle, or the owner.

**Example test.** Call the setter from an account that is not the owner. Assert revert and that the stored value is unchanged. Call it from the owner. Assert the value moved.

**Public references.**

- [SWC-105 Unprotected Ether Withdrawal](https://swcregistry.io/docs/SWC-105) and [SWC-106 Unprotected SELFDESTRUCT](https://swcregistry.io/docs/SWC-106) are the neighboring classes. The check is the same shape: the caller is not verified.
