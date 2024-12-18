---
description: Learn how to deposit assets as collateral and to earn interest.
---

# Depositing Assets

## Tutorial

In order to borrow assets, you must first deposit assets as collateral such as ETH or cbBTC. Deposited assets can be borrowed by other users and therefore earns interest. You can also simply deposit assets without borrowing, to earn interest.

1.  To deposit assets into Spark, navigate to the **My portfolio** page.

![](/assets/deposit-1.png)
*Navigate to My portfolio*

![](/assets/deposit-2.png)
*My Portfolio Page*


2.  Scroll down to the **Deposit** section which shows the following information:

    * **Assets:** The different assets that can be deposited into Spark
    * **In Wallet:** Amount of the specific asset in your wallet, and its value in USD.
    * **Deposit**: Amount of the asset you have deposited into Spark.
    * **APY:** The current annual percentage yield. Deposited assets can be borrowed by other users, and therefore earns yield.

![](/assets/deposit-3.png)
*Deposit Section*


3. You deposit assets by clicking on the Deposit button for the corresponding asset, which will open the **Deposit window**.

4. The **Deposit window** will display:
   * **Amount:** Here you specify the amount of the specific asset you wish to deposit.
   * **Transaction overview:** Shows the supply APY for the asset and whether the asset is enabled as collateral.
   *   **Actions**: An overview of the necessary transactions you must do to create the deposit.


![](/assets/deposit-4.png)
*Deposit Window*


5.  Once you deposit assets, the position will be updated, which is reflected in the Health Factor and overview in **Your position**.


![](/assets/deposit-5.png)
*Health Factor and Your Position Overview*


6. You receive spTokens in return which reflect your deposit in Spark. You need these tokens to withdraw your assets from the protocol, so keep them in your wallet.

7. If you wish to deposit more assets, for example to increase the *Health Factor* of your borrow position, you simply repeat this process.

8.  You can use the **Collateral toggle** to enable or disable an asset as collateral for your borrow position. Disabling an already supplied asset as collateral will impact the Health Factor of your position, as the asset will no longer count towards the collateral value and loan to value.


![](/assets/deposit-6.png)
*Collateral Toggle: The toggle is green when the asset is enabled as collateral*

![](/assets/deposit-7.png)
*Disabling an asset at collateral*

## FAQ

### Is there a minimum or maximum deposit amount?

You can deposit any amount you want, there is no minimum or maximum limit. However, it's important to note that for low amounts it is possible that the transaction cost of the process is higher than the expected earnings. It is recommended that you consider this when depositing low amounts.

### Where are my deposited funds stored?

Funds are deposited in a non-custodial smart contract. The code of the smart contract is public, open source, formally verified and audited by third party auditors. No centralized entity can access deposited funds.

### How much will I earn?

Depositors receive continuous yield that fluctuates due to market conditions based on:

* **The interest rate payment on loans:** Depositors share the interests paid by borrowers. The higher the utilization of a reserve the higher the yield for depositors.

Each asset has its own market of supply and demand with its own APY (Annual Percentage Yield) which fluctuates over time. You can find the average annual rate over the past 30 days to evaluate the rate evolution, and you can also find more data on the reserve overview of each asset in the home section on the app.

### Can I opt-out my asset from being used as a collateral?

Yes. After depositing your assets, you are able to unselect the asset so that it will not be used as collateral. The opt-out is available in the **Deposit** section within your dashboard. Simply switch the **Collateral** toggle on the asset you would prefer to opt-out from being used as a collateral.

You can withdraw your assets without opting out of using them as collateral, as long as those funds are not actively being lent out or the withdrawal would cause a liquidation on your loans.

[^1]: The **Health Factor** is a measure of how close the position is to liquidation based on the current LTV. A Health Factor **below 1** means the position can be liquidated. Users are therefore responsible for keeping a Health Factor above 1, in order to avoid liquidation. The LTV of the position can change over time if the underlying collateral changes in value, and as debt accrues due to interest rates.
