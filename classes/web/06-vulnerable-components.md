# 6. Vulnerable and outdated components

**Description.** A dependency pinned in the lockfile has a known fix, and a scoped flow actually
calls that code. A version number in a banner is a lead. The finding is the call path.

**Why it matters.** A report that lists every CVE in the tree is not a review. The ones that
matter are the ones the named flow reaches. The ones it does not reach are marked "present, not
on this path".

**Detection hints.**

- Read the lockfile, not the marketing version.
- For each dependency the scope cares about, find one call from the flow under test.
- If the vendor fix is a config flag, check the default of that flag.
- Invariant: the running process loads the version the lockfile names.

**Example test.** Print the resolved version from the lockfile and from the running app. Assert
they match. If a scoped flow calls a function the advisory names, say so and stop. Do not write a
weaponized request for the advisory.

**Public references.**

- [OWASP Top 10 2021 — A06 Vulnerable and Outdated Components](https://owasp.org/Top10/2021/A06_2021-Vulnerable_and_Outdated_Components/)
- [OWASP Vulnerability Disclosure Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Vulnerability_Disclosure_Cheat_Sheet.html)
