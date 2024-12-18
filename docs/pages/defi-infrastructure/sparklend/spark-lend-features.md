# SparkLend Modes

## Isolation Mode
Isolation mode allows Sky Governance to list new assets as isolated assets, which have a specific debt ceiling and can only be used as the sole collateral for a position. Wrapped Ether.fi ETH (weETH) is an example of an isolated asset in SparkLend.

The debt ceiling for an isolated asset is represented as the maximum amount in USD that can be borrowed against the user’s collateral.

### How can I enter isolation mode?

The steps to entering isolation mode are as follows:

1. From the My portfolio page select an isolated asset to Deposit.
2. You will then see an information notification explaining that you are entering into isolation mode.
3. Once you have successfully entered isolation mode, you will then be able to deposit an isolated asset.
4. You can also borrow assets once in isolation mode; however, you will only be able to borrow stablecoins up to a certain debt ceiling.

### How can I exit isolation mode?

To exit isolation mode, you will need to disable the collateralized isolated asset that you have supplied.

1. On the **My portfolio** page in the **Deposit** section, click the **Collateral** toggle to disable the isolated asset.
2. Confirm the disabled isolation mode setting. You have now successfully exited isolation mode.

## High Efficiency Mode (E-mode)

The E-mode feature maximizes capital efficiency when collateral and borrowed assets have correlated prices. For example, sDAI, USDC, USDT are all stablecoins pegged to USD. These stablecoins are all within the same E-mode category. Accordingly, a user supplying sDAI in E-mode will have higher collateralization power when borrowing assets like USDC or USDT.

Only assets of the same category (for example stablecoins) can be borrowed in E-mode.

E-mode does not restrict the usage of other assets as collateral. Assets outside of the E-mode category can still be supplied as collateral with normal LTV and liquidation parameters.

### How do I enter E-mode?

To enter E-mode from the go to **My portfolio** and find the **Borrow** section. Here you will find an **E-Mode Toggle**, which you can click.

![](/assets/e-mode.png)

You can then select which E-mode category you wish to choose.

![](/assets/e-mode-eth.png)
*Selection of E-Mode Category*

You then submit the transactions in the **Actions** section to enable E-Mode.

### How do I exit E-mode?

To exit E-mode, go to the **My portfolio** page and navigate to the **Borrow** section. Click on the E-Mode toggle and select No E-mode in the popup window. Carry out the transactions in the **Actions** section to exit E-mode.

### How does E-mode affect my borrowing power?

When E-mode is enabled, you will have higher borrowing power over assets of the same E-mode category.