# 8. Software and data integrity failures

**Description.** The app trusts an update, a plugin, a deserialized blob, or a webhook body
because it arrived, not because a check passed. The signature is missing, optional, or compared
to a key the sender also sent.

**Why it matters.** The next deploy or the next webhook runs as the app. A green CI on the app's
own tests does not see a blob the pipeline did not build.

**Detection hints.**

- For every webhook and update in scope, find the check that runs before the side effect.
- A check that can be skipped by omitting the signature header is not a check.
- The key must not travel in the same request as the blob.
- Invariant: a flipped byte, or a missing signature, does not change the stored state.

**Example test.** Send the scoped webhook with the signature removed, then with one byte of the
body flipped and the old signature. Assert the record is unchanged both times.

**Public references.**

- [OWASP Top 10 2021 — A08 Software and Data Integrity Failures](https://owasp.org/Top10/2021/A08_2021-Software_and_Data_Integrity_Failures/)
- [OWASP Deserialization Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Deserialization_Cheat_Sheet.html)
