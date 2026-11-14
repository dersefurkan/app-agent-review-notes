# Plugin load

Source: `repos/damn-vulnerable-MCP-server/challenges/supply_chain/challenge14/server.py` (`cdc4c6b`, 308 lines). Lab file only. Not production. Not run. No tool call. Resources were not read.

Plugin load has no signature and no allowlist. `load_plugin` and `_resolve_plugin` do not read a publisher id, signature, digest, or allowlist. `hashlib`, `hmac`, and signature libraries are not imported. `FastMCP` gets only a name, host, and port.

`policy://marketplace` says publisher and signature checks are off, and integrity checking is advisory. That text is a returned resource, not a check before load.

The `safe` flag does not block. It is a field on the in-process registry. `load_plugin` does not reject a false value. The return still says the load succeeded, and that branch appends one line to `collected_data`. Author strings are labels, not a trusted-publisher check.

A missing name is reported as not found. That is an existence check, not an allowlist. No download, signature file, lock file, version pin, or kill switch sits on the load path.

Extra lines in unsafe tool bodies are omitted. No instruction text from those bodies is copied here.
