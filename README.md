# Vesper Finance

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Vesper Finance is a DeFi yield aggregator that enables users to deposit assets into
managed pools where automated yield strategies optimize returns across decentralized
finance protocols. The platform supports Ethereum, Polygon, Avalanche, and Optimism.

## APIs

This repository contains an APIs.json 0.19 profile for Vesper Finance covering:

- **Vesper Finance REST API** - Public API at `https://api.vesper.finance` providing
  pool performance data, APY/APR metrics, VSP token statistics, and historical TVL
- **Vesper Contracts API Reference** - Smart contract interface for direct on-chain
  integration via Web3/ethers.js
- **Vesper Subgraph API** - GraphQL access to on-chain Vesper data via The Graph

## Key REST Endpoints

| Endpoint | Description |
|----------|-------------|
| `GET /dashboard` | All pools with contract, strategy, and reward details |
| `GET /loan-rates` | 24-hour APY and APR for all pools |
| `GET /pools` | Full pool metadata including fees, risk levels, and earning rates |
| `GET /pools/:address/data-points` | Historical data points for a specific pool (past week) |
| `GET /values-locked` | Total value locked history across all pools (past month) |
| `GET /vsp-stats` | VSP token price, supply, market cap, and distribution data |

## Authentication

The Vesper Finance REST API is publicly accessible with no authentication required.

## Resources

- Website: https://vesper.finance/
- Documentation: https://docs.vesper.finance/
- Developer Guide: https://docs.vesper.finance/vesper-developers/vesper-developers-guide
- GitHub: https://github.com/vesperfi
- JavaScript Library: https://github.com/vesperfi/lib-js
- Subgraph: https://github.com/vesperfi/vesper-subgraph

## Maintainer

API Evangelist - https://apievangelist.com
