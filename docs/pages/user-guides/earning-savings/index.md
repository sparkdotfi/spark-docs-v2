---
description: Learn how to earn savings on your stablecoin holdings.
---

# Earning Savings

Spark enables users to easily deposit stablecoins into Savings Vaults, and receive Savings Tokens, representing your share of deposits in the Savings Vaults. As savings accrue, Savings Tokens increases in value over time against the underlying deposit asset.

:::info
**Note:** sUSDS, sDAI, the Sky Savings Rate and DAI Savings Rate are non-custodial and permissionless smart contracts offered by Sky, and is not issued by Spark. Spark never has custody of funds deposited into savings or any control over sUSDS, sDAI, the Sky Savings Rate and DAI Savings Rate.
:::

## Savings Vaults
Spark currently supports the following Savings Vaults:

- **Savings USDS**
    - The Savings USDS vault deposits user deposits of USDS into the Sky Savings Rate.
    - [You can read more about sUSDS here.](/user-guides/earning-savings/susds)

- **Savings USDC**
    - The Savings USDC vault deposits user deposits of USDC into the Sky Savings Rate.
    - [You can read more about sUSDC here.](/user-guides/earning-savings/susdc)

- **Savings DAI**
    - The Savings DAI vault deposits user deposits of DAI into the DAI Savings Rate.
    - [You can read more about sDAI here.](/user-guides/earning-savings/sdai)


## Tutorial

### Deposit Savings

1. Make sure you are connected to the network you wish to use.
2. To earn yield on your stablecoins such as USDS, USDC, and DAI navigate to the **Savings** page, which is the front page of [app.spark.fi](https://spark.fi).

![](/assets/savings-1.png)
*Savings Page*

3. To the left, you can see which Savings Vaults are available. To see more info or to deposit, you can click on the different Vaults. In this example we will use the USDS vault.

![](/assets/savings-vaults.png)
*Savings Vaults*

4. Below the general info it shows the current and historical Savings Rate (SSR) for the selected vault.

![](/assets/savings-apy.png)
*Savings Rate*

5. To deposit, for the selected vault, click on the Deposit button. You can also navigate to the **Supported stablecoins** section, which displays the stablecoin holdings in your wallet, and click on the deposit button for the asset you wish to deposit. Note that different Savings Vaults will support different stablecoins.

6.  In the deposit window you specify the stablecoin (dropdown) and amount (input) you wish to deposit.

    In the Transaction Overview it will show the APY, the route (if not using USDS, how tokens are swapped, before being deposited), and the final outcome of the deposit.
    To finalize the deposit you must execute the transactions in the **Actions** section.

![](/assets/savings-2.png)
*Depositing USDS, and receiving sUSDS*

**Note:** If you deposit other stablecoins than USDS, they will be swapped for USDS before being deposited into Savings. The swap route is shown in the Transaction Overview. This swap uses non-custodial Sky smart contracts, and is not facilitated or in any way custodied by Spark.

The following example showcases a USDC deposit:

![](/assets/savings-3.png)
*Depositing USDC into Savings*

7. Once you have done all the necessary transactions, the specified amount of assets will be deposited and you will receive Savings USDS (sUSDS) tokens in return.

![](/assets/savings-4.png)
*Confirmation Savings Deposit*

8. The sUSDS tokens represents your share of USDS deposited the Sky Savings Rate. You need the sUSDS tokens to withdraw accrued savings in the future, so keep the tokens safe.

9. After your deposit, you will see your Savings grow in real time. You can also see your projected earnings in the My Earnings section.

![](/assets/savings-earnings.png)
*My Earnings*

### Withdraw Savings

1.  When you wish to withdraw accrued savings, you simply click on the withdraw button in the Savings USDS window. In the withdraw window you specify the asset and amount you wish to withdraw. To finalize the withdrawal you must execute the transactions in the **Actions** section.


![](/assets/savings-5.png)
*Withdraw from Savings*

![](/assets/savings-6.png)
*Withdraw from Savings*

**Note:** If you withdraw USDC from Savings, USDS will be swapped for USDC using the Sky PSM after being withdrawn from Savings. The Sky PSM does not incur any slippage or fee beyond gas. The swap route is shown in the Transaction Overview. This swap is possible as long as there is liquidity in the Sky PSM. This swap uses non-custodial Sky smart contracts, and is not facilitated or in any way custodied by Spark.

The following example showcases a USDC withdrawal:

![](/assets/savings-7.png)
*USDC withdrawal from Savings*

2. Once you have done all the necessary transactions, the specified amount of USDS will be transferred to your wallet in exchange for sUSDS tokens.

![](/assets/savings-8.png)
*Confirmation: Withdrawal from Savings*