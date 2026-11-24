# Agent Landline MCP server

**A phone line for your AI assistant.** Tell your assistant what you need. It hands the call
to Agent Landline, which phones the person or business from your own verified number, says it
is an AI, stays inside the limits you set and asks your assistant before agreeing to anything
new. The transcript and the outcome come back to the same conversation.

- Website: https://agentlandline.dev
- Documentation: https://agentlandline.dev/docs
- Server address: `https://api.agentlandline.dev/mcp` (remote, Streamable HTTP)
- Sign-in: OAuth. No API key or bearer token to copy.

This repository holds the public connection guide and the
[MCP Registry](https://registry.modelcontextprotocol.io/) entry (`server.json`). The server
is hosted; there is nothing to install or run on your computer.

## What you need

- An Agent Landline account: sign in at https://agentlandline.dev
- A verified phone number in your account, which calls show as caller ID
- An assistant that supports remote MCP servers with OAuth (Claude, Claude Code, Codex,
  Cursor and others)

## Connect your assistant

### Claude (web and desktop)

1. Open **Customize › Connectors**, choose **Add**, then **Add custom connector**.
2. Name it *Agent Landline* and paste `https://api.agentlandline.dev/mcp`.
3. Sign in when the window opens.

On Team and Enterprise plans an owner adds the connector for the organization first.

### Claude Code

```bash
claude mcp add --transport http agent-landline https://api.agentlandline.dev/mcp
```

Then run `/mcp` inside Claude Code, pick `agent-landline` and sign in in your browser.

### Codex

```bash
codex mcp add agent-landline --url https://api.agentlandline.dev/mcp
```

```bash
codex mcp login agent-landline
```

### Cursor

Add to `~/.cursor/mcp.json` (every project) or `.cursor/mcp.json` (one project):

```json
{
  "mcpServers": {
    "agent-landline": { "url": "https://api.agentlandline.dev/mcp" }
  }
}
```

Cursor then offers to sign in.

### Other MCP clients

Add `https://api.agentlandline.dev/mcp` as a remote (Streamable HTTP) server and let the
client run its OAuth sign-in. Clients that can only start local servers cannot connect.

## What your assistant can do

| Tool | What it does |
|---|---|
| `prepare_call` | Prepare a call: who to call, the goal, the facts and what may be agreed |
| `check_number` | Check a phone number before calling |
| `place_call` | Place the prepared call |
| `call_status` | Follow a call: status, live transcript and the result |
| `nudge_call` | Send the voice agent a note during the call |
| `answer_question` | Answer a question the voice agent asks mid-call |
| `press_keys` | Press keypad digits for phone menus |
| `hand_over_call` | Ring your own phone so you can take over the call |
| `abort_call` | End the call |
| `list_contacts`, `save_contact`, `forget_contact` | Short notes about people and businesses you call |

The [tools reference](https://agentlandline.dev/docs/tools) has every input and result.

## Example requests

- "Call the dentist on +49 … and move my appointment to next week, mornings only."
- "Ask the restaurant whether they have a table for four on Friday at 8 pm."
- "Call the landlord's office and ask when the heating repair is scheduled."

## Safety and privacy

- Every call starts with Agent Landline saying it is an AI assistant.
- Calls show your own verified number.
- Limits set in the task cannot be widened during the call. New proposals go back to your
  assistant first.
- No audio is recorded. Transcripts are deleted 30 days after a call.
- Hosted in Frankfurt. Details: [privacy policy](https://agentlandline.dev/privacy) ·
  [terms](https://agentlandline.dev/terms). Advertising or sales calls nobody asked for are
  not allowed.

## Pricing

Paid plans; see https://agentlandline.dev/pricing.

## Support

https://agentlandline.dev/support · hello@agentlandline.dev

Agent Landline is a product of thomatte solutions UG (haftungsbeschränkt), Germany.
[Legal notice](https://agentlandline.dev/legal-notice).
