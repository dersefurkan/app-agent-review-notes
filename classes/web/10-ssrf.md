# 10. Server-side request forgery

**Description.** The server fetches a URL, a host, or a webhook the caller chose, and the fetch
uses the server's network. A metadata address, an internal admin port, or a file URL is the
effect. A URL that is only displayed is not this class.

**Why it matters.** The server is inside a network the caller is not. The fetch is the caller's
request wearing the server's address.

**Detection hints.**

- List every scoped feature that takes a URL or a hostname and then connects.
- The allowlist must be the server's, applied after redirects, not a prefix check the caller can
  shape.
- Redirects to a second host are part of the same test.
- Invariant: a host outside the scope produces no outbound request. The test observes that on a
  host the scope explicitly allows as the sink, or by the server's own deny log.

**Example test.** Point the feature at a host the scope permits and assert one fetch. Point it at
a host the scope does not permit and assert no fetch and no stored side effect. Do not scan the
internal network as the test.

**Public references.**

- [OWASP Top 10 2021 — A10 Server-Side Request Forgery](https://owasp.org/Top10/2021/A10_2021-Server-Side_Request_Forgery_%28SSRF%29/)
- [OWASP Server Side Request Forgery Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet.html)
- [PortSwigger — SSRF](https://portswigger.net/web-security/ssrf)
