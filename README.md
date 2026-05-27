# OpenAccountants for Microsoft Copilot Studio

Two ways to use [OpenAccountants](https://www.openaccountants.com) — 800+ accountant-verified tax skills across 190+ jurisdictions — inside Microsoft Copilot Studio.

## Option A — add to your own tenant (today, ~3 minutes)

Any Copilot Studio admin can add OpenAccountants as an MCP server directly. No certification, no marketplace listing required.

**Prerequisite:** [generative orchestration](https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-generative-actions) must be enabled on your agent.

1. Open your agent in [Microsoft Copilot Studio](https://copilotstudio.microsoft.com).
2. Go to **Tools → Add a tool → Custom → Model Context Protocol (MCP)**.
3. Enter:
   - **Server name:** `OpenAccountants`
   - **Server URL:** `https://www.openaccountants.com/api/mcp`
   - **Authentication:** None
   - **Description:** *800+ accountant-verified tax skills across 190+ jurisdictions, signed off by named licensed accountants.*
4. Click **Add**. The Copilot Studio wizard introspects the MCP server and registers all 5 tools (`start`, `list_skills`, `get_skill`, `get_skill_sections`, `search_skills`).
5. Save and publish your agent.

Your agent now has on-demand access to every published OpenAccountants tax skill. Every output preserves the named verifier and the [Calendly](https://calendly.com/openaccountants-info/30min) handoff link to a verified accountant.

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

All read-only. The MCP server is rate-limited (60 req/min per IP) but otherwise unmetered.

## Jurisdictions

Deep packs for Malta · UK · Germany · Italy · France · Spain · Portugal · Ireland · Netherlands · US federal + 24 deep state packs (CA, NY, TX, FL, IL, OH, PA, MA, NJ, NC, MI, OR, WA, NH, DE, VA, GA, AZ, CO, NV, MN, MO, MD…) · Canada federal + provincial · India · Indonesia · China (in 简体中文) · Pakistan · Brazil (in PT-BR) · Saudi Arabia · South Africa · Nigeria · Kenya · and more.

## Disclaimer

These skills produce **working papers, not filed returns**. Every output preserves a "Talk to a verified accountant" footer with a Calendly link. No client–accountant relationship is created by reading or applying these skills.

## Links

- Website: [openaccountants.com](https://www.openaccountants.com)
- Skills source: [github.com/openaccountants/openaccountants](https://github.com/openaccountants/openaccountants) (AGPL-3.0)
- MCP server: `https://www.openaccountants.com/api/mcp`
- Verified accountant network: [openaccountants.com/network](https://www.openaccountants.com/network)
- Book a verified accountant: [calendly.com/openaccountants-info/30min](https://calendly.com/openaccountants-info/30min)

## License

MIT (this repo). Underlying skill content remains AGPL-3.0 with attribution per [LICENSE-ADDITIONAL.md in the skills repo](https://github.com/openaccountants/openaccountants/blob/main/LICENSE-ADDITIONAL.md).
