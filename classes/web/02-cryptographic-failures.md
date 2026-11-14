# 2. Cryptographic failures

**Description.** A secret is stored or sent in a form another party can read. The password is in
the row. The session cookie has no secure flag. The backup is the database file. The token is in a
query string that lands in a log.

**Why it matters.** The cryptographic primitive can be fine and the product still fails, because
the secret never needed to be cracked. It was stored as itself.

**Detection hints.**

- Read the column that holds the password or the session secret. A reversible encoding is not a
  hash.
- Follow the cookie and the reset link. The secret must not sit in a `Referer` or a front-end
  bundle.
- A default key in the repo is this class, not a later hardening task.
- Invariant: after signup, the stored secret field is not equal to the password that was submitted.

**Example test.** Create a user with a known password. Read the stored field with the app's own
admin or the test database. Assert inequality, and assert the transport for the session is the
one the scope required.

**Public references.**

- [OWASP Top 10 2021 — A02 Cryptographic Failures](https://owasp.org/Top10/2021/A02_2021-Cryptographic_Failures/)
- [OWASP Cryptographic Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cryptographic_Storage_Cheat_Sheet.html)
- [OWASP Password Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)
