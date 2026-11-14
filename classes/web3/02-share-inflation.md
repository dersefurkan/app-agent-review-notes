# 2. First depositor share inflation

**Description.** The first deposit sets the exchange rate between assets and shares. If the rate is assets divided by shares, and shares can be driven to one, a gift of assets into the vault inflates the price of that share. The next depositor’s assets round to zero shares.

**Why it matters.** The second depositor pays and receives nothing. The first share can withdraw what both put in.

**Detection hints.**

- Read the share formula. Look for a division by total shares before a minimum is required.
- Virtual offset or a dead-shares mint on the first deposit is the usual patch. Confirm it is in the code, not only in a comment.
- Invariant: a depositor who sends a positive amount receives a positive share balance, including the depositor who arrives second.

**Example test.** First deposit of 1. Donate a large amount of the asset directly to the vault. Second deposit of a normal amount. Assert the second account’s shares are not zero.

**Public references.**

- [OpenZeppelin ERC-4626 inflation discussion](https://docs.openzeppelin.com/contracts/4.x/erc4626) describes virtual shares and assets as the offset.
- Teaching repo [pool-invariant-suite-demo](https://github.com/dersefurkan/pool-invariant-suite-demo).
