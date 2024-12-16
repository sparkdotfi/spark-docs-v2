---
description: Learn how to use the Easy Borrow Flow to borrow USDS or DAI.
---

# Borrow DAI and USDS

{% hint style="warning" %}
**Note:** When borrowing USDS, you are actually borrowing DAI which is then upgraded to USDS in the same transaction. This means that your debt is in DAI and must be repaid using DAI. To payback DAI, you can downgrade USDS to DAI on the Savings page. [Find more info here.](../upgrading-to-usds-and-susds/)
{% endhint %}

## Tutorial

On the **Borrow DAI and USDS** page, you can borrow USDS and DAI, by depositing crypto assets as collateral. If you wish to borrow other assets than USDS or DAI, navigate to the **My portfolio** page and follow the [deposit assets](depositing-assets.md) and [borrowing assets](borrowing-assets.md) steps instead.

1.  Navigate to the **Borrow DAI and USDS** page.\


    <figure><img src="../../.gitbook/assets/borrow-1.png" alt=""><figcaption><p>Navigating to Borrow DAI and USDS</p></figcaption></figure>



<figure><img src="../../.gitbook/assets/borrow-2.png" alt=""><figcaption><p>The Borrow DAI or USDS page</p></figcaption></figure>

2. Under **Deposit** you can select the crypto asset in the dropdown menu you wish to deposit as collateral for the loan.

<figure><img src="../../.gitbook/assets/borrow-3.png" alt=""><figcaption><p>Easy Borrow Flow</p></figcaption></figure>

3. In the input bar on the left you specify the amount of collateral you wish to deposit, denominated in the asset. The dollar value is displayed below.
4. On the right under Borrow, using the dropdown menu you can specify the asset you wish to borrow.

<figure><img src="../../.gitbook/assets/borrow-5.png" alt=""><figcaption><p>Selection of which asset to borrow.</p></figcaption></figure>

5. Click on **Add more +** to add more crypto assets to be used as collateral. This will generate an additional deposit bar, where you can select the asset and amount.

<figure><img src="../../.gitbook/assets/borrow-4.png" alt=""><figcaption><p>Deposit multiple collateral assets</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/borrow-6.png" alt=""><figcaption><p>Depositing multiple collateral assets</p></figcaption></figure>

6. On the right side under **Borrow**, you specify the DAI or USDS amount you wish to borrow.
7. Below you are able to see the simulated state of the borrow position based on the current price of the collateral assets and the borrow amount. It displays:

* **Loan to Value (LTV):** The percentage value of the borrow amount in USD in respect to the collateral amount in USD.
* **The LTV slider:** Shows the current LTV percentage and its associated risk level ranging from Conservative to Moderate to Aggressive. You can drag the slider to adjust the borrow amount to specify an LTV percentage, which will adjust the Dai borrow amount above accordingly.
* **Liquidation Indicator**: The LTV slider also shows the LTV at which the position can be liquidated. The different collateral assets have a different liquidation LTV. Creating a position with multiple collateral assets will use an aggregate liquidation LTV based on the amount of each collateral.
* **Max LTV:** The maximum allowed percentage value of the borrow amount in USD in respect to the collateral amount in USD.
* **Borrow rate:** The annual percentage rate (APR) for borrowing. For USDS and DAI, this rate is set by Sky Governance.

{% hint style="warning" %}
**Note:** Crypto assets are volatile so even conservative borrow positions should be monitored on an ongoing basis to prevent unwanted liquidations. [You can read more about liquidations here.](liquidations.md)
{% endhint %}

8. Once the parameters for the borrow position has been set, you click **Borrow**.\

9.  This will showcase the [Health Factor](#user-content-fn-1)[^1], the [liquidation pric](#user-content-fn-2)[^2]e and the [current collateral pricing](#user-content-fn-3)[^3] for the position.\


    <figure><img src="../../.gitbook/assets/borrow-7.png" alt=""><figcaption><p>The Health Factor Overview</p></figcaption></figure>

    * The **Health Factor** is a measure of how close the position is to liquidation based on the current LTV. A Health Factor **below 1** means the position can be liquidated. Users are responsible for keeping a Health Factor above 1, in order to avoid liquidation. The LTV of the position can change over time if the underlying collateral changes in value, and as debt accrues due to interest rates.
    * **Current Price** shows the current market price of the collateral asset provided by the price oracle.
    * If the price of the collateral asset reaches the **Liquidation Price**, the position can be liquidated.

    **Note:** If you are using more than one collateral type, the current price and liquidation price information is not displayed.\

10. The **Actions** section below shows the transactions necessary to create the borrow position. You must click the buttons to sign each transactions with the connected wallet.\


    <figure><img src="../../.gitbook/assets/borrow-8.png" alt=""><figcaption><p>Actions Window</p></figcaption></figure>

    * **Token Permit/Approval:** You must approve the deposit of the collateral token.
    * **Deposit:** You deposit the collateral tokens into the borrow position.
    * **Borrow:** You borrow the specified amount of assets.\

11. Once every step is done, you will have received the borrowed Dai in your wallet, and a confirmation and overview of the actions. You can click on **View in dashboard** to view your new position.\


    <figure><img src="../../.gitbook/assets/borrow-9.png" alt=""><figcaption><p>Confirmation Window</p></figcaption></figure>

## FAQ

You can find frequently asked questions relating to collateral deposits and borrowing here:

* [**Depositing Assets FAQ**](depositing-assets.md#faq)
* [**Borrowing Assets FAQ**](borrowing-assets.md#faq)

[^1]: The **Health Factor** is a measure of how close the position is to liquidation based on the current LTV. A Health Factor **below 1** means the position can be liquidated. Users are responsible for keeping a Health Factor above 1, in order to avoid liquidation. The LTV of the position can change over time if the underlying collateral changes in value, and as debt accrues due to interest rates.

[^2]: If the price of the collateral asset reaches the **Liquidation Price**, the position can be liquidated.

[^3]: **Current Price** shows the current market price of the collateral asset provided by the price oracle.
