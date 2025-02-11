# Savings DAI

:::info
**Note:** Savings DAI is the old version of Savings USDS. [Learn how to upgrade to sUSDS and earn a higher yield here.](/user-guides/upgrading-to-usds-and-susds/upgrading-to-susds)
:::

Savings Dai (sDAI) is the old version of sUSDS. sDai is a tokenized representation of Dai deposited in the Dai Savings Rate (DSR) offered by Sky. The sDAI token enables users to receive returns on their DSR deposits while still being able to transfer, stake, lend and use it in any way they want.

:::info
**Note:** Savings Dai and the Dai Savings Rate are non-custodial and permissionless smart contracts offered by Sky, and are not issued or deployed by Spark. Spark does not have any control over the Sky Savings Rate or the sDAI token.
:::

sDAI increases in value according to the DSR, as its Dai denominated value gradually increases over time. sDAI is an accumulating token, not a rebasing token. Each sDAI is fungible and always instantly redeemable for DAI.

## Yield Source

The yield source for sDAI is the Dai Savings Rate (DSR), which is a feature of the Sky Protocol that enables any Dai holder to earn a savings rate on their Dai. The DSR is paid out in Dai.

Dai does not automatically earn savings, you must activate the DSR by depositing Dai into the Dai Savings Rate contract. The Dai is not locked and can always be instantly withdrawn.

The Dai Savings Rate is funded by Sky's revenue, which includes fees from crypto collateralized loans, investments into U.S. treasury bills and its liquidity provisioning into SparkLend and the Spark Liquidity Layer. You can find a full overview of revenue sources here: https://info.sky.money/collateral

The Dai Savings Rate is set by Sky Governance and is subject to change. Spark has no control over the Dai Savings Rate.

## Acquiring Savings Tokens

To acquire Savings Tokens you can deposit stablecoins into Savings Vault using the [Spark App](https://app.spark.fi/).
See the [Earning Savings](/user-guides/earning-savings/) for a guide on how to deposit.

For technical documentation on the sDAI implementation please refer to the [Developer docs](/dev/savings/sdai-token).

## Supported Networks and Token Addresses

| Network  | Address                                                                                                                    |
| -------- | -------------------------------------------------------------------------------------------------------------------------- |
| Ethereum | [0x83f20f44975d03b1b09e64809b757c47f942beea](https://etherscan.io/address/0x83f20f44975d03b1b09e64809b757c47f942beea)      |

## Integrating Savings Vaults

For technical documentation on the sDAI implementation and how to integrate please refer to the [Developer docs](/dev/savings/sdai-token).