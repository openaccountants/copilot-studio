# Adding OpenAccountants to Microsoft Copilot Studio — visual walkthrough

> Screenshots from a fresh Copilot Studio environment. Total time: ~3 minutes from open agent to live MCP tools.

## Step 1 — Open your agent and go to Tools

In your Copilot Studio agent, open the **Tools** tab.

> *[Screenshot placeholder: Tools tab in Copilot Studio agent]*

## Step 2 — Add a new tool

Click **Add a tool** → **Custom** → **Model Context Protocol**.

> *[Screenshot placeholder: tool type selection panel showing the MCP option]*

## Step 3 — Configure the MCP server

Fill in:
- **Server name:** `OpenAccountants`
- **Server URL:** `https://www.openaccountants.com/api/mcp`
- **Authentication:** None (the OpenAccountants MCP endpoint is public and rate-limited)
- **Description:** *Tax skills with sources and version-specific review status. Check each fetched version's published review record.*

Click **Add server**.

> *[Screenshot placeholder: MCP server configuration form filled with the values above]*

## Step 4 — Confirm tool discovery

The wizard discovers the server's current tools and their schemas. The following read tools cover skill retrieval:

- `start` — front door, returns a ready-to-execute plan
- `list_skills` — list published skills with filters
- `get_skill` — fetch one skill with provenance footer
- `get_skill_sections` — same content split into sections
- `search_skills` — keyword search

> *[Screenshot placeholder: discovered tool list with descriptions and permissions]*

Click **Add to agent** for each tool the agent needs. The server may also advertise tools that save or send information. Expose those only for a workflow that requires them, and use them only at the user's explicit request with agreement to share the specified information.

## Step 5 — Save and publish

Save your agent and publish. The next time it's invoked, it'll have full access to OpenAccountants.

> *[Screenshot placeholder: agent test panel with a sample tax question + the agent calling get_skill in response]*

## Example test conversation

After publishing, ask your agent:

> **You:** I'm a Maltese freelancer earning EUR 45,000 from foreign clients. What VAT obligations do I have?
>
> **Agent:** *Calls `start({intent: "VAT", jurisdiction: "MT"})` → sees malta-vat-return in the plan → calls `get_skill({slug: "malta-vat-return"})` → walks the user through Article 10 vs Article 11, the EUR 35,000 threshold, EU reverse charge logic, and cites the fetched skill and its published review status. Name a reviewer only when that version's record identifies one; preserve its available Calendly link.*

If you get this kind of response, the integration is working.

## Troubleshooting

| Problem | Fix |
|---|---|
| "Generative orchestration is required" | Enable it: agent settings → Generative AI → Generative orchestration ON |
| Tools don't appear after adding the server | Refresh the page. Discovery takes a few seconds the first time. |
| 429 rate-limit errors | The MCP endpoint is rate-limited to 60 req/min per IP. A busy enterprise agent shouldn't hit it. If you do, contact `info@openaccountants.com` for a dedicated allocation. |
| HTTP 5xx errors | Server-side. Email `info@openaccountants.com` with the request timestamp and we'll investigate. Status page coming soon. |
