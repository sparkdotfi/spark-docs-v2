---
description: >-
  Learn how to monitor and adjust your position to avoid liquidations in
  changing markets.
---

# Adjusting Your Position

## Tutorial

Having an active borrow position on Spark requires ongoing monitoring and management. These steps will guide you through how to effectively manage your position and to avoid liquidation.

1.  To monitor your Spark position, navigate to the **My portfolio** page.


    ![](/assets/deposit-2.png)
    *The Dashboard*


2.  The section **Your position** will show:

    * The value of the deposited collateral in USD
    * The value of the borrowed funds in USD. This accrues over time based on the borrow rate.
    * The maximum that can be borrowed, before violating the Loan-To-Value requirements.

    **Note:** If you do not have an active position, it will show an empty position, and a button below to create one using the **Easy Borrow Flow**.


    ![](/assets/deposit-5.png)
    *Your Position: Shows collateral value, loan value, and the max borrow amount*


3.  The **Dashboard** also displays the current Health Factor of the borrow position.

    * The **Health Factor** is a measure of how close the position is to liquidation based on the current LTV. A Health Factor **below 1** means the position can be liquidated. Users are therefore responsible for keeping a Health Factor above 1, in order to avoid liquidation. The LTV of the position can change over time if the underlying collateral changes in value, and as debt accrues due to interest rates.
    * **Current Price** shows the current market price of the collateral asset.
    * If the price of the collateral asset reaches the **Liquidation Price**, the position can be liquidated.

    **Note:** If you are using more than one collateral type, the current price and liquidation price information is not displayed.


    ![](/assets/deposit-8.png)
    *The Health Factor for your Spark position*


4.  On the **My portfolio page** you have the necessary functionality to adjust your position.

    *   In the **Deposit** section you can deposit and withdraw assets. [See the steps here](/user-guides/using-sparklend/depositing-assets).

    ![](/assets/deposit-3.png)
    *Deposit Section*

    * In the **Deposit** section you can also enable or disable assets as collateral. Learn about this here.
    *   In the **Borrow** section you can borrow or repay assets. [See the steps here](b/user-guides/using-sparklend/borrowing-assets).


    ![](/assets/deposit-9.png)
    *Borrow Section*


    For example, if your position is close to liquidation you can either repay some of fully your loan, or deposit more collateral. See the [deposit assets](/user-guides/using-sparklend/depositing-assets) and [borrow asset](/user-guides/using-sparklend/borrowing-assets) sections for the step by step guide.

5. If your position is liquidated, your position will be updated accordingly and automatically. Depending on the exact situation for the liquidation you might still have an open borrow position. [You can read more about liquidations here](/user-guides/using-sparklend/liquidations).

## FAQ

Find relevant FAQs here:

* [**Depositing Assets FAQ**](/user-guides/using-sparklend/depositing-assets#faq)
* [**Borrowing Assets FAQ**](/user-guides/using-sparklend/borrowing-assets#faq)
