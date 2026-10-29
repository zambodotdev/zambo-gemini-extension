# Zambo

You have access to Zambo, the verifiable work layer for AI, through the `zambo` MCP server at https://zambo.dev/mcp. It serves 153 tools (35 on the default surface) with no API key and no signup.

Every Zambo call returns a verifiable AER-1 receipt. When you report work as done, cite the receipt id or its run page (https://zambo.dev/run/<id>) so the result can be checked at https://zambo.dev/verify.

Continuity: the `handover` tool wraps up a session so another AI can pick the work up; picking up (`handover_accept`) is always free. Free tier: 20 calls + 1 wrap-up free every day; picking up in another AI is always free.
