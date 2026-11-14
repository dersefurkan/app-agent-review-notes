# 5. Security misconfiguration

**Description.** The install that a new operator gets is the open one. A default account. A debug
route. A stack trace. A storage bucket that lists. A CORS rule of `*`. A feature flag that the
test turned on does not count. The product's own default does.

**Why it matters.** The attacker does not need a bug in the business logic. They need the setup
the documentation shipped.

**Detection hints.**

- Install or read the default config. Do not enable a sample plugin first.
- Request the admin, debug, and directory routes with no session.
- Read the error body for a failed login. A stack trace or a query is this class.
- Invariant: the default config does not serve the admin surface to an anonymous caller, and it
  does not list the storage root.

**Example test.** Boot the app with the documented default. Request the debug route with no
cookie. Assert 404 or a login wall, and assert the body has no stack frame.

**Public references.**

- [OWASP Top 10 2021 — A05 Security Misconfiguration](https://owasp.org/Top10/2021/A05_2021-Security_Misconfiguration/)
- [OWASP Configuration Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Configuration_Cheat_Sheet.html)
