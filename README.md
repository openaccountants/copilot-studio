# OpenAccountants for Microsoft Copilot Studio

Two ways to use [OpenAccountants](https://www.openaccountants.com) tax skills inside Microsoft Copilot Studio via MCP.

Skills include accountant-reviewed versions and source-cited drafts. Check the [current catalogue](https://www.openaccountants.com/skills) and [review method](https://www.openaccountants.com/review-method) for each skill's review status, reviewer, version and review date. Authorship or a jurisdiction lead's name does not establish professional review of every skill version.

## Option A — add to your own tenant (today, ~3 minutes)

Any Copilot Studio admin can add OpenAccountants as an MCP server directly. No certification, no marketplace listing required.

**Prerequisite:** [generative orchestration](https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-generative-actions) must be enabled on your agent.

1. Open your agent in [Microsoft Copilot Studio](https://copilotstudio.microsoft.com).
2. Go to **Tools → Add a tool → Custom → Model Context Protocol (MCP)**.
3. Enter:
   - **Server name:** `OpenAccountants`
   - **Server URL:** `https://www.openaccountants.com/api/mcp`
   - **Authentication:** None
   - **Description:** *Tax skills with sources and published review status via OpenAccountants MCP.*
4. Click **Add**. The Copilot Studio wizard discovers the current tools and schemas. Select the retrieval tools the agent needs, such as `start`, `list_skills`, `get_skill`, `get_skill_sections` and `search_skills`. Tools that save or send information require a separate workflow and the user's explicit agreement to share the specified information.
5. Save and publish your agent.

Your agent now has on-demand access to every published OpenAccountants tax skill. Preserve the fetched skill's review status in the answer. The [Calendly](https://calendly.com/openaccountants-info/30min) handoff provides a way to seek professional review.

📸 **Screenshots:** see [`docs/screenshots.md`](./docs/screenshots.md).

## Option B — wait for the certified marketplace listing (~15+ business days)

OpenAccountants is in the process of being submitted as a **Verified Publisher Connector** in the Microsoft Power Platform connector directory. Once certified, any Copilot Studio user can install the connector with one click from the marketplace without manual wizard steps.

Status: certification package built (this repo's [`certification-package/`](./certification-package/)); pending submission via PR to [`microsoft/PowerPlatformConnectors`](https://github.com/microsoft/PowerPlatformConnectors). Microsoft Partner Center registration + Verified Credentials setup required before submission.

## What you get

| Tool | Purpose |
|---|---|
| `start` | Front door — pass intent + jurisdiction → ready-to-execute plan |
| `list_skills` | List published skills filtered by jurisdiction or category |
| `get_skill` | Fetch full markdown + provenance footer for one skill |
| `get_skill_sections` | Same content split into sections (for very large skills) |
| `search_skills` | Keyword search across published skill content |

The 5 retrieval tools listed above are read-only. The MCP server is rate-limited (60 req/min per IP) but otherwise unmetered.

## Jurisdictions

Deep packs for Malta · UK · Germany · Italy · France · Spain · Portugal · Ireland · Netherlands · US federal + 24 deep state packs (CA, NY, TX, FL, IL, OH, PA, MA, NJ, NC, MI, OR, WA, NH, DE, VA, GA, AZ, CO, NV, MN, MO, MD…) · Canada federal + provincial · India · Indonesia · China (in 简体中文) · Pakistan · Brazil (in PT-BR) · Saudi Arabia · South Africa · Nigeria · Kenya · and more.

## Disclaimer

These skills produce **working papers, not filed returns**. Preserve the provenance and professional contact details returned by the service. Attribute professional review only when the fetched version's published review record identifies it; otherwise describe it as unconfirmed. No client–accountant relationship is created by reading or applying these skills.

## Links

- Website: [openaccountants.com](https://www.openaccountants.com)
- Skills source: [github.com/openaccountants/openaccountants](https://github.com/openaccountants/openaccountants); [content terms](https://github.com/openaccountants/openaccountants/blob/main/LICENSING.md)
- MCP server: `https://www.openaccountants.com/api/mcp`
- Verified accountant network: [openaccountants.com/network](https://www.openaccountants.com/network)
- Book a verified accountant: [calendly.com/openaccountants-info/30min](https://calendly.com/openaccountants-info/30min)

## Licence

MIT for this repository. Skill content has separate terms from this wrapper. The source repository's [licensing document](https://github.com/openaccountants/openaccountants/blob/main/LICENSING.md) describes the source-available Open Accountants Skills License, commercial options, third-party copyleft exceptions and prior AGPL releases. Check the terms for the skill version you use.
