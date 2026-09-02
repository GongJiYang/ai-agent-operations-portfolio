# AI Agent Operations Portfolio

Static portfolio for the AgentOps Desk and FleetLens case studies.

**[Open the published portfolio](https://gongjiyang.github.io/ai-agent-operations-portfolio/)**

## Local preview

```bash
cd portfolio-site
python3 -m http.server 8090
```

Open `http://localhost:8090`.

## Published demos

- [Portfolio and printable resume](https://gongjiyang.github.io/ai-agent-operations-portfolio/)
- [AgentOps Desk interactive review demo](https://gongjiyang.github.io/agentops-console/)
- [FleetLens Revenue Command Center](https://gongjiyang.github.io/fleetlens-mcp/)

Each repository includes a GitHub Pages workflow. A push to `main` rebuilds and deploys its public demo.

FleetLens is a static React build backed by the seeded datasets in the repository. AgentOps exports its authenticated, seeded operations dashboard into an interactive static artifact; review decisions are browser-local and no credentials or customer data are present.

The AgentOps Render Blueprint remains available for a full server-side deployment. It deliberately runs `AGENTOPS_DEMO=true` with a known demo token and an ephemeral SQLite database. Do not connect real plugins, credentials, accounts, or customer data to that deployment. For production, remove `AGENTOPS_DEMO`, generate a secret `MCP_AUTH_TOKEN`, use persistent encrypted storage for `GATEWAY_DB_PATH`, set `MCP_BASE_URL` to the public HTTPS origin, and restrict network access.

## Deployment acceptance checks

- Portfolio: home page and `resume.html` return HTTP 200; both case studies remain readable at 390 px and 1440 px widths.
- FleetLens: no browser console errors; revenue dashboard shows `$1.05M` open pipeline, `$599K` weighted forecast, 12 active deals, and four filters.
- AgentOps Desk: `/dash` accepts the demo token; the overview, risk watchlist, audit evidence, and review action pages load from seeded data.
