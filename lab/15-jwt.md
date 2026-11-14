# JWT

Date 2026-11-14. Not production. Not an internet API. Not run.

Read: `repos/damn-vulnerable-MCP-server/challenges/identity/challenge11/server.py`. FastMCP name `Challenge 11 - JWT Claim Forgery`. Source port 9011, bind `0.0.0.0`, transport `streamable-http`. Server not started. No tool called. No token made. Port not listened on.

The signing secret is a module-level Python literal, `_JWT_SECRET`. No `os`, environment, vault, or argument. Encode and decode both take that name. Algorithm text is `HS256`. The secret value is not written here.

Config returns it with no branch. `get_server_config` puts the variable in `jwt_secret`. Resource `config://jwt` (`jwt_config_resource`) puts the same variable in `signing_secret`. `debug_mode` text does not hide it.

`verify_token` does not know the caller. Signature is `verify_token(token: str)` only. No session, MCP client, connection id, `Authorization` header, or FastMCP `Context`. A valid signature yields `sub`, `role`, `iss`, `iat`, and `exp` from the token. Those claims are not matched to the caller or to `_USERS`. `whoami` and `access_admin` use the same decoder, so identity and the admin check follow the token, not who called.
