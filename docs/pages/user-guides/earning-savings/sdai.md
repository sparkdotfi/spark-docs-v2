# Savings DAI

:::info
**Note:** Savings DAI is the old version of Savings USDS. [Learn how to upgrade to sUSDS and earn a higher yield here.](/user-guides/converting-tokens/)
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

## Savings xDai on Gnosis Chain

Savings xDAI on Gnosis Chain will in most cases offer a higher yield than sDAI on Ethereum Mainnet. This is an intentional mechanic of how Savings xDAI is designed.

Gnosis Chain uses xDAI, which is DAI bridged from Ethereum to Gnosis Chain as its base network currency for fees. The bridged DAI is locked in a token bridge on Ethereum mainnet, where it is deposited into the Dai Savings Rate to earn yield. This means all DAI on Gnosis Chain, is earning the DSR. Gnosis Chain offers its own version of Savings DAI called Savings xDAI. For users to earn savings on Gnosis Chain, they must deposit xDAI it into the Gnosis Savings xDAI contract.
Gnosis has elected to distribute all the yield accrued for the entire bridged DAI supply only to Savings xDAI depositors on Gnosis Chain. This means Savings xDAI will offer a higher yield, due to the fact that not all xDAI is deposited into Savings xDAI. Therefore you will in most cases see a higher yield for Savings xDAI on Gnosis Chain than Savings DAI on Ethereum Mainnet.

- Savings xDAI Token Address: [0xaf204776c7245bf4147c2612bf6e5972ee483701](https://gnosisscan.io/token/0xaf204776c7245bf4147c2612bf6e5972ee483701)

- More info on Savings xDAI: [Gnosis Forum Post](https://forum.gnosis.io/t/deposit-dai-of-the-xdai-bridge-in-sdai-vault-from-spark/7236)