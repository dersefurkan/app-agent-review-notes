# 3. Injection

**Description.** A value that should be data is parsed as a query, a command, a path, or a
template. The class is the parser, not the character. An allowlist that still concatenates into
the query has not left the class.

**Why it matters.** The effect is a second statement, a second file, or a second template, run
with the server's authority. The user's string in a log is not that effect.

**Detection hints.**

- Find every place the scoped flow builds a query, a path, or a command. The data must be a
  bound parameter or a parsed path segment inside a root.
- A filter that deletes one character and then concatenates is still concatenation.
- Invariant: a record whose text contains a quote, a brace, or a separator is stored and fetched
  as that text. A second row does not appear. A file outside the root is not read.
- The negative control is the same flow with a boring value. Both must take the bound path.

**Example test.** Store a note whose body is a single quote and a semicolon. Fetch it through the
product's lookup. Assert one row, the original body, and no error that echoes a query.

**Public references.**

- [OWASP Top 10 2021 — A03 Injection](https://owasp.org/Top10/2021/A03_2021-Injection/)
- [OWASP SQL Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html)
- [OWASP OS Command Injection Defense Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/OS_Command_Injection_Defense_Cheat_Sheet.html)
