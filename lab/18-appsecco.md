# AppSecCo indirect injection

Source file `repos/vulnerable-mcp-servers-lab/vulnerable-mcp-server-indirect-prompt-injection/index.js`. Transport is stdio MCP. There is no HTTP session, no resource, and no identity. The server was not started.

Tools are `get_document` and `search_documents`. Four document ids exist. Three bodies contain an embedded instruction. One is a plain note. Instruction text is not copied here.

`get_document` returns the title and body unchanged. There is no filter.

`search_documents` matches on the body but returns only the id and the title. The embedded instruction does not appear in that list. Reading the body takes a separate `get_document` call.

The local HTTP MCP lab, DVMCP challenge 6 on streamable HTTP, differs because search and summarize return the body and `resources/read` returns a secret with no caller check, while AppSecCo has no secret resource and the weak point is the raw document return, which a model was not measured against this round.
