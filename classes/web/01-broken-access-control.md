# 1. Broken access control

**Description.** The server performs an action for a caller who does not own the object and does
not hold the role the action requires. The UI hid the button. The check on the server is missing,
or it trusts an id, a role, or a tenant the client sent.

**Why it matters.** This is the class OWASP has ranked first. The state change is someone else's
record, file, or invoice. A hidden link that still returns the object is the same class as an id
the attacker guessed.

**Detection hints.**

- For every object id in a scoped flow, repeat the request as a second user created by the product,
  not by a test backdoor.
- Diff the server check: it must compare the session's subject to the object's owner or role. A
  check that only looks at the id in the query is not a check.
- Horizontal and vertical are the same test with a different second identity. An admin route is
  vertical. Another user's invoice is horizontal.
- Invariant: B's request does not change A's object, and the response does not contain A's secret
  fields.

**Example test.** A owns invoice 1. B is logged in. B requests invoice 1. Assert denial and that
the amount, status, and owner are unchanged.

**Public references.**

- [OWASP Top 10 2021 — A01 Broken Access Control](https://owasp.org/Top10/2021/A01_2021-Broken_Access_Control/)
- [OWASP Authorization Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html)
- [PortSwigger — Access control](https://portswigger.net/web-security/access-control)
