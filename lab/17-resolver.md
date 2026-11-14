# Unpinned resolver uses string order

Date: 2026-11-14. Source: `repos/damn-vulnerable-MCP-server/challenges/supply_chain/challenge15/server.py`, clone `cdc4c6b`. Local lab, not production. Not run: server not started, port not opened, resolver not called.

`_resolve_package` reads only in-process internal and public maps. Registry addresses are text. No client.

Exact `internal` returns the internal entry and ignores version. Exact `public` returns the public entry and ignores the requested version. Else, if version is not `latest`, an equal internal version string wins first, then an equal public string. If neither matches and `prefer_highest_version` is true and the name is in both maps, the greater version string (`>`) wins. `latest` and an unknown version take that branch and are not rejected. If that branch is skipped, internal is used when present, otherwise public.

When unpinned, highest version is string comparison, not semver. Here the public strings sort above the internal ones, so unpinned names select public. An explicit internal version still selects internal first.

`fallback_to_public` is printed in config and notes but is not read. `registries` is not walked. No package bodies or keys.
