
## Introduction

This integration guide explains why listing sUSDS instead of USDS on lending markets is beneficial and how to implement this integration efficiently.

## Benefits of Listing sUSDS Over USDS

The key advantage of listing sUSDS over USDS is that it ensures base lending and borrowing rates follow the Sky Savings Rate (SSR) of sUSDS, making markets more capital-efficient. In practice, this means liquidity providers will always earn at least the base rate of sUSDS—the Sky Savings Rate—even without any borrowing activity.

This is not the case with USDS, where markets require either sufficient borrowing demand or efficient rate arbitrage to ensure the lending rate matches that of sUSDS. By listing sUSDS, the protocol becomes more capital-efficient for LPs by eliminating the opportunity cost of potentially low rates, as depositors always earn the Sky Savings Rate. This should attract more liquidity to the lending protocol, potentially generating more loans and ultimately more fees.

Conversely, listing sUSDS also guarantees a minimum borrow rate equal to the SSR. This reduces the need for rate arbitrage across lending markets by mitigating market inefficiencies.

From a user experience perspective, sUSDS usage can be completely abstracted away, as USDS and sUSDS can be freely converted without liquidity constraints or fees. The result is a lending market that appears to be a standard USDS market but with guaranteed lending and borrowing base rates equal to the SSR.


## How Does it Work?

sUSDS is a token that increases in value against USDS according to the Sky Savings Rate. This means the dollar value of sUSDS gradually increases over time. By listing sUSDS in a lending market, depositors earn this rate as their sUSDS becomes more valuable, in addition to the interest earned (which is also in sUSDS).

Similarly, when borrowing sUSDS, both the interest and the principal debt amount increase in value over time according to the Sky Savings Rate. In other words, it gradually becomes more expensive to acquire the sUSDS tokens needed to repay the debt.

Lending markets should adjust their interest rate mechanisms to account for these "built-in" rates. Read more about this in the Rates section below.

## Improving the User Experience

Since many users are unfamiliar with lending and borrowing a yield-accumulating token, it makes sense in some cases to abstract away this complexity.

As mentioned earlier, sUSDS usage can be abstracted to appear as a normal USDS lending market with guaranteed base rates equal to the SSR. This is possible because USDS and sUSDS can be freely and instantly converted without fees, slippage, or liquidity constraints. A user could deposit USDS, and the lending protocol would convert it to sUSDS before depositing it into the lending market. The protocol would then display converted balances and rates for USDS. When users borrow USDS, the protocol would withdraw sUSDS and convert it to USDS before sending it to the user. From the end user's perspective, this would function like a standard USDS lending market. The sections below explain how this can be implemented.

## Integrating sUSDS Into a Lending Market

The following sections explore how sUSDS can be listed from a technical perspective. There are two options: listing sUSDS directly, or listing sUSDS while abstracting it as a USDS lending market.

sUSDS is an ERC4626 token with USDS as its base asset. sUSDS increases in value against USDS over time. It's an accumulating token, not a rebasing token, as yield accumulates in its value rather than through an increasing supply.

sUSDS can be integrated like any other token as it is ERC20 compliant.

You can find more documentation on sUSDS here:

- [sUSDS Developer Documentation](/dev/savings/susds-token)

### Price Feed

For markets to list an asset, they typically need a price feed to calculate user collateral value, borrow limits, and trigger liquidations.

The sUSDS token contract on Ethereum mainnet contains a conversion rate [`chi`](https://etherscan.io/token/0xa3931d71877C0E7a3148CB7Eb4463524FEc27fbD#readProxyContract#F7) which increases over time according to the Sky Savings Rate (SSR). `chi` is essentially the price of sUSDS in USDS and is a 27-decimal number.

On networks other than Ethereum mainnet, sUSDS is not an ERC4626 token and doesn't contain the `chi` variable. Instead, the `chi` value can be fetched from the [SSR Oracle here](https://basescan.org/address/0x65d946e533748A998B1f0E430803e39A6388f7a1#readContract#F4) (in this example Base). You can read more about the SSR Oracle here.

- [SSR Oracle Developer Documentation](/dev/savings/cross-chain-savings-rate-oracle)

The protocol can leverage a USDS/USD oracle price to calculate the sUSDS/USD price by multiplying the two together:

`sUSDS_price = USDS_price * chi / ray`

Where `ray = 10^27`

We divide by ray because `chi` is a 27-decimal number.

Spark uses the following Chainlink-compliant oracle for sUSDS: [https://etherscan.io/address/0x27f3A665c75aFdf43CfbF6B3A859B698f46ef656#readContract](https://etherscan.io/address/0x27f3A665c75aFdf43CfbF6B3A859B698f46ef656#readContract)

**Note:** This oracle uses a fixed 1.00 USD price for USDS. If you wish to use a market price for USDS, you should not use this oracle.

### Conversions

To convert USDS to sUSDS, divide by the `chi` variable, which can be fetched from the [sUSDS contract on Ethereum](https://etherscan.io/token/0xa3931d71877C0E7a3148CB7Eb4463524FEc27fbD#readProxyContract#F7) or from the SSROracle on other networks ([Base Example](https://basescan.org/address/0x65d946e533748A998B1f0E430803e39A6388f7a1#readContract#F4)):

`ray = 10^27`

`sUSDS_amount = USDS_amount * ray / chi`

On Ethereum, the ERC4626 function [`convertToAssets`](https://etherscan.io/token/0xa3931d71877C0E7a3148CB7Eb4463524FEc27fbD#readProxyContract#F8) of sUSDS performs this calculation. It takes an sUSDS amount and returns the USDS amount.

To convert sUSDS to USDS, multiply by `chi`:

`USDS_amount = sUSDS_amount * chi / ray`

On Ethereum, the ERC4626 function [`convertToShares`](https://etherscan.io/token/0xa3931d71877C0E7a3148CB7Eb4463524FEc27fbD#readProxyContract#F9) of sUSDS performs this calculation. It takes a USDS amount and returns the sUSDS amount.

### Rates

The Sky Savings Rate can be fetched from the [sUSDS contract on Ethereum](https://etherscan.io/token/0xa3931d71877C0E7a3148CB7Eb4463524FEc27fbD#readProxyContract#F24) or from the [SSROracle on external networks](https://basescan.org/address/0x65d946e533748A998B1f0E430803e39A6388f7a1#readContract#F13) as the `ssr` variable. `ssr` is a 27-decimal variable. This is a per-second rate, so to calculate the APY, use the following conversion:

`APY = (ssr/ray)^(seconds_in_a_year)-1 = (ssr/ray)^(60*60*24*365)-1`

An example is:

`APY = (1000000002659864411854984565/10^27)^(60*60*24*365)-1 = 0.0875 = 8.75%`

### Interest Rate Models

Since sUSDS has a "built-in" rate, integrators should consider this when defining their interest rate models.

In an Aave-type lending market, this would mean adjusting the base rate. From a USDS perspective, the base rate and optimal rate in this scenario are the additional rates on top of the SSR. The base rate could be set to 0 to just reflect the underlying SSR, with the optimal rate slightly above. These rates would therefore need to be set differently than for non-yielding stablecoins.

The combined rate of the SSR and the protocol rate in USDS terms would be calculated as:

`APY_combined_USDS = (1+ssr_apy) * (1+protocol_apy_sUSDS) - 1`

This applies to both lending and borrowing rates.

Note that we use APY for both rates. This can subsequently be converted into APRs if necessary, using the number of compounding periods.

**Example**

-   The Sky Savings Rate is 5% APY.
-   sUSDS price (chi) is `1.0384`

Alice deposits 1000 USDS into sUSDS and receives 962.98 sUSDS (worth 1000 USDS)

Alice deposits 962.98 sUSDS into a lending market which has an APY of 2%.

After a year, Alice will have earned:

`0.02 * 962.98 sUSDS = 19.26 sUSDS`

Making her total balance `962.98 + 19.26 = 982.24` sUSDS total.

In the same time span, sUSDS has increased in value by 5% against USDS.

`New_Price_sUSDS = Old_Price_sUSDS * 1.05 = 1.0384 * 1.05 = 1.0903`

Her total USDS amount after 1 year is:

`USDS_amount = sUSDS_amount * New_Price_sUSDS = 982.24 * 1.0903 = 1071`

This gives a combined APY for USDS of 7.1%

Which is equal to

`APY_combined_USDS = (1+ssr_apy) * (1+protocol_apy_sUSDS) - 1 = (1+0.05) * (1+0.02) - 1 = 0.071 = 7.1%`

### Abstracting away sUSDS

Since users are mostly familiar with lending/borrowing non-yielding stablecoins, it makes sense to abstract away the use of sUSDS. It's important to note that this is simply an sUSDS market on the backend, but with clever conversions will look and behave like a standard USDS lending market with a base rate equal to the Sky Savings Rate. This can be achieved using the ERC4626 conversion functions of the sUSDS token on Ethereum, or the Spark PSM on other networks, when depositing and withdrawing USDS into the lending market. Furthermore, the rate conversions above can be used to display accounting of supply, debt, lending, and borrowing rates in terms of USDS instead of sUSDS.

#### Price Feed

Since the market would be an sUSDS market on the backend, it will still use an sUSDS oracle for collateral pricing. See the price feed section for more information.

#### Depositing & Withdrawing USDS

If the user already has sUSDS, they should simply be able to deposit it directly. However, the frontend will still display balances, accounting, and rates for USDS using the conversion methods outlined above.

On Ethereum, if the user has USDS, the lending market can integrate the deposit function of sUSDS to mint sUSDS and transfer it into the lending market. The balances and rates shown to the user in the frontend would be converted to USDS, as per the Conversions and Rates sections above.

When the user withdraws, the system can leverage the withdraw function of sUSDS to send USDS to the user. This is also done when a user borrows USDS.

You can read about the sUSDS ERC4626 functions here:

- [sUSDS Developer Documentation](/dev/savings/susds-token#erc4626-token-functionality)

On networks other than Ethereum mainnet, sUSDS is not an ERC4626 token but a simple ERC20 token, which is why these conversion functions are not available in the token itself. Instead, you can leverage the Spark PSM, which enables swapping between USDS, sUSDS, and USDC with no slippage or fee (besides gas), to achieve the same functionality. You can read more about the Spark PSM here.

- [Spark PSM Developer Documentation](/dev/savings/spark-psm)

The Spark Liquidity Layer will ensure there is always enough liquidity on external networks for swapping.

#### USDS Balances & Debt

To display USDS balances and debt in the UI, the conversion functions in the "Conversions" section can be used to convert sUSDS balances to USDS balances.

#### USDS Lending and Borrow Rates

To display rates according to USDS, you can refer to the example in the Interest Rate Models section. The rates for USDS can be calculated using the Sky Savings Rate and the sUSDS borrow or lending rate as follows:

`APY_combined_USDS = (1+ssr_apy) * (1+protocol_apy_sUSDS) - 1`

#### USDS Liquidations

For liquidations, the protocol can elect to support paying down sUSDS debt using USDS, by using the same conversions as for lending and borrowing. Liquidators would still have to monitor the sUSDS debt and price to trigger liquidations.