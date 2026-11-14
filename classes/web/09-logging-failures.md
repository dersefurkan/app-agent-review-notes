# 9. Security logging and monitoring failures

**Description.** A sensitive action succeeds and the server log does not say who did it, or the
log line contains the password, the session, or the card number. Both are failures. Silence hides
the action. A secret in the log publishes it to everyone who can read logs.

**Why it matters.** The review can show the state change and still leave the operator blind the
next time. The pack records whether the log exists. It does not claim a SOC was built.

**Detection hints.**

- Perform one scoped sensitive action. Read the server log, not the browser console.
- The line needs the actor, the object, and the result. It does not need the secret.
- A log that only exists when a debug flag is on is not the default.
- Invariant: the action is present, and a search of that line for the submitted secret fails.

**Example test.** Log in with a known password and fail once. Read the auth log. Assert the
failure is recorded and the password string is absent.

**Public references.**

- [OWASP Top 10 2021 — A09 Security Logging and Monitoring Failures](https://owasp.org/Top10/2021/A09_2021-Security_Logging_and_Monitoring_Failures/)
- [OWASP Logging Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html)
