# 7. Identification and authentication failures

**Description.** The app accepts a session, a reset, or a second factor for the wrong person, or
it accepts them forever. Guessing a weak password is the noisy form. The quiet form is a reset
link that logs in whoever opens it, or a session that stays valid after logout and after password
change.

**Why it matters.** Every later check trusts the subject this step produced. A wrong subject makes
the access-control tests meaningless.

**Detection hints.**

- Request a reset for user A. Open the link as user B, or after it should have expired.
- Change the password. Replay the old session cookie.
- A "remember me" token that is the user id is this class.
- Invariant: after logout and after password change, the old cookie does not load A's data.

**Example test.** Log in as A. Log out. Replay the cookie on A's profile. Assert denial. Then
request a reset, expire it by the product's own clock or by using it once, and assert the second
use fails.

**Public references.**

- [OWASP Top 10 2021 — A07 Identification and Authentication Failures](https://owasp.org/Top10/2021/A07_2021-Identification_and_Authentication_Failures/)
- [OWASP Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)
- [OWASP Forgot Password Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Forgot_Password_Cheat_Sheet.html)
