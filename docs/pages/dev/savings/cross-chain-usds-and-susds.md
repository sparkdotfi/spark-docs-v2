# Cross-chain USDS & sUSDS

:::info
If you are looking to integrate Ethereum mainnet sUSDS, you should use [this documentation instead](/dev/savings/susds-token).
:::

## Overview

The Spark Liquidity Layer enables cross-chain liquidity of USDS and sUSDS. Integrators on these networks can tap into this liquidity by integrating these cross-chain tokens, and the [Spark PSM](/dev/savings/spark-psm).

The crosschain USDS and sUSDS tokens use the same simple ERC20 token implementation. The only difference between them is that sUSDS will increase in value over time according to the Sky Savings Rate. Converting between them on other networks can be done at no slippage or fees beyond gas using the Spark PSM. The crosschain sUSDS token does not contain any ERC4626 functionality - this is only available on Ethereum mainnet.

:::info
Savings USDS and the Sky Savings Rate are non-custodial and permissionless smart contracts offered by [Sky](https://sky.money), and is not issued by Spark. Spark does not have any control over the Sky Savings Rate or the sUSDS token.
:::

## Contract Details

* Type/Category: Token
* Contract Source: [Github](https://github.com/makerdao/usds/blob/master/src/Usds.sol)

### Deployment Addresses

| Network | Token | Address                                                                                                               |
| ------- | ----- | --------------------------------------------------------------------------------------------------------------------- |
| Base    | USDS  | [0x820C137fa70C8691f0e44Dc420a5e53c168921Dc](https://basescan.org/address/0x820c137fa70c8691f0e44dc420a5e53c168921dc) |
| Base    | sUSDS | [0x5875eEE11Cf8398102FdAd704C9E96607675467a](https://basescan.org/address/0x5875eee11cf8398102fdad704c9e96607675467a) |
| Arbitrum   | USDS  | [0x6491c05A82219b8D1479057361ff1654749b876b](https://arbiscan.io/address/0x6491c05A82219b8D1479057361ff1654749b876b) |
| Arbitrum   | sUSDS | [0xdDb46999F8891663a8F2828d25298f70416d7610](https://arbiscan.io/address/0xdDb46999F8891663a8F2828d25298f70416d7610) |

### ERC20 token functionality

The contract implements the functions specified in the ERC-20 interface.

* **`transfer`**: Transfers a specified amount of tokens from the caller's address to the specified recipient's address. It returns a boolean value indicating the success of the transfer.
* **`transferFrom`**: Transfers a specified amount of tokens from the **`from`** address to the **`to`** address. The transfer must be allowed by the **`from`** address by calling the **`approve`** function or by setting an allowance. It returns a boolean value indicating the success of the transfer.
* **`approve`**: Sets an allowance for a specific spender to spend a certain amount of tokens on behalf of the caller. It returns a boolean value indicating the success of the approval.

### Upgradeability

The contract uses the ERC-1822 UUPS pattern for upgradeability and the ERC-1967 proxy storage slots standard. It is important that the `SUsdsDeploy` library sequence be used for deploying.

### Events emitted

* **`Approval`**: This event is emitted when an approval is set for a specific address. It indicates that the owner has approved the spender to spend a certain amount of tokens.
* **`Transfer`**: This event is emitted when tokens are transferred from one address to another. It indicates the amount of tokens transferred and the addresses involved in the transfer.

## Additional resources

* [Spark Liquidity Layer](https://docs.spark.fi/user-guides/spark-liquidity-layer)
* [Spark PSM](/dev/savings/spark-psm)
* [sUSDS (Mainnet)](/dev/savings/susds-token)
* [Overview of](https://docs.spark.fi/user-guides/earning-savings/savings-usds#what-is-dsr-1)[ Sky Savings Rate](https://docs.spark.fi/user-guides/earning-savings/savings-usds#what-is-dsr-1)
* [EIP-4626](https://eips.ethereum.org/EIPS/eip-4626)
* [ERC-4626 Tokenized Vault Standard](https://ethereum.org/en/developers/docs/standards/tokens/erc-4626/)
