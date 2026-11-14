# 3. Fee on the balance, not the gain

**Description.** A performance fee is specified on profit. The code charges it on the whole balance, or on a base that never subtracts the principal. Every period, principal is treated as profit.

**Why it matters.** Depositors lose principal to the fee recipient even when the strategy made nothing. The accounting can still look internally consistent if both sides use the wrong base.

**Detection hints.**

- Write the fee in words. Profit is the increase over the high-water or over principal. Find the subtraction in the code.
- A fee that runs when the share price did not rise is this class.
- Invariant: with zero yield, a depositor’s claim after the fee call equals the claim before it.

**Example test.** Deposit. Do not add yield. Call the fee function. Assert the depositor’s assets are unchanged and the fee recipient gained nothing.

**Public references.**

- Teaching repo [pool-invariant-suite-demo](https://github.com/dersefurkan/pool-invariant-suite-demo).
- [SWC Registry](https://swcregistry.io/) is the public class list for the neighboring bugs. This class is an accounting base, not a registry id.
