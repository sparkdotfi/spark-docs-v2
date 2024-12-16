---
description: Learn about sUSDS and the Sky Savings Rate.
---

# Savings USDS

## What is sUSDS?

Savings USDS (sUSDS) is the upgraded version of sDAI, which offers higher yield than sDAI. sUSDS is a tokenized representation of USDS deposited in the Sky Savings Rate (SSR) offered by Sky. The sUSDS token enables users to receive returns on their SSR deposits while still being able to transfer, stake, lend and use it in any way they want. sUSDS is supported on various networks such as Ethereum and Base. You can find an overview of supported networks and token addresses [below](#supported-networks-and-token-addresses).

:::info
**Note:** Savings USDS and the Sky Savings Rate are non-custodial and permissionless smart contracts offered by Sky, and is not issued or deployed by Spark. Spark never has custody of funds deposited into or any control of the Sky Savings Rate or sUSDS token.
:::

sUSDS increases in value according to the SSR, as its USDS denominated value gradually increases over time. sUSDS is an accumulating token, not a rebasing token. Each sUSDS is fungible and always instantly redeemable for USDS. Deposited USDS is never locked, as it can always be withdrawn instantly. There are no liquidity constraints when withdrawing USDS from sUSDS or the SSR.

### Acquiring sUSDS

To acquire sUSDS and earn savings you can deposit USDS and other stablecoins using the [Spark App](https://app.spark.fi/).

### Supported Networks and Token Addresses

| Network  | Address                                                                                                                    |
| -------- | -------------------------------------------------------------------------------------------------------------------------- |
| Ethereum | [0xa3931d71877c0e7a3148cb7eb4463524fec27fbd](https://etherscan.io/address/0xa3931d71877c0e7a3148cb7eb4463524fec27fbd)      |
| Base     | [0x982f2DF63Fe38AB8d55f4B1464e8cfDc8eA5dEC8](https://basescan.org/address/0x982f2DF63Fe38AB8d55f4B1464e8cfDc8eA5dEC8#code) |

### Integrating sUSDS

For technical documentation on the sUSDS implementation and how to integrate please refer to the [Developer docs](/dev/savings/susds-token).

## What is the Sky Savings Rate?

Sky Savings Rate (SSR) is a feature of the Sky Protocol that enables any USDS holder to earn a savings rate on their USDS. The SSR is paid out in USDS.

The Sky Savings Rate is funded by the borrowing fees accrued by the Sky Protocol. You can always find the current Sky Savings Rate on the [Savings page in the Spark App](http://app.spark.fi/).

The Sky Savings Rate offers higher yield than the Dai Savings Rate.

The Sky Savings Rate is set by Sky Governance and is subject to change. Spark has no control over the Sky Savings Rate.
