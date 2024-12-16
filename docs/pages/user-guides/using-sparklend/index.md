---
description: Learn more about how SparkLend works and how to use it.
---

# Using SparkLend

## What is SparkLend?

SparkLend is a decentralized non-custodial liquidity market protocol where users can participate as lenders or borrowers. Lenders provide liquidity to the market to earn a passive income, as their assets are lent out, while borrowers are able to borrow in an overcollateralized and perpetual fashion.

## How do I interact with SparkLend?

Get started using SparkLend using this guide:

{% content-ref url="borrow-dai-and-usds.md" %}
[borrow-dai-and-usds.md](borrow-dai-and-usds.md)
{% endcontent-ref %}

## What are the risks?

No platform can be considered entirely risk-free. The risks related to the SparkLend platform are the smart contract risk (risk of a bug within the protocol code) and liquidation risk (risk on the collateral liquidation process). Every possible step has been taken to minimize the risk as much as possible, the protocol code is public and open source and it has been audited. Additionally, you can find additional security-related information in the [security and audits](https://devs.spark.fi/security-and-audits) sections.

## Feature Overview

### Lending and Borrowing

On SparkLend, users are able to deposit assets into liquidity markets where they can be borrowed by other users. This enables depositors to earn interest on their deposits. Furthermore, can depositors use their deposits as collateral to borrow assets. Borrowers will pay interest to lenders based on the supply and demand of the borrowed asset.

You can lean more about Depositing, Lending and Borrowing here:

{% content-ref url="depositing-assets.md" %}
[depositing-assets.md](depositing-assets.md)
{% endcontent-ref %}

{% content-ref url="borrowing-assets.md" %}
[borrowing-assets.md](borrowing-assets.md)
{% endcontent-ref %}

### Efficiency Mode (E-Mode)

The High Efficiency Mode or _**E-Mode**_ allows borrowers to extract the highest borrowing power out of their collateral when supplied and borrowed assets are correlated in price, particularly when both are derivatives of the same underlying asset (e.g. stablecoins pegged to USD).

This can enabling a wave of new use cases such as High leverage forex trading, Highly efficient yield farming (for example, deposit ETH staking derivatives to borrow ETH), Diversified risk management&#x20;

Learn more about E-Mode here:

{% content-ref url="e-mode.md" %}
[e-mode.md](e-mode.md)
{% endcontent-ref %}

### Isolation Mode

New assets can be listed as _**isolated**_. Borrowers depositing an isolated asset as collateral cannot supply other assets as collateral (though they can still supply to capture yield). Borrowers using an isolated collateral can only borrow up to a specified debt ceiling.

Learn more about Isolation mode here:

{% content-ref url="spark-lend-features.md" %}
[spark-lend-features.md](spark-lend-features.md)
{% endcontent-ref %}

### Siloed Borrowing

Siloed borrowing allows assets with potentially manipulatable oracles to be listed on Spark as single borrow asset i.e. if a user borrows siloed asset, they cannot borrow any other asset. This helps mitigating the risk associated with such assets from impacting the overall solvency of the protocol.

### Open Source

SparkLend is completely open source, which allows anyone to interact with a user interface client, API or directly with the smart contracts on the Ethereum network. Being open source enables any third-party service or application to integrate and interact with the protocol.

You can find all Spark related code here: [https://github.com/marsfoundation](https://github.com/marsfoundation)

## Risk Management

SparkLend brings a greatly improved set risk parameters and features to protect the protocol from insolvency.

### Supply and Borrow Caps

Sky Governance can configure Borrow and Supply Caps.

* **Borrow Caps:** allow to modulate how much of each asset can be borrowed, which reduces insolvency risk.
* **Supply Caps**: allow to limit how much of a certain asset is supplied to SparkLend. This helps reducing exposure to a certain asset and mitigate attacks like infinite minting or price oracle manipulation.

### Granular Borrowing Power Control

In SparkLend, it is possible to lower the borrowing power of any asset to as low as 0% without any impact on existing borrowers (it’s still possible to use the old approach - liquidating existing users - if deemed necessary)

### Risk Admins

SparkLend introduces the ability for the Sky Governance to grant entities permission to update the risk parameters with going through governance vote for every change. These entities can be DAOs or automated agents that can build on top of this feature to react automatically in case of unanticipated events.

{% hint style="info" %}
Sky Governance will have the ability to revoke access to existing Risk Admins or add new Risk Admins.
{% endhint %}

### Price Oracle Sentinel

The Sentinel feature introduces a grace period for liquidations and disables borrowing under specific circumstances.

This feature has been specifically designed for L2s to handle eventual downtime of the sequencer (but can be extended to handle other cases, even on L1s, in the future).

### Variable Liquidation Close Factor

The variable liquidation close factor will based on the Health Factor (HF) allow for partial of full liquidation of the borrow position. If the HF is below 1, but >0.95, 50 % of the position collateral can be liquidated. However if the HF is < 0.95 100 % of the collateral can be liquidated.

You can read more about liquidations here:

{% content-ref url="liquidations.md" %}
[liquidations.md](liquidations.md)
{% endcontent-ref %}
