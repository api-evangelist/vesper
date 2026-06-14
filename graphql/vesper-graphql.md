# Vesper Finance GraphQL Subgraph

## Overview

The Vesper Finance subgraph is deployed on The Graph protocol and provides a GraphQL API for querying on-chain pool data, revenue metrics, and token statistics for Vesper pools on Ethereum Mainnet.

- **Explorer**: https://thegraph.com/explorer/subgraph?id=0x9520b477aa81180e6ddc006fc09fb6d3eb4e807a-0
- **GitHub**: https://github.com/vesperfi/vesper-subgraph
- **Network**: Ethereum Mainnet
- **Protocol**: The Graph
- **Schema file**: [vesper-schema.graphql](vesper-schema.graphql)

## Endpoint

```
https://api.thegraph.com/subgraphs/name/vesperfi/vesper-subgraph
```

Local development endpoint (after `npm run dev`):

```
http://127.0.0.1:8000/subgraphs/name/vesperfi/vesper-subgraph/graphql
```

## Entities

### Pool

The primary entity representing a Vesper yield pool. Each pool is identified by its contract address.

| Field | Type | Description |
|-------|------|-------------|
| `id` | `ID!` | Pool contract address |
| `poolName` | `String!` | Name of the pool |
| `poolVersion` | `Int!` | Version of the pool (2 or 3) |
| `poolToken` | `String!` | Symbol of the shares token |
| `poolTokenDecimals` | `Int!` | Decimal precision of the pool token |
| `collateralToken` | `String!` | Symbol of the underlying collateral token |
| `collateralTokenDecimals` | `Int!` | Decimal precision of the collateral token |
| `totalSupply` | `BigInt!` | Total assets deposited, measured in pool tokens (shares) |
| `totalSupplyUsd` | `BigDecimal!` | `totalSupply` in USD |
| `totalDebt` | `BigInt!` | Total assets invested from the pool, in collateral token |
| `totalDebtUsd` | `BigDecimal!` | `totalDebt` in USD |
| `protocolRevenue` | `BigDecimal!` | 95% of withdraw/interest fees; measured in collateral asset |
| `protocolRevenueUsd` | `BigDecimal!` | `protocolRevenue` in USD |
| `supplySideRevenue` | `BigDecimal!` | 5% of withdraw/interest fees; measured in collateral asset |
| `supplySideRevenueUsd` | `BigDecimal!` | `supplySideRevenue` in USD |
| `totalRevenue` | `BigDecimal!` | Sum of `protocolRevenue` and `supplySideRevenue` |
| `totalRevenueUsd` | `BigDecimal!` | `totalRevenue` in USD |

## Example Query

```graphql
{
  pools(id: "0xpool-address-here") {
    id
    poolName
    poolVersion
    poolToken
    poolTokenDecimals
    collateralToken
    collateralTokenDecimals
    totalSupply
    totalSupplyUsd
    totalDebt
    totalDebtUsd
    protocolRevenue
    protocolRevenueUsd
    supplySideRevenue
    supplySideRevenueUsd
    totalRevenue
    totalRevenueUsd
  }
}
```

## Revenue Model

The Vesper revenue model splits fees between the protocol and liquidity providers:

- **Protocol Revenue (95%)**: Generated from withdrawal fees and interest fees, allocated to the protocol treasury.
- **Supply-Side Revenue (5%)**: The portion of fees returned to depositors/liquidity providers.

For more details, see the [Vesper Revenue Model documentation](https://docs.vesper.finance/vsp-economics/revenue-model).

## Event Handlers

The subgraph indexes the following on-chain events:

- **`Withdraw(indexed address, uint256, uint256)`** — calculates withdrawal fees for V2 and V3 pools.
- **`Deposit(indexed address, uint256, uint256)`** (V2) / **`Transfer(indexed address, indexed address, uint256)`** (V3) — calculates interest fees.
- **Block handlers** — updates `totalDebt` and `totalSupply` values per block.

## Deployment

The subgraph indexes Ethereum Mainnet production pools (stage: `prod`, chainId: `1`) from the [vesperfi/metadata](https://github.com/vesperfi/metadata) pool registry.
