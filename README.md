# Vesper Finance

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
