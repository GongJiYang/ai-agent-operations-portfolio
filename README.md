# AI Agent Operations Portfolio

Static portfolio for the AgentOps Desk and FleetLens case studies.

## Local preview

```bash
cd portfolio-site
python3 -m http.server 8090
```

Open `http://localhost:8090`.

## Deploy the portfolio

This folder includes a Render Blueprint. Push the folder to a GitHub repository, then in Render choose **New → Blueprint** and select the repository. Render reads `render.yaml` and publishes the site as a static service.

Equivalent hosts such as Netlify, Cloudflare Pages, or GitHub Pages can publish this folder directly. There is no build step and no runtime secret.

## Deploy FleetLens

1. Push `fleetlens-mcp` to its own GitHub repository.
2. In Render, choose **New → Blueprint** and select that repository.
3. Render runs the renderer build and publishes `packages/renderer/dist/web`.
4. Confirm the landing page opens, then choose **Open Revenue Command Center** to exercise the seeded portfolio dashboard.

The FleetLens demo is static and uses only the seeded datasets included in the repository.

## Deploy AgentOps Desk

1. Push `agentops-console` to its own private or public GitHub repository.
2. In Render, choose **New → Blueprint** and select that repository.
3. Wait for the Python service health check at `/dash`.
4. Open `/dash` and sign in with `agentops-demo`.

The included blueprint deliberately runs `AGENTOPS_DEMO=true` with a known demo token and an ephemeral SQLite database. It is safe only for the seeded public portfolio demo: do not connect real plugins, credentials, accounts, or customer data to this deployment.

For a real deployment, remove `AGENTOPS_DEMO`, generate a secret `MCP_AUTH_TOKEN`, use persistent encrypted storage for `GATEWAY_DB_PATH`, set `MCP_BASE_URL` to the public HTTPS origin, and restrict network access as required.

## Deployment acceptance checks

- Portfolio: home page and `resume.html` return HTTP 200; both case studies remain readable at 390 px and 1440 px widths.
- FleetLens: no browser console errors; revenue dashboard shows `$1.05M` open pipeline, `$599K` weighted forecast, 12 active deals, and four filters.
- AgentOps Desk: `/dash` accepts the demo token; the overview, risk watchlist, audit evidence, and review action pages load from seeded data.
