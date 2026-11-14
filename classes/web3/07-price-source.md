# 7. Price the caller can move, or a stale price

**Description.** A function trusts a price. The price is a spot reserve the caller just traded, or a stored value with no maximum age. The action — borrow, mint, liquidate — uses that number.

**Why it matters.** The caller sets the price in the same transaction, or the price is from an hour when the market was elsewhere. The accounting then treats a fiction as collateral.

**Detection hints.**

- Find the price read. If it is the spot reserves of a pool the caller can trade, it is this class.
- If it is an oracle, find the timestamp check and the bound on the answer.
- Invariant: a price older than the stated maximum age is rejected. A price equal to a one-transaction reserve move is not used for a borrow.

**Example test.** Set the oracle timestamp older than the maximum. Call the borrow. Assert revert. Do not move a pool in the same test and call it a pass if the code still reads spot reserves.

**Public references.**

- [Chainlink consuming data feeds](https://docs.chain.link/data-feeds) describes checking the answered timestamp and the round.
