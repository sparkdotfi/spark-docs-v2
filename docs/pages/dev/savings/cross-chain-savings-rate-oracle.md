# Cross-chain Savings Rate Oracle

## Overview

The Cross-chain SSR Oracle reports the Sky Savings Rate (SSR) values across various bridges. This is primarily used to provide integrators the sUSDS/USDS conversion rate (the value of 1 sUSDS in USDS) as sUSDS is an accumulating token that increases in value against USDS over time. This oracle is used by the [Spark PSM](spark-psm.md), to enable swapping between USDS and sUSDS at the current conversion rate. Another example use case is decentralized exchanges leveraging the oracle to make liquidity management more capital efficient, by automatically moving sUSDS/USDS order book liquidity according to the conversion rate.

The oracle provides three sUSDS values in sync:&#x20;

* `ssr`: The per second Sky Savings Rate (compounding rate)
* `chi`: The rate accumulator
* `rho`: The last time chi was updated

These three values enables integrators to extrapolate an exact sUSDS/USDS conversion rate to any point in the future as long as the `ssr` value is not updated on Mainnet. Because this oracle does not need to be synced unless the `ssr` value changes, it uses canonical bridges for maximum security.

The oracle provides convenience functions to fetch the conversion rate at various levels of precision trading off gas efficiency. The specific details are covered in the Functions section below.

## Deployments

<table><thead><tr><th width="216">Network</th><th>Address</th></tr></thead><tbody><tr><td>Base</td><td><a href="https://basescan.org/address/0x65d946e533748a998b1f0e430803e39a6388f7a1#code">0x65d946e533748A998B1f0E430803e39A6388f7a1</a></td></tr></tbody></table>

Check the Spark Address Registry for the most up to date resource for contract deployments:

{% content-ref url="../deployments/spark-address-registry.md" %}
[spark-address-registry.md](../deployments/spark-address-registry.md)
{% endcontent-ref %}

## Contracts

* Contract Source: [Github](https://github.com/marsfoundation/xchain-ssr-oracle/tree/master)

### SSROracleBase

Contains common functionality shared between the Ethereum mainnet and cross-chain instances of the oracle. Contains convenience functions to fetch the conversion rate at various levels of precision trading off gas efficiency. sUSDS data is compressed into a single word to save SLOAD gas cost.

### SSRAuthOracle

Ensures the oracle receives data from an authorized data provider. This is intended to be one or more bridges which publish data to the oracle. Application-level sanity checks are included when new data is proposed to minimize damage in the event of a bridge being compromised. These sanity checks also enforce event ordering in case messages are relayed out of order. `maxSSR` is used as an upper bound for sanity checks to prevent malicious data from being proposed.

### Forwarders & Receivers

Forwarders and Receivers are bridge-specific messaging contracts. Forwarders permissionlessly relay `sUSDS` data. Receivers decode this message and forward it to the `SSRAuthOracle`. Please note that receivers are generic and part of the [`xchain-helpers` repository](https://github.com/marsfoundation/xchain-helpers).

### Functions

#### **Conversion Functions**

* **`getConversionRate()`**: Returns the current exact conversion rate for sUSDS/USDS with maximum precision as a 27 decimal number.
* **`getConversionRate(uint256 timestamp)`**: Returns the exact conversion rate for sUSDS/USDS for a specific `timestamp` as a 27 decimal number. Can be used to fetch future or conversion rates.
* **`getConversionRateBinomialApprox()`**: Returns a binominal approximation of the current conversion rate for sUSDS/USDS as a 27 decimal number. This approximation is more gas efficient than `getConversionRate`, but it does not give you the exact number.
* **`getConversionRateBinomialApprox(uint256 timestamp)`**: Returns a binominal approximation of the conversion rate for sUSDS/USDS for a specific `timestamp` in the future as a 27 decimal number. Can be used to approximate future conversion rates. This approximation is more gas efficient than `getConversionRate`, but it does not give you the exact number.
* **`getConversionRateLinearApprox()`**: Returns a linear approximation of the current conversion rate for sUSDS/USDS as a 27 decimal number. This approximation is more gas efficient than `getConversionRate`, but it does not give you the exact number.
* **`getConversionRateLinearApprox(uint256 timestamp)`**: Returns a linear approximation of the conversion rate for sUSDS/USDS for a specific `timestamp` in the future as a 27 decimal number. Can be used to approximate future conversion rates. This approximation is more gas efficient than `getConversionRate`, but it does not give you the exact number.

## Gotchas / Integration Concerns

### Future Conversions

Using the conversion functions for a future rate will only be correct if the Sky Savings Rate (ssr) is not changed in the interim. This rate can be changed by Sky Governance through a governance vote. This fact should be taken into consideration when using the future conversions. You cannot use this function to get past conversion rates.

### Gas and Precision Tradeoffs

The oracle contains three functions to provide the conversion rate, where one is a perfectly precise function, and the two others are approximations that in return are cheaper in gas. Depending on your use case, and if gas savings are critical you can elect to use an approximation instead of the exact value. Below is an overview of precision vs gas cost.

* `getConversionRate()`: exact value, highest gas cost
* `getConversionRateBinomialApprox():` higher precision, medium gas cost
* `getConversionRateLinearApprox():`  lower precision, lowest gas cost

### Rate Compounding

The Sky Savings Rate is a compounding rate that is stored in the rate accumulator `chi`. Using this value, the last time it was updated (`rho`), and the per second Sky Savings Rate (`ssr`), you can calculate the exact conversion rate for the current time using standard rate compounding calculations. If you are new to how Sky's rate mechanism works, you can find more information here: [Sky Savings Rate Mechanism](https://github.com/makerdao/developerguides/blob/master/mcd/intro-rate-mechanism/intro-rate-mechanism.md#dai-savings-rate).

## Additional resources

* [Cross-chain USDS & sUSDS](cross-chain-usds-and-susds.md)
* [Spark PSM](spark-psm.md)
* [Sky Savings Rate Mechanism](https://github.com/makerdao/developerguides/blob/master/mcd/intro-rate-mechanism/intro-rate-mechanism.md#dai-savings-rate)

