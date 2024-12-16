# Liquidations

## What is a liquidation?

A liquidation is a process that occurs when a borrower's [Health Factor](borrowing-assets.md#what-is-the-health-factor) (HF) goes below 1 due to their collateral value not properly covering their loan/debt value. This might happen when the collateral decreases in value or the borrowed debt increases in value. In a liquidation up to 100 % (depending on your HF - [see below](liquidations.md#variable-liquidation-close-factor)) of a borrower's debt is covered by seizing the collateral and selling it to repay the debt.

### Variable Liquidation Close Factor

The variable liquidation close factor will based on the Health Factor (HF) allow for partial of full liquidation of the borrow position. If the HF is <1, but >0.95, 50 % of the position collateral can be liquidated. However if the HF is < 0.95 100 % of the collateral can be liquidated.

## How much is the liquidation penalty?

The liquidation penalty (or bonus for liquidators) depends on the asset used as collateral. The liquidation penalty for each individual asset can be found on the [Markets page](overview-of-markets.md).

## How can I avoid getting liquidated?

It's important to monitor your health factor to avoid a liquidation. Keeping your health factor over 2, for example, gives you more of a margin to avoid a liquidation.

To avoid liquidation you can raise your health factor by depositing more collateral assets or repaying part of your loan.&#x20;

## Can I participate in the liquidations ecosystem?

Yes, liquidations are open to anyone. Liquidators develop solutions and bots to be the first ones liquidating loans to get the liquidation bonus. You can find more details in the [developers liquidation section](https://devs.spark.fi/sparklend/features/liquidations).
