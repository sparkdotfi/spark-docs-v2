# Savings USDC

sUSDC is a tokenized representation of USDC deposited in the Savings USDC Vault. The Savings USDC vault deposits USDC into the Sky Savings Rate (SSR) offered by Sky. The sUSDC token enables users to receive returns on their SSR deposits while still being able to transfer, stake, lend and use it in any way they want. sUSDC is supported on various networks such as Ethereum, Base and Arbitrum. You can find an overview of supported networks and token addresses [below](#supported-networks-and-token-addresses).

:::info
**Note:** The Sky Savings Rate is a non-custodial and permissionless smart contract offered by Sky. Spark never has custody of funds deposited into or any control of the Sky Savings Rate.
:::

sUSDC increases in value according to the SSR, as its USDC denominated value gradually increases over time. sUSDC is an accumulating token, not a rebasing token. 

## Yield Source

The yield source for USDC is the Sky Savings Rate (SSR), which is a feature of the Sky Protocol that enables users to earn a savings rate on their USDS. It is therefore similar to sUSDS, except that it is denominated in USDC.

The USDC Savings vault exchanges USDC for USDS using the Sky PSM, and deposits it into the the Sky Savings Rate. When users withdraw, the USDS is exchanged back to USDC using the Sky PSM. This is a 1:1 swap with no slippage or fees besides network fees. The Spark Liquidity Layer ensures there is always enough USDC liquidity to redeem sUSDC for USDC even for large sizes. This is possible due to Sky keeping 25 % of USDS backing in cash reserves, such as USDC. This results in readily available liquidity in the billions.
You can always check the current yield of sUSDC on the Spark App.

The Sky Savings Rate is funded by Sky's revenue, which includes fees from crypto collateralized loans, investments into U.S. treasury bills and its liquidity provisioning into SparkLend and the Spark Liquidity Layer. You can find a full overview of revenue sources here: https://info.sky.money/collateral

You can always find the current Sky Savings Rate on the [Savings page in the Spark App](http://app.spark.fi/).

The Sky Savings Rate is set by Sky Governance and is subject to change. Spark has no control over the Sky Savings Rate.

## Acquiring sUSDC

To acquire Savings Tokens you can deposit stablecoins into Savings Vault using the [Spark App](https://app.spark.fi/).
See the [Earning Savings](/user-guides/earning-savings/) for a guide on how to deposit.


## Supported Networks and Token Addresses

| Network  | Token | Address                                                                                                                    |
| -------- | ----- | ---------------------------------------------------------------------------------------------------------------------------|
| Ethereum | sUSDC | [0xBc65ad17c5C0a2A4D159fa5a503f4992c7B545FE](https://etherscan.io/address/0xBc65ad17c5C0a2A4D159fa5a503f4992c7B545FE)      |
| Base     | sUSDC | [0x3128a0F7f0ea68E7B7c9B00AFa7E41045828e858](https://basescan.org/address/0x3128a0F7f0ea68E7B7c9B00AFa7E41045828e858) |      |
| Arbitrum | sUSDC | [0x940098b108fB7D0a7E374f6eDED7760787464609](https://arbiscan.io/address/0x940098b108fB7D0a7E374f6eDED7760787464609)       |

## Integrating Savings Vaults

For technical documentation on the sUSDC implementation and how to integrate please refer to the [Developer docs](/dev/savings/susdc-token).