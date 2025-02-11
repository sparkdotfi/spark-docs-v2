# Savings Tokens
This page provides an overview of the different savings tokens available on Spark Savings: sUSDS and sDAI. Savings tokens represent deposits in the Sky Savings Rate (SSR) and the Dai Savings Rate (DSR) offered by Sky. The savings tokens enable users to receive returns on their deposits while still being able to transfer, stake, lend and use them in any way they want. All the savings tokens are ERC4626 compliant, and are accumulating tokens, meaning they increase in value over time against its base asset. Savings token are therefore not rebasing.

## Savings USDS

Savings USDS (sUSDS) is the upgraded version of sDAI, which offers higher yield than sDAI. sUSDS is a tokenized representation of USDS deposited in the Sky Savings Rate (SSR) offered by Sky. The sUSDS token enables users to receive returns on their SSR deposits while still being able to transfer, stake, lend and use it in any way they want. sUSDS is supported on various networks such as Ethereum and Base. You can find an overview of supported networks and token addresses [below](#supported-networks-and-token-addresses).

:::info
**Note:** Savings USDS and the Sky Savings Rate are non-custodial and permissionless smart contracts offered by Sky, and is not issued or deployed by Spark. Spark never has custody of funds deposited into or any control of the Sky Savings Rate or sUSDS token.
:::

sUSDS increases in value according to the SSR, as its USDS denominated value gradually increases over time. sUSDS is an accumulating token, not a rebasing token. Each sUSDS is fungible and always instantly redeemable for USDS. Deposited USDS is never locked, as it can always be withdrawn instantly. There are no liquidity constraints when withdrawing USDS from sUSDS or the SSR.

## What is the Sky Savings Rate?

Sky Savings Rate (SSR) is a feature of the Sky Protocol that enables any USDS holder to earn a savings rate on their USDS. The SSR is paid out in USDS.

The Sky Savings Rate is funded Sky's revenue, which includes fees from crypto collateralized loans, investments into US T-bills and its liquidity provisioning into SparkLend and Spark Liquidity Layer. You can find a full overview of revenue sources here: https://info.sky.money/collateral

You can always find the current Sky Savings Rate on the [Savings page in the Spark App](http://app.spark.fi/).

The Sky Savings Rate offers higher yield than the Dai Savings Rate.

The Sky Savings Rate is set by Sky Governance and is subject to change. Spark has no control over the Sky Savings Rate.

### Acquiring sUSDS

To acquire sUSDS and earn savings you can deposit USDS and other stablecoins using the [Spark App](https://app.spark.fi/).

### Supported Networks and Token Addresses

| Network  | Address                                                                                                                    |
| -------- | -------------------------------------------------------------------------------------------------------------------------- |
| Ethereum | [0xa3931d71877c0e7a3148cb7eb4463524fec27fbd](https://etherscan.io/address/0xa3931d71877c0e7a3148cb7eb4463524fec27fbd)      |
| Base     | [0x982f2DF63Fe38AB8d55f4B1464e8cfDc8eA5dEC8](https://basescan.org/address/0x982f2DF63Fe38AB8d55f4B1464e8cfDc8eA5dEC8#code) |

### Integrating sUSDS

For technical documentation on the sUSDS implementation and how to integrate please refer to the [Developer docs](/dev/savings/susds-token).

## Savings DAI

:::info
**Note:** Savings DAI is the old version of Savings USDS. [Learn how to upgrade to sUSDS and earn a higher yield here.](/user-guides/upgrading-to-usds-and-susds/upgrading-to-susds)
:::

Savings Dai (sDAI) is the old version of sUSDS. sDai is a tokenized representation of Dai deposited in the Dai Savings Rate (DSR) offered by Sky. The sDAI token enables users to receive returns on their DSR deposits while still being able to transfer, stake, lend and use it in any way they want.

:::info
**Note:** Savings Dai and the Dai Savings Rate are non-custodial and permissionless smart contracts offered by Sky, and are not issued or deployed by Spark. Spark does not have any control over the Sky Savings Rate or the sDAI token.
:::

sDAI increases in value according to the DSR, as its Dai denominated value gradually increases over time. sDAI is an accumulating token, not a rebasing token. Each sDAI is fungible and always instantly redeemable for DAI.

To acquire sDAI you can deposit Dai and other stablecoins using the [Spark App](https://app.spark.fi/).

For technical documentation on the sDAI implementation please refer to the [Developer docs](/dev/savings/sdai-token).

### What is the Dai Savings Rate?

Dai Savings Rate (DSR) is a feature of the Sky Protocol that enables any Dai holder to earn a savings rate on their Dai. The DSR is paid out in Dai.

Dai does not automatically earn savings, you must activate the DSR by depositing Dai into the Dai Savings Rate contract. The Dai is not locked and can always be instantly withdrawn.

The Dai Savings Rate is funded Sky's revenue, which includes fees from crypto collateralized loans, investments into US T-bills and its liquidity provisioning into SparkLend and Spark Liquidity Layer. You can find a full overview of revenue sources here: https://info.sky.money/collateral

The Dai Savings Rate is set by Sky Governance and is subject to change. Spark has no control over the Dai Savings Rate.