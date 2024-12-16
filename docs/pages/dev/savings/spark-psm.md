# Spark PSM

## Overview

The Spark PSM extends the Sky PSM liquidity on Ethereum mainnet to other chains, starting with Base. It allows swaps between USDS, sUSDS, and USDC with no slippage or fees beyond gas, making it the top liquidity source for these pairs in DeFi. This enables holders of USDC on supported networks to easily acquire sUSDS to earn yield, at no cost beyond gas.

## Contract Details

* Contract Name: PSM3.sol
* Contract Source: [Spark PSM code repository](https://github.com/marsfoundation/spark-psm)

### Deployments

| Network  | Spark PSM Address                                                                                                     |
| -------- | --------------------------------------------------------------------------------------------------------------------- |
| B**ase** | [0x1601843c5E9bC251A3272907010AFa41Fa18347E](https://basescan.org/address/0x1601843c5E9bC251A3272907010AFa41Fa18347E) |

### State Variables and Immutables

* **`usdc`**: IERC20 interface of USDC.
* **`usds`**: IERC20 interface of USDS.
* **`susds`**: IERC20 interface of sUSDS. Note that this is an ERC20 and not a ERC4626 because it's not on mainnet.
* **`pocket`**: Address that holds custody of USDC. The `pocket` can deploy USDC to yield-bearing strategies. Defaulted to the address of the PSM itself.
* **`rateProvider`**: Contract that returns a conversion rate between and sUSDS and USD in 1e27 precision. [See Cross-chain Savings Rate Oracle for more information.](cross-chain-savings-rate-oracle.md)
* **`totalShares`**: Total shares in the PSM. Shares represent the ownership of the underlying assets in the PSM.
* **`shares`**: Mapping of user addresses to their shares.

### Functions

#### **Admin Functions**

* **`setPocket`**: Sets the `pocket` address. Only the `owner` can call this function. This is a very important and sensitive action because it transfers the entire balance of USDC to the new `pocket` address. OZ Ownable is used for this function, and `owner` will always be set to the governance proxy.

#### **Swap Functions**

* **`swapExactIn`**: Allows swapping of assets based on current conversion rates, specifying an `amountIn` of the asset to swap. Ensures the derived output amount is above the `minAmountOut` specified by the user before executing the transfer and emitting the swap event. Includes a referral code.
* **`swapExactOut`**: Allows swapping of assets based on current conversion rates, specifying an `amountOut` of the asset to receive from the swap. Ensures the derived input amount is below the `maxAmountIn` specified by the user before executing the transfer and emitting the swap event. Includes a referral code.

#### **Liquidity Provision Functions**

* **`deposit`**: Deposits assets into the PSM, minting new shares. Includes a referral code.
* **`withdraw`**: Withdraws assets from the PSM by burning shares. Ensures the user has sufficient shares for the withdrawal and adjusts the total shares accordingly. Includes a referral code.

#### **Preview Functions**

* **`previewDeposit`**: Estimates the number of shares minted for a given deposit amount.
* **`previewWithdraw`**: Estimates the number of shares burned and the amount of assets withdrawn for a specified amount.
* **`previewSwapExactIn`**: Estimates the amount of `assetOut` received for a given amount of `assetIn` in a swap.
* **`previewSwapExactOut`**: Estimates the amount of `assetIn` required to receive a given amount of `assetOut` in a swap.

#### **Conversion Functions**

{% hint style="warning" %}
**NOTE:** These functions do not round in the same way as preview functions, so they are meant to be used for general quoting purposes.
{% endhint %}

* **`convertToAssets`**: Converts shares to the equivalent amount of a specified asset.
* **`convertToAssetValue`**: Converts shares to their equivalent value in USD terms with 18 decimal precision.
* **`convertToShares`**: Converts asset values to shares based on the current exchange rate.

#### **Asset Value Functions**

* **`totalAssets`**: Returns the total value of all assets held by the PSM denominated in USD with 18 decimal precision.

#### Events

* **`Swap`**: Emitted on asset swaps.
* **`Deposit`**: Emitted on asset deposits.
* **`Withdraw`**: Emitted on asset withdrawals.

## Key Mechanisms & Concepts

### **Fetch Liquidity**

You can fetch the liquidity of the PSM3 by checking the USDS and sUSDS ERC20 token balances deposited in the PSM3 contract. USDC liquidity is being kept in the `pocket` address, but currently this address is set to the PSM3 contract itself, however it could be different in the future.

### **Pricing**

USDS and USDC are always converted at a fixed 1:1 ratio.

sUSDS is a yield accumulating token, meaning its price will increase vs USDS/USDC over time. A [rate provider oracle](cross-chain-savings-rate-oracle.md) is used to provide the sUSDS price.

## Additional resources

* [Cross-chain USDS & sUSDS](cross-chain-usds-and-susds.md)
* [Cross-chain Savings Rate Oracle](cross-chain-savings-rate-oracle.md)
