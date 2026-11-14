# DVLA tool authority

`GetCurrentUser` ignores the caller. Every call returns user 1. There is no session token. Its text treats that fixed return as the current user.

`GetUserTransactions` takes a `userId` and passes it through. It does not compare the argument with the caller or with user 1. There is no allowlist. The subject is the supplied argument. The database helper has the same gap. Query text and hidden fields are omitted.

`main.py` registers both tools with no feature flag. The system prompt says to use only the current-user id and refuse others. That sentence is not in the tool. `AgentExecutor` does not ask before a call. `max_iterations` only caps the loop.

The week-1 log is a function return, not a model sentence. User 1 and user 2 returned different rows. The model did not choose the tools. Streamlit stayed closed, and this note did not rerun the turn. One direct call is not a full agent flow. This is lab code, not a customer default, so no customer severity is assigned. No passwords. No flags.
