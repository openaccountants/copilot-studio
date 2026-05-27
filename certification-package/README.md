# OpenAccountants — Power Platform connector certification package

Files for the Microsoft Power Platform / Copilot Studio Verified Publisher connector certification submission.

## Files

| File | Purpose |
|---|---|
| `apiDefinition.swagger.json` | OpenAPI 2.0 spec describing the JSON-RPC MCP endpoint |
| `apiProperties.json` | Connector metadata (publisher, categories, brand color, MCP server flags) |
| `settings.json` | Local connector settings pointing at the artifacts above |
| `icon.png` | Brand mark (1:1, emerald `oa` circle, copied from openaccountants.com/logo-circle.png) |
| `README.md` | This file |

## Submission process (to be completed by Glimpse Ltd as Verified Publisher)

Per [Microsoft's Verified Publisher certification process](https://learn.microsoft.com/en-us/connectors/custom-connectors/submit-for-certification):

1. **Set up Microsoft Partner Center account** for Glimpse Ltd. One-time.
   → https://partner.microsoft.com/dashboard

2. **Set up Verified Credentials** via Microsoft Authenticator app. One-time.
   → https://learn.microsoft.com/en-us/connectors/custom-connectors/verified-credentials-ip

3. **Fork the connectors repo**.
   → https://github.com/microsoft/PowerPlatformConnectors

4. **Open a Proposal PR** titled `Proposal - OpenAccountants` to seed the submission. Include this README + an `intro.md`.

5. **Package and submit**:
   - Validate the package: run the [Package Validator tool](https://learn.microsoft.com/en-us/connectors/custom-connectors/certification-submission#step-7-validate-the-package-for-structure)
   - Update the PR with the full file set
   - Remove `Proposal -` from the PR title
   - Microsoft certification team comments `certify-connector` to trigger validation

6. **Wait ~15 business days** for review + deployment.

7. **Region deployment** notification by email when live.

## Key submission details

| Field | Value |
|---|---|
| Connector name | OpenAccountants |
| Publisher | Glimpse Ltd (OpenAccountants) |
| Publisher type | Verified Publisher (we own the underlying MCP server) |
| API endpoint | `https://www.openaccountants.com/api/mcp` |
| Authentication | None (public, read-only, rate-limited) |
| Transport | Streamable HTTP (JSON-RPC 2.0) |
| Categories | Productivity, Finance, AI |
| Privacy policy | `https://www.openaccountants.com/privacy` |
| Support email | `info@openaccountants.com` |
| Status | Production |
| Uptime SLA | 99.9% recommended target (matches Microsoft requirement) |

## After certification — marketing payoff

Per Microsoft's docs:
- Listed in [Connector reference](https://learn.microsoft.com/en-us/connectors/connector-reference/) — official documentation page
- Featured in the [Power Automate blog](https://flow.microsoft.com/blog/) new-connector announcement
- Shoutout on Power Automate Twitter account
- Listed across Copilot Studio, Power Automate, Power Apps, Logic Apps

That's the SEO + B2B-discovery reach that Microsoft enterprises actually use to find tools.
