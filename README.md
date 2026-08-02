# Viome

Viome (Viome Life Sciences) is a health technology company founded in 2016 by Naveen Jain. It uses
metatranscriptomic RNA sequencing — a technique originally developed for biodefense at Los Alamos
National Laboratory — plus AI to measure active gene expression across the gut microbiome, oral
microbiome, and human cells, from at-home stool, saliva, and finger-prick blood samples.

- Website — https://www.viome.com/
- Life Sciences division — https://www.viomelifesciences.com/
- Support — https://support.viome.com/
- Secondary market listing — https://forgeglobal.com/viome_stock/

## API posture

**Viome publishes no public API and no machine-readable API contract.** This was established by probe,
not by assumption — recorded here so later enrichment rounds do not repeat the hunt.

| Probe | Result |
|---|---|
| `api.viome.com` — `/openapi.json`, `/openapi.yaml`, `/swagger.json`, `/v1/openapi.json`, `/api-docs`, `/docs`, `/redoc`, `/graphql` | all **404** |
| `www.viome.com/openapi.json` | 404 |
| `developer.viome.com`, `docs.viome.com`, `developers.viome.com` | do not resolve (no DNS) |
| GraphQL introspection | no `/graphql` surface on any host |
| MCP `tools/list` | no MCP server; `mcp.viome.com` does not resolve; MCP registry search returns 0 |
| A2A `/.well-known/agent-card.json` and `/.well-known/agent.json` | 404 on `www.` and `api.`; **HTML SPA catch-all 200s** on `my.`, `app.`, `vpp.` — rejected as false positives |
| `/.well-known/*` (security.txt, openid-configuration, oauth-authorization-server, api-catalog, ai-plugin.json) | none published |
| npm / PyPI / RubyGems | no API client SDK |
| `github.com/Viome` | 4 public repos, all forks of unrelated third-party projects |

The consumer app at `my.viome.com` is backed by an **undocumented private HTTP backend**
(`/app/authenticate/credentials`, `/app/dashboard/user/external/results/…`) that is known only from a
third-party reverse-engineering gist. Viome publishes no specification, no documentation, and no terms
covering it, so it is **not** registered as an API here and no OpenAPI has been authored for it.

## What Viome does publish

A curated, high-quality **`llms.txt`** at <https://www.viome.com/llms.txt> — captured verbatim in
[`llms/viome-llms.txt`](llms/viome-llms.txt). Their `robots.txt` also carries an explicit AI-crawler
policy (OAI-SearchBot / ChatGPT-User / PerplexityBot / Google-Extended allowed; GPTBot and CCBot
disallowed). For a company with no API, that is a deliberate agent-facing posture.

## Artifacts

- `llms/viome-llms.txt` — verbatim `llms.txt` (searched)
- `packages/viome-packages.yml` — package-registry sweep (searched)
- `well-known/viome-well-known.yml` — `/.well-known/*` probe record incl. SPA false positives (probed)
- `security/viome-domain-security.yml` — TLS/HSTS/DNSSEC/CAA/SPF/DMARC (probed)
