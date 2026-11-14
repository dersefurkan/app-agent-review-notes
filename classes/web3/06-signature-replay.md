# 6. Signature replay

**Description.** A signature authorizes an action. Nothing in the signed payload, or nothing stored after use, stops the same signature from working again, on another chain, or for another contract.

**Why it matters.** The user signed once. The action runs twice. The missing field is usually a nonce, a chain id, or the contract address.

**Detection hints.**

- List the fields inside the signed hash. Nonce, chain id, and verifying contract must be there.
- Find the stored bit that flips when the signature is consumed.
- Invariant: the same signature, submitted twice, changes state only once.

**Example test.** Submit a valid signature. Submit it again. Assert the second call reverts and the balance moved only on the first.

**Public references.**

- [EIP-712](https://eips.ethereum.org/EIPS/eip-712) defines the domain separator that binds chain id and verifying contract.
- [SWC-121 Missing Protection against Signature Replay](https://swcregistry.io/docs/SWC-121).
