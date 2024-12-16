---
description: Find security audit reports for Spark products.
---

# Security Audits

## SparkLend

SparkLend is based on the Aave v3 codebase (including 3.0.1 and 3.0.2 upgrades) which has been extensively audited. [You can find the audits of Aave v3 here.](https://aave.com/security)

Notable code differences include:

* The DAI market has a custom interest rate strategy due to its relation with Sky.
* A custom oracle had to be made for the Savings DAI market.
* The `RewardsController` was not set up through the `PoolAddressProvider`.

ChainSecurity completed the audits for the deployment of SparkLend along with audits of the additional code used for the custom interest rate strategy for the DAI market and the Savings DAI oracle. You can read the audit reports here:

{% file src="../.gitbook/assets/Chainsecurity - SparkLend Deployment Verification" %}

{% file src="../.gitbook/assets/Chainsecurity - DAI IR Strategy and sDAI Oracle" %}

## Spark Liquidity Layer

{% file src="../.gitbook/assets/Cantina - Spark Liquidity Layer (2024-09-25).pdf" %}

{% file src="../.gitbook/assets/Cantina - Spark Liquidity Layer (2024-10-23).pdf" %}

{% file src="../.gitbook/assets/Chainsecurity - Spark Liquidity Layer (2024-10-22).pdf" %}

## Savings USDS (sUSDS)

{% file src="../.gitbook/assets/Chainsecurity - sUSDS.pdf" %}

{% file src="../.gitbook/assets/Cantina - sUSDS.pdf" %}

## Savings DAI (sDAI)

{% file src="../.gitbook/assets/Chainsecurity - sDAI" %}
