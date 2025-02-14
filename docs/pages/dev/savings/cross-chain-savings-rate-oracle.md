# Cross-chain Savings Rate Oracle

## Overview

The Cross-chain SSR Oracle reports the Sky Savings Rate (SSR) values across various bridges. This is primarily used to provide integrators the sUSDS/USDS conversion rate (the value of 1 sUSDS in USDS) as sUSDS is an accumulating token that increases in value against USDS over time. This oracle is used by the [Spark PSM](/dev/savings/spark-psm), to enable swapping between USDS and sUSDS at the current conversion rate. Another example use case is decentralized exchanges leveraging the oracle to make liquidity management more capital efficient, by automatically moving sUSDS/USDS order book liquidity according to the conversion rate.

The oracle provides three sUSDS values in sync:&#x20;

* `ssr`: The per second Sky Savings Rate (compounding rate)
* `chi`: The rate accumulator
* `rho`: The last time chi was updated

These three values enables integrators to extrapolate an exact sUSDS/USDS conversion rate to any point in the future as long as the `ssr` value is not updated on Mainnet. Because this oracle does not need to be synced unless the `ssr` value changes, it uses canonical bridges for maximum security.

The oracle provides convenience functions to fetch the conversion rate at various levels of precision trading off gas efficiency. The specific details are covered in the Functions section below.

## Deployments

### Base

| Contract                | Address                                                                                                               |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------- |
| AuthOracle              | [0x65d946e533748A998B1f0E430803e39A6388f7a1](https://basescan.org/address/0x65d946e533748A998B1f0E430803e39A6388f7a1) |
| Chainlink Rate Provider | [0x026a5B6114431d8F3eF2fA0E1B2EDdDccA9c540E](https://basescan.org/address/0x026a5B6114431d8F3eF2fA0E1B2EDdDccA9c540E) |
| Balancer Rate Provider  | [0x49aF4eE75Ae62C2229bb2486a59Aa1a999f050f0](https://basescan.org/address/0x49aF4eE75Ae62C2229bb2486a59Aa1a999f050f0) |
| Forwarder (Ethereum)    | [0xB2833392527f41262eB0E3C7b47AFbe030ef188E](https://etherscan.io/address/0xB2833392527f41262eB0E3C7b47AFbe030ef188E) |
| Receiver (Base)         | [0x212871A1C235892F86cAB30E937e18c94AEd8474](https://basescan.org/address/0x212871A1C235892F86cAB30E937e18c94AEd8474) |


### Arbitrum
| Contract                | Address                                                                                                               |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------- |
| AuthOracle              | [0xEE2816c1E1eed14d444552654Ed3027abC033A36](https://arbiscan.io/address/0xEE2816c1E1eed14d444552654Ed3027abC033A36) |
| Chainlink Rate Provider | [0x84AB0c8C158A1cD0d215BE2746cCa668B79cc287](https://arbiscan.io/address/0x84AB0c8C158A1cD0d215BE2746cCa668B79cc287) |
| Balancer Rate Provider  | [0xc0737f29b964e6fC8025F16B30f2eA4C2e2d6f22](https://arbiscan.io/address/0xc0737f29b964e6fC8025F16B30f2eA4C2e2d6f22) |
| Forwarder (Ethereum)    | [0x1A229AdbAC83A948226783F2A3257B52006247D5](https://etherscan.io/address/0x1A229AdbAC83A948226783F2A3257B52006247D5) |
| Receiver (Base)         | [0x567214Dc57a2385Abc4a756f523ddF0275305Cbc](https://arbiscan.io/address/0x567214Dc57a2385Abc4a756f523ddF0275305Cbc) |


Check the Spark Address Registry for the most up to date resource for contract deployments:

- [Spark Address Registry](/dev/deployments#spark-address-registry)

## Contracts

* Contract Source: [Github](https://github.com/marsfoundation/xchain-ssr-oracle/)

### SSROracleBase

Contains common functionality shared between the Ethereum mainnet and cross-chain instances of the oracle. Contains convenience functions to fetch the conversion rate at various levels of precision trading off gas efficiency. sUSDS data is compressed into a single word to save SLOAD gas cost.

### SSRAuthOracle

Ensures the oracle receives data from an authorized data provider. This is intended to be one or more bridges which publish data to the oracle. Application-level sanity checks are included when new data is proposed to minimize damage in the event of a bridge being compromised. These sanity checks also enforce event ordering in case messages are relayed out of order. `maxSSR` is used as an upper bound for sanity checks to prevent malicious data from being proposed.

### Rate Providers
Rate Provider contracts take data from the AuthOracle and formats it for specific purposes and integrations. For example The Chainlink Rate Provider provides an up-to-date SSR conversion price in Chainlink format, enabling existing integrators of Chainlink oracles to easily consume this data.

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

* [Cross-chain USDS & sUSDS](/dev/savings/cross-chain-usds-and-susds)
* [Spark PSM](/dev/savings/spark-psm)
* [Sky Savings Rate Mechanism](https://github.com/makerdao/developerguides/blob/master/mcd/intro-rate-mechanism/intro-rate-mechanism.md#dai-savings-rate)

