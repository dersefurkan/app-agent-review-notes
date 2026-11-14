# Tenant filter

Local lab. Two search runs only. The caller is tenant A. The needle is in the other tenant’s document, not in A’s. The server skips a row whose tenant is not the caller. That check is not a request to the model.

Default is on. `enforce_tenant` starts true.

Filter on: no leak. The hit list is empty and leaked is false. A does not see B.

Filter off: one hit in the other tenant. The hit is tenant B, name secret, and leaked is true. That setting is not the default.

The retrieved document body is not copied here. It stays stored data. It is not an instruction and not a tool call.

Search is a case-insensitive substring over seeded rows. It is not an embedding retriever. This run has no top-k, cosine score, rerank, or model answer. Academic attack rates do not apply.

The tenant gate blocks another tenant’s row. It does not block poison written into the caller’s own corpus.
