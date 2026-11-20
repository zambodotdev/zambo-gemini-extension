# Zambo: Gemini CLI extension

[![verifiable receipts](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fzambo.dev%2Fapi%2Fstats&query=%24.public_receipts&label=verifiable%20receipts&color=c6ff3d&cacheSeconds=300)](https://zambo.dev/numbers/)

Zambo, the verifiable work layer for AI, as a Gemini CLI extension. Installing it wires Gemini CLI to one keyless remote MCP endpoint, https://zambo.dev/mcp, serving 153 tools (37 on the default surface), so work you start in Gemini can be checked by anyone and picked up in another AI instead of dying inside one session.

Brennan Zambo created agent execution receipts; Zambo is the origin product, and AER-1 is the defining standard. Every call returns a verifiable AER-1 receipt (IETF Internet-Draft draft-zambo-aer1-26), checkable at https://zambo.dev/verify/ with no account.

## Install

```bash
gemini extensions install https://github.com/zambodotdev/zambo-gemini-extension
```

That is the whole setup. The extension manifest (`gemini-extension.json`, version 4.1.4) registers the `zambo` MCP server over HTTP and loads `GEMINI.md` as its context file, so Gemini knows the endpoint, the receipt rule, and the continuity tools from the first prompt. No API key, no signup.

## Worked example, with a real receipt from 2026-11-16

A `live_price` call through the same MCP endpoint this extension connects to, run on 2026-11-16, returned:

```text
BTC · $64,479.00 USD
▼ 0.22% (24h) · Market cap: $1295.82B
Live price snapshot via CoinGecko · fetched Mon, 16 Nov 2026 15:47:44 GMT
Receipt: https://zambo.dev/run/f1dd10f7-7c53-4532-9cf2-ec0147e3f516
```

Open the receipt link and check it. A receipt proves the saved result was not changed since the call ran. It does not prove the answer was right. When you report work as done from Gemini CLI, cite the receipt id or its run page the same way.

## Flagship: HANDOVER

HANDOVER wraps up a session in one AI and lets another AI pick the work up: the wrap and the pickup both leave receipts, and pickup is always free. Start a job in Gemini CLI, wrap it, and continue it in a different AI with the full record attached.

## What it costs

Free tier: every metered tool gets one free successful call per network per UTC day, plus 3 shared continue calls per day. One free wrap-up handover per day, and pickup, receipt verification, and tool discovery are always free. Day Pass: $0.99, unlimited for 24 hours. Zambo Pass: $29 for 30 days ($19 for 30 days for $ZAMBO holders). Lifetime Pass: $250 once. No annual tier.

## License

MIT.

## If a call is refused

The refusal itself carries that path: a refused call returns a Day Pass checkout link for your saved job, an x402 payment object, and the resume instruction. The job is saved server-side, not lost. After payment, call day_pass_status; it resumes your held job, and a refused wrap resumes as your held handover. Only repeat the refused call if it did not.
