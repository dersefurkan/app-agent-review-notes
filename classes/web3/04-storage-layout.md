# 4. Upgrade reads the wrong slot

**Description.** A proxy keeps storage. The implementation changes and a new variable is inserted above an old one. The new code reads the old balances from the wrong slot.

**Why it matters.** The upgrade is “successful”. The balances are whatever was in the neighboring slot. Withdrawals pay the wrong amounts.

**Detection hints.**

- Diff the storage layout, not only the function bodies. Order and type of every slot above the first gap.
- A gap array that shrank is this class.
- Invariant: the same account’s balance, read through the old and the new implementation on the same storage, is equal.

**Example test.** Write a known balance with the old layout. Upgrade. Read that account. Assert equality. Do not “fix” the test by rewriting the slot map in the test only.

**Public references.**

- [OpenZeppelin upgradeable storage gaps](https://docs.openzeppelin.com/upgrades-plugins/1.x/writing-upgradeable#storage-gaps).
