# Savings USDS

Savings USDS (sUSDS) is the upgraded version of sDAI, which offers higher yield than sDAI. sUSDS is a tokenized representation of USDS deposited in the Sky Savings Rate (SSR) offered by Sky. The sUSDS token enables users to receive returns on their SSR deposits while still being able to transfer, stake, lend and use it in any way they want. sUSDS is supported on various networks such as Ethereum and Base. You can find an overview of supported networks and token addresses [below](#supported-networks-and-token-addresses).

:::info
**Note:** Savings USDS and the Sky Savings Rate are non-custodial and permissionless smart contracts offered by Sky, and is not issued or deployed by Spark. Spark never has custody of funds deposited into or any control of the Sky Savings Rate or sUSDS token.
:::

sUSDS increases in value according to the SSR, as its USDS denominated value gradually increases over time. sUSDS is an accumulating token, not a rebasing token. Each sUSDS is fungible and always instantly redeemable for USDS. Deposited USDS is never locked, as it can always be withdrawn instantly. There are no liquidity constraints when withdrawing USDS from sUSDS or the SSR.

## Yield Source

The yield source for USDS is the Sky Savings Rate (SSR), which is a feature of the Sky Protocol that enables any USDS holder to earn a savings rate on their USDS. The SSR is paid out in USDS.

The Sky Savings Rate is funded by Sky's revenue, which includes fees from crypto collateralized loans, investments into U.S. treasury bills and its liquidity provisioning into SparkLend and the Spark Liquidity Layer. You can find a full overview of revenue sources here: https://info.sky.money/collateral

You can always find the current Sky Savings Rate on the [Savings page in the Spark App](http://app.spark.fi/).

The Sky Savings Rate offers higher yield than the Dai Savings Rate.

The Sky Savings Rate is set by Sky Governance and is subject to change. Spark has no control over the Sky Savings Rate.

## Acquiring sUSDS

To acquire Savings Tokens you can deposit stablecoins into Savings Vault using the [Spark App](https://app.spark.fi/).
See the [Earning Savings](/user-guides/earning-savings/) for a guide on how to deposit.


## Supported Networks and Token Addresses

| Network  | Token | Address                                                                                                                    |
| -------- | ----- | ---------------------------------------------------------------------------------------------------------------------------|
| Ethereum | USDS  | [0xdC035D45d973E3EC169d2276DDab16f1e407384F](https://etherscan.io/address/0xdC035D45d973E3EC169d2276DDab16f1e407384F)      |
| Ethereum | sUSDS | [0xa3931d71877c0e7a3148cb7eb4463524fec27fbd](https://etherscan.io/address/0xa3931d71877c0e7a3148cb7eb4463524fec27fbd)      |
| Base     | USDS  | [0x820C137fa70C8691f0e44Dc420a5e53c168921Dc](https://basescan.org/address/0x820C137fa70C8691f0e44Dc420a5e53c168921Dc) |
| Base     | sUSDS | [0x5875eEE11Cf8398102FdAd704C9E96607675467a](https://basescan.org/address/0x5875eEE11Cf8398102FdAd704C9E96607675467a) |
| Arbitrum | USDS  | [0x6491c05A82219b8D1479057361ff1654749b876b](https://arbiscan.io/address/0x6491c05A82219b8D1479057361ff1654749b876b)       |
| Arbitrum | sUSDS | [0xdDb46999F8891663a8F2828d25298f70416d7610](https://arbiscan.io/address/0xdDb46999F8891663a8F2828d25298f70416d7610)       |

## Integrating Savings Vaults

For technical documentation on the sUSDS implementation and how to integrate please refer to the [Developer docs](/dev/savings/susds-token).