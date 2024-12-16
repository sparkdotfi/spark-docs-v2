---
description: Learn how to find details on the supported lending markets on Spark.
---

# Overview of Markets

The **Markets** page displays an overview of the state of the protocol and the supported assets. The displayed data is specific to the selected network, so if you wish to browse another network, use the network toggle in the top right hand corner.

<figure><img src="../../.gitbook/assets/markets-nav.png" alt=""><figcaption><p>Navigate to Markets Page</p></figcaption></figure>

The Markets page displays:

* The total market size
* Total value locked (TVL)
* Total available liquidity that can be borrowed
* Total borrow amount

<figure><img src="../../.gitbook/assets/markets.png" alt=""><figcaption><p>The Markets Page</p></figcaption></figure>

In the section below it displays the following data for each supported asset:

* Total amount supplied
* Deposit APY
* Total amount borrowed
* Borrow APY
* Status, which indicates certain risk modes for the assets:
  * Can it be supplied or not
  * Can it be used as collateral or not
  * Can it be borrowed or not, or is it in isolation mode ([read more here](spark-lend-features.md)).

<figure><img src="../../.gitbook/assets/markets-2.png" alt=""><figcaption><p>Market Status: Specific for each asset</p></figcaption></figure>

For each asset you can click on the details button to get a more in-depth overview of the metrics for the asset, and its parameters, such as liquidation threshold and penalty, and whether the asset can be used in E-mode. The page also displays which oracle is being used for this asset ([you can read more about this here](oracles.md)). It also displays a more in-depth overview of the interest rate model for the asset. You are also able to deposit or borrow the asset directly from this page, using the sidebar on the right.

<figure><img src="../../.gitbook/assets/markets-3.png" alt=""><figcaption><p>Detailed Asset Overview</p></figcaption></figure>
