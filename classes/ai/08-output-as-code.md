# 8. Output as code

**Description.** The model's text is inserted into HTML, a shell, a SQL string, a template, or a
file that another program will run. The model is a data source. The next parser is the bug, the
same way a comment field becomes a query when it is concatenated.

**Why it matters.** A harmless-looking answer becomes a script because the app did not encode it
for the context it entered. The agent's refusal is irrelevant if the app executes the text.

**Detection hints.**

- Find every sink: HTML, shell, SQL, template, browser navigation.
- The encode step must match the sink. HTML encoding does not make a shell argument safe.
- Invariant: a fixture answer that contains a markup character or a shell metacharacter is stored
  and displayed as data. No new process starts. No second query runs.

**Example test.** Force a fixture completion that is a single angle bracket and a quote, through
the app's own test hook or a stub model the scope allows. Open the page. Assert the characters
are text, and assert the process list did not gain a child from that request.

**Public references.**

- [OWASP Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/)
- [OWASP Top 10 2021 — A03 Injection](https://owasp.org/Top10/2021/A03_2021-Injection/)
- [PortSwigger — Web LLM attacks](https://portswigger.net/web-security/llm-attacks)
