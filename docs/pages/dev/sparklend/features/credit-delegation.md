# Credit Delegation

Credit delegation allows a depositor to deposit funds in the protocol to earn interest, and delegate borrowing power (i.e. their credit) to other users. The enforcement of the loan and its terms are agreed upon between the depositor and borrowers, which can be either off-chain via legal agreements or on-chain via smart contracts.

This enables:

* The supplier (aka delegator) to earn extra yield on top of the yield they already earn from the protocol,
* The borrowers (aka delegatees) to access an uncollateralized loan.

:::warning
Borrow by _delegatee_ must be consistent with _delegator_ [eMode](/dev/sparklend/features/efficiency-mode-emode) category.\
For eg. if a delegator eMode category is `STABLECOINS`, then

* delegator can only borrow `STABLECOINS` eMode category asset.
* in case _delegator_ approve credit to _delegatee_ for non `STABLECOINS`category (for eg. weth), then borrow would revert.
:::

:::danger
The _delegatee_ cannot abuse credit approval to liquidate _delegator_ i.e. if the borrow puts _delegator's_ position in HF < `HEALTH_FACTOR_LIQUIDATION_THRESHOLD`, then borrow will fail.
:::

## Approving the delegation

The [`approveDelegation()`](/dev/sparklend/tokens/debttoken#approvedelegation) or [`delegationWithSig()`](/dev/sparklend/tokens/debttoken#delegationwithsig) must be called by the supplier (delegator), approving the borrower (delegatee) a certain amount.

This is done for each debt token that needs to be delegated.

:::info
The delegator does not need to already have supplied funds in the protocol to `approveDelegation()`. However, **before** the delegatee executes `borrow()`, there must be sufficient collateral supplied by delegator in the protocol.
:::

## Borrowing the credit

The borrower (delegatee) calls the [`borrow()`](/dev/sparklend/core-contracts/pool#borrow) method on the `Pool`, using the supplier's (delegator's) address in final parameter `onBehalfOf`.

The borrower's available credit is reduced by the borrowed amount.

## Repaying the credit

Anyone can repay the debt _OnBehalf_ of the user, by calling one of the methods - [repay()](/dev/sparklend/core-contracts/pool#repay) or [repayWithPermit()](/dev/sparklend/core-contracts/pool#repaywithpermit). The supplier (aka creditor) can also use [repayWithSpTokens()](/dev/sparklend/core-contracts/pool#repaywithsptokens) method to repay debt with their _spTokens_ of the underlying debt asset in the same pool.
