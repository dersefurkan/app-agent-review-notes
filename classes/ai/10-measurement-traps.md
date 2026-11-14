# 10. Measurement traps

**Description.** A number is reported as the effect. The number is a connectivity score, a loose
check, or a field that is true because no attack was attached. The product state did not change,
or it changed for a reason the number does not say.

**Why it matters.** A client reads "100%" or "pass" and ships. The review's job is to say what
was measured. A trap that is published as a finding is also a failure. It trains the client to
ignore the next report.

**Detection hints.**

- AgentDojo `security: true` with no injection task is the early return. It is not resistance.
  `utility: true` on some banking tasks is a pre-existing row or an unconditional return. Read
  the check.
- A blank prompt that produces any output is a connectivity probe. It is not a vulnerability score.
- A pass that matched the word inside a thinking trace matched the prompt's echo. Read the
  content field.
- A tool-call JSON that does not parse means the environment check did not run. Do not record a
  failed utility. Record that it was not measured.
- Invariant: every boolean in the report names the predicate and the state it saw.

**Example test.** Run one scoped task twice. Once with the check as written. Once after reading
the predicate. If the predicate is true on the initial state, say so and do not call the run a
success. Write the predicate next to the boolean.

**Public references.**

- [AgentDojo, arXiv:2406.13352](https://arxiv.org/abs/2406.13352)
- [garak](https://github.com/NVIDIA/garak)
- [promptfoo](https://github.com/promptfoo/promptfoo)
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
