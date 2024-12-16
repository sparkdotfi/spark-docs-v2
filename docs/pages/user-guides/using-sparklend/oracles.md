---
description: Learn about the Oracles powering SparkLend.
---

# Oracles

SparkLend uses oracle price feeds to power its lending markets. Depending on the asset, different types of oracles are used, to ensure the proper pricing and risk management. The oracle price feeds are used to calculate the value of user collateral, and consequently how much a user can borrow, and when the system must liquidate risky positions.

## Oracle Providers

SparkLend uses [Chronicle](https://chroniclelabs.org/) and [Chainlink](https://chain.link/) as the main oracle providers for the lending markets. You can see which Oracle is used for the specific market on the [Markets page](#where-can-i-check-what-oracle-is-being-used).

## Where can I check what Oracle is being used?

On the [Spark App](https://app.spark.fi), in the “Borrow” dropdown menu in the top navigation bar, you can select “Markets”. From there, you click “Details” on the specific asset you wish to inspect, and scroll down to **Oracle type** section at the bottom. Here you will see the Oracle type, the current price, and the contract address for the Oracle smart contract.

## Who selects the Oracles?

[Sky](https://sky.money) Governance controls which oracles are used by the SparkLend markets.

## Types of Oracles

SparkLend uses different types of oracle price feeds depending on the asset and the lending market.

### Market Price

A Market Price oracle reflects the live market value of the asset. This means the price the asset is currently being traded at on various exchanges. An example is ETH which uses a Market Price oracle.

![](/assets/market-price.png)
*Market Price Oracle for ETH*

### Fixed Price

With a Fixed Price oracle, the asset price is set by a contract at a predefined value, adjustable only through Sky governance decisions. For example, stablecoins such as DAI uses a fixed price of 1.00 USD, and does not deviate even if the market price of DAI deviates from this value.

![](/assets/fixed-price.png)
*Fixed Price Oracle for Dai*

### Underlying Asset Price

For an Underlying Asset Price oracle, the asset price is derived from a market price oracle tracking the value of the _underlying asset_, and not the asset itself. For example, a derivative asset such as cbBTC, uses a market price feed for its underlying asset BTC, and not a market price for cbBTC.

![](/assets/underlying-asset.png)
*Underlying Asset Price for cbBTC*

### Yielding Fixed

For a Yielding Fixed oracle, the asset price is calculated using both an exchange rate and a market price oracle. The exchange rate is a conversion rate of the asset and its underlying asset. An example is yielding assets such as wstETH (Wrapped Staked ETH), which uses the exchange rate between wstETH and its underlying asset WETH (Wrapped ETH), multiplied by the market price of the underlying asset WETH.

![](/assets/yielding-fixed.png)
*Yielding Fixed Oracle for wstETH*

## Redundant Oracle Feeds

For certain assets SparkLend uses oracle price feeds from both Chronicle and Chainlink, ensuring that in the unlikely event one price feed should fail, a redundant price feed will automatically be used. Finally, in the extremely unlikely event that price feeds from both Chronicle and Chainlink should fail at the same time, a Uniswap TWAP (time-weighted average price), is used as a fallback price feed. This ensures maximum protection for SparkLend users. You can see an example of this mechanism above in the Yielding Fixed Oracle used for wstETH. \
You can check if an asset uses redundant price feeds, by checking if it says "Redundant" in its Oracle type, on the specific Market page. [See here where to check the oracle type.](#where-can-i-check-what-oracle-is-being-used)
