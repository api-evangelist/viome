# Viome

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
