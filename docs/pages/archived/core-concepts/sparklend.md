---
description: Learn about the core concepts behind SparkLend.
hidden: true
---

# SparkLend

SparkLend is a decentralized non-custodial liquidity protocol where users can participate as depositors, borrowers or liquidators. Depositors provide liquidity to a market and can earn interest on the crypto assets provided, while borrowers are able to borrow in an overcollateralized fashion.

## Capital Efficiency

We allow users to optimise their assets supplied to the SparkLend in terms of yield generation and borrowing power.

### Efficiency Mode (E-Mode)

The High Efficiency Mode or _**E-Mode**_ allows borrowers to extract the highest borrowing power out of their collateral when supplied and borrowed assets are correlated in price, particularly when both are derivatives of the same underlying asset (e.g. stablecoins pegged to USD).

This can enable a wave of new use cases such as High leverage forex trading, Highly efficient yield farming (for example, deposit ETH staking derivatives to borrow ETH), Diversified risk management&#x20;

### Isolation Mode

New assets can be listed as _**isolated**_. Borrowers supplying an isolated asset as collateral cannot supply other assets as collateral (though they can still supply to capture yield). Borrowers using an isolated collateral can only borrow stablecoins that have been permitted by Sky Governance to be borrowable in isolation mode, up to a specified debt ceiling.

### Siloed Borrowing

Siloed borrowing allows assets with potentially manipulatable oracles to be listed on Spark as single borrow asset i.e. if a user borrows siloed asset, they cannot borrow any other asset. This helps mitigating the risk associated with such assets from impacting the overall solvency of the protocol.

## Risk Management

SparkLend brings a greatly improved set of risk parameters and new features to protect the protocol from insolvency.

### Supply and Borrow Caps

Sky Governance can now configure Borrow and Supply Caps.

* **Borrow Caps:** allow to modulate how much of each asset can be borrowed, which reduces insolvency risk.
* **Supply Caps:** allow to limit how much of a certain asset is supplied to SparkLend. This helps reducing exposure to a certain asset and mitigate attacks like infinite minting or price oracle manipulation.

### Granular Borrowing Power Control

In SparkLend, it will be possible to lower the borrowing power of any asset to as low as 0% without any impact on existing borrowers (it’s still possible to use the old approach - liquidating existing users - if deemed necessary)

### Risk Admins

SparkLend introduces the ability for the Sky Governance to grant entities permission to update the risk parameters without going through governance vote for every change. These entities can be DAOs or automated agents that can build on top of this feature to react automatically in case of unanticipated events.

{% hint style="info" %}
Sky Governance will have the ability to revoke access to existing Risk Admins or add new Risk Admins.
{% endhint %}

### Price Oracle Sentinel

The Sentinel feature introduces a grace period for liquidations and disables borrowing under specific circumstances.

This feature has been specifically designed for L2s to handle eventual downtime of the sequencer (but can be extended to handle other cases, even on L1s, in the future).

### Variable Liquidation Close Factor

The liquidation mechanism has been improved to allow the position to be fully liquidated when it approaches insolvency i.e. _HF < 0.95_ (previously only half of the position could be liquidated at any point).

## Decentralisation

SparkLend introduces a new system role - `ASSET_LISTING_ADMIN_ROLE` - that can be granted by the Maker Governance to allow admins to create and set custom asset listing strategies for each asset listing.

## Spark Interface

The Spark interface is hosted on [IPFS](https://ipfs.tech/) in a decentralized manner. Spark maps the following DNS names to the Cloudflare IPFS gateway:

* [https://app.spark.fi](https://app.spark.fi) will always point to the latest main IPFS hash

### IPFS Troubleshooting

If the Cloudflare gateway is not working and you are unable to connect to [app.spark.fi](https://app.spark.fi), you can use any public or private IPFS gateway supporting origin isolation to access the Spark interface:

* Go to `<your favorite public ipfs gateway>/ipns/app.spark.fi`
* Make sure the gateway supports origin isolation to avoid possible security issues
* You should be redirected to a URL that looks like `https://app-spark.fi.<your gateway>`

### Previous Links

The following links have worked previously:

* https://app-spark.fi.ipns.cf-ipfs.com/#/
* https://app-spark.fi.ipns.dweb.link/#/
