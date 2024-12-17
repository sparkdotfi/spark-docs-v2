---
description: Learn how to borrow non Dai assets, and how to use E-mode.
---

# Borrowing Assets

## Tutorial

In order to borrow assets, you must first deposit assets as collateral. [Click here](/user-guides/using-sparklend/depositing-assets) for a step by step deposit guide.

If you wish to borrow USDS or Dai you can use the [**Borrow DAI or USDS**](/user-guides/using-sparklend/borrow-dai-and-usds) page.

1.  To borrow assets navigate to the **My portfolio** page and scroll down to the **Borrow** section.

![](/assets/deposit-2.png)
*My Portfolio*

![](/assets/deposit-9.png)
*Borrow Section*


2. The **Borrow** section shows the following information:
   * The assets that can be borrowed
   * The available liquidity that can be borrowed
   * Your current borrow amount
   * The current borrow interest rate for the specific asset

3.  If you are borrowing an asset that is correlated with the deposited collateral type, you can activate the **E-Mode** **toggle** to increase the borrow amount.
    
![](/assets/e-mode.png)
    
This is available between ETH correlated assets (ETH, wsETH, rETH) and stablecoin correlated assets (DAI, USDC, USDT), and allows for increased leverage. For example, you can enable E-mode if you are borrowing ETH using wstETH as collateral. If you are borrowing assets not supported in E-mode, you cannot enable E-mode. For example, if you have already borrowed Dai against ETH, you cannot enable E-mode until this loan has been repaid. [You can read more about E-mode here.](/user-guides/using-sparklend/e-mode)


![](/assets/e-mode-eth.png)
*E-mode Categories*


4. You can borrow an asset by navigating to the asset row, and clicking **Borrow**.

5.  In the **Borrow window** you specify the amount you wish to borrow. In the **Transaction overview** it will display the Health Factor of the borrow position. The **Actions** section will guide you through the steps to create the borrow position.


![](/assets/borrow-weth.png)
*Borrow Window: WETH*


6.  Once you have done all the necessary transactions, you will receive the borrowed assets. Your overall position will be updated, which is reflected in the **Health Factor** and overview in **Your position**.

![](/assets/borrow-weth-done.png)
*Confirmation: Borrowing WETH*


7. If you wish to borrow more at a later stage, you simply repeat this process.

## FAQ

### Why would I borrow instead of selling my assets?

By borrowing you are able to obtain liquidity without selling your assets. Users are mainly borrowing to leverage their holdings or for new investment opportunities.

### How much I can borrow?

The maximum amount you can borrow depends on the value of the collateral you have deposited and the available liquidity. For example, you cannot borrow an asset if there is not enough liquidity or if your health factor does not allow you to.

### What asset do I need to repay?

You repay your loan in the same asset you borrowed. For example, if you borrow 1000 DAI you will pay back 1000 DAI + interest accrued.

### What is the difference between transparent and variable rate?

Transparent rates act as a fixed rate in the short-term, but will change based on Sky Governance. The variable rate is the rate based on the supply and demand in SparkLend, and will constantly change.

### How much will I pay in interest?

The interest rate you pay for borrowing assets depends on the borrowing rate which is derived from the supply and demand ratio of the asset in the case of the variable rate. For transparent rate assets (DAI), the borrowing rate is defined by Sky Governance. The interest rate of a variable rate changes constantly. You can find your current borrowing rate at any time in the Borrow section of your Dashboard.

### What is the health factor?

The health factor is the ratio of your collateralization ratio (the value of your collateral vs the value of your debt) and the liquidation loan to value. The higher Health Factor value is, the safer the state of your funds are against a liquidation scenario. If the health factor goes below 1, a liquidation of your collateral deposits will be triggered.

### What happens when my health factor is reduced?

Depending on the value fluctuation of your collateral deposits, the health factor will increase or decrease. If your health factor increases, it will improve your borrow position by making the liquidation threshold more unlikely to be reached. In the case that the value of your collateral assets against the borrowed assets decreases, the health factor is reduced, causing the risk of liquidation to increase.

### When do I need to pay back the loan?

There is no fixed time period to pay back the loan. As long as your position is safe, you can borrow for an undefined period. However, as time passes, the accrued interest will grow making your health factor decrease, which might result in your deposited assets becoming more likely to be liquidated.

### How do I payback the loan?

In order to payback the loan you simply go to the Borrowings section of your dashboard and click on the repay button for the asset you borrowed and want to repay. Select the amount to pay back and confirm the transaction.

### How do I avoid liquidation?

In order to avoid the reduction of your health factor leading to liquidation, you can repay the loan or deposit more collateral assets in order to increase your health factor. Learn more about liquidations here:

- [Liquidations](/user-guides/using-sparklend/liquidations)

### How can I use permit?

The permit function of SparkLend allows you to move your funds from a wallet by simply signing an approval message instead of approving a transaction on the network to avoid gas fees.
