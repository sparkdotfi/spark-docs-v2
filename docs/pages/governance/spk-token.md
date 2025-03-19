---
description: Learn about the SPK Token and Pre-farming Airdrop.
---

# SPK Token & Airdrop

:::danger
**The SPK token is not released yet, please beware of scammers.**
:::

:::info
SPK pre-farming airdrop is ongoing, see current stats at [BlockAnalitica's website](https://spark.blockanalitica.com/v1/ethereum/airdrop/).
:::

## What is SPK?

SPK is the governance token of the Spark Sky Star. [Learn more about this here.](https://forum.makerdao.com/t/makerdao-endgame-launch-season/23857)

## What is Spark Sky Star?

Spark is a Sky Star, a part of the Sky Ecosystem. [You can read more about the Sky Star here.](https://forum.makerdao.com/t/sky-has-arrived/24959#p-98600-spark-the-first-sky-star-14)

Sky Stars are currently in bootstrapping phase and will be officially launched in 2025

## Has SPK been launched yet?

The SPK token has not yet been launched. Please beware of scammers and false SPK tokens.

When the token is launched, announcements will be made from the official X accounts of [Sky (@SkyEcosystem)](https://x.com/SkyEcosystem) and [Spark (@sparkdotfi)](https://x.com/sparkdotfi) once the launch date arrives. No official launch date has been determined yet.

## What is the SPK pre-farming airdrop?

Spark is running a pre-farming airdrop campaign based on usage of its lending platform. Users of the platform will receive an airdrop, depending on how much and how long they have used the platform during specific periods, also known as seasons. Users will continue to be able to farm the SPK token after it has launched. See further details on [how to qualify](#how-do-i-qualify-for-the-spk-airdrop) for the airdrop, and the [different seasons](#season-1-aug-20-2023-may-20-2024) below.

## How many SPK tokens are distributed?

### Season 1 (Aug 20, 2023 - May 20, 2024)

In season 1 60M SPK was allocated to users who qualified for the airdrop.

* 80 % (48M) is allocated to users borrowing DAI
* 20 % (12M) is allocated to users supplying ETH.

Season 1 was a pre-farming period of 9 months active from Aug 20 2023 14:25 UTC (Ethereum block 17956537) to May 20 2024 14:25 UTC.

**Note:** In season 1 the [airdrop formula](#how-much-spk-will-i-earn) was used across the entire time period, so your allocation is based on the qualifying amount and how long it was borrowed/supplied.

### Active: Season 2 (May 20, 2024 - Sky Star Launch TBD)

The current season offers SPK rewards across both SparkLend and Aave. Learn more about how to earn rewards on the different lending markets below.

#### SparkLend

In season 2 14.5M SPK will be rewarded per month to SparkLend users who qualify for the airdrop.

The monthly SPK rewards are allocated as following:

* 80 % is allocated to users borrowing USDS or DAI
* 20 % is allocated to users supplying ETH.

Season 2 is an additional pre-farming period, which runs until the Spark Sky Star launches as part of Sky Endgame launch season.

**Note:** In season 2, the [airdrop formula](#how-much-spk-will-i-earn) will be applied per block, meaning you will accrue SPK each block, based on the qualifying amount borrowed/supplied.

#### Aave

In season 2 7.25M SPK will be rewarded per month to Aave users who qualify for the airdrop.

The monthly SPK rewards are allocated as following:

* 100 % is allocated to users who supply USDS into Aave.

The idle USDS supply consistently earns the Sky Savings Rate (SSR), ensuring capital efficiency for suppliers.

To prevent gaming the incentives through "stablecoin looping", meaning supplying USDS and borrowing DAI or USDS and supplying USDS again, effectively providing a highly leveraged USDS position, the following formula is used to discount such behavior:

`USDS Supplies - Sum_i(USDS+DAI Borrow Amount (in USD) / USDS+DAI Liquidation Threshold)`

[You can read more about the Aave SPK rewards here.](https://forum.sky.money/t/spark-proposal-for-integrations-into-aave/25005#p-98707-h-1-usds-incentives-program-2)

## What will the total supply of SPK be?

The SPK emissions follow the rules set forth in [MIP101: Sky Atlas Immutable Alignment Artifact](https://forum.makerdao.com/t/mip102c2-sp21-mip-amendment-subproposal/23039/5#h-4312-allocatordao-emissions-107) as part of the Sky Endgame, which states that **4.6 billion SPK tokens will be emitted over the first 10 years**. 4 billion tokens are emitted through Genesis farming, which gradually decreases over time, and 600 million tokens are allocated to a workforce bonus pool. See the allocation chart below:

![](/assets/spk_distribution.png)
*SPK Genesis Distribution*

The Genesis farming follow the following emission schedule:

|             | Yearly Amount of SPK (in millions) | Total Amount of SPK (in millions) |
| ----------- | ---------------------------------- | --------------------------------- |
| Year 1      | 1000                               | 1000                              |
| Year 2      | 1000                               | 2000                              |
| Year 3      | 500                                | 2500                              |
| Year 4      | 500                                | 3000                              |
| Year 5      | 250                                | 3250                              |
| Year 6      | 250                                | 3500                              |
| Year 7      | 125                                | 3625                              |
| Year 8      | 125                                | 3750                              |
| Year 9      | 125                                | 3875                              |
| Year 10     | 125                                | 4000                              |

![](/assets/spk_emissions.png)
*SPK Emissions Over First 10 Years*

## How do I qualify for the SPK airdrop?

This section only relates to SPK rewards on SparkLend. To learn more about the Aave SPK rewards [read more here](#aave).

Users of [Spark](http://app.spark.fi) who borrow DAI or supply ETH qualify for the SPK airdrop. You can see the formula for calculating the SPK amount in the [following section](#how-many-spk-tokens-are-distributed).

**Note**: Attempting to game the airdrop by lending sDAI while borrowing DAI or lending and borrowing ETH on the same account will forfeit your inclusion in the airdrop.

For clarity here are some **valid examples:**

* Supply wstETH, Borrow USDS - USDS amount is included ✅
* Supply rETH, Borrow USDS - USDS amount is included ✅
* Supply wstETH, Borrow USDS, Swap USDS for sUSDS - USDS amount is included ✅
* Supply ETH, Borrow USDS - Both ETH and USDS amounts are included in the airdrop ✅
* Supply rETH, Supply ETH, Borrow USDS - Both ETH and USDS amounts are included in the airdrop ✅
* Supply GNO, Borrow USDS - USDS amount is included ✅
* Supply wstETH, Borrow DAI - DAI amount is included ✅
* Supply rETH, Borrow DAI - DAI amount is included ✅
* Supply wstETH, Borrow DAI, Swap DAI for sDAI - DAI amount is included ✅
* Supply ETH, Borrow DAI - Both ETH and DAI amounts are included in the airdrop ✅
* Supply rETH, Supply ETH, Borrow DAI - Both ETH and DAI amounts are included in the airdrop ✅
* Supply GNO, Borrow DAI - DAI amount is included ✅
* Supply ETH - ETH amount is included ✅
* Supply ETH, Borrow wstETH - ETH amount is included ✅

**Invalid examples:**

* Supply sUSDS, Borrow USDS - FORFEIT AIRDROP ❌
* Supply sUSDS, Borrow DAI - FORFEIT AIRDROP ❌
* Supply sDAI, Borrow USDS - FORFEIT AIRDROP ❌
* Supply sDAI, Borrow DAI - FORFEIT AIRDROP ❌
* Supply ETH, Borrow ETH - FORFEIT AIRDROP ❌
* Supply wstETH, Borrow USDS, Deposit sUSDS as Collateral - FORFEIT AIRDROP ❌
* Supply wstETH, Borrow USDS, Deposit sDAI as Collateral - FORFEIT AIRDROP ❌
* Supply wstETH, Borrow DAI, Deposit sDAI as Collateral - FORFEIT AIRDROP ❌
* Supply wstETH, Borrow DAI, Deposit sUSDS as Collateral - FORFEIT AIRDROP ❌

**Note:** Borrowing DAI and depositing it into sDAI using the Cash and Savings feature of Spark is accepted and does not count against the airdrop. It is only penalized if you supply sDAI as collateral to borrow against.

## How much SPK will I earn?

This section only relates to SPK rewards on SparkLend. To learn more about the Aave SPK rewards [read more here](#aave).

The SPK Airdrop for SparkLend is calculated using the following formula:

`Airdrop = 80% * USDS+DAI Borrows in USD + 20% * ETH Supplies in USD`

Please note all supplies and borrows are denominated in USD and will use the on-chain oracle price at that block to determine the conversion.

For Aave SPK rewards, [read more here](#aave).

To calculate the final airdrop, the formula will be computed for every account on each block within the valid time range, and the Airdrop value will be summed over every included block to produce a final number for each account. The relative weight of this number will then be converted to the allocated SPK token supply. See the [seasons sections](#season-1-aug-20-2023-may-20-2024) for the different time frames.

### Anti-cheat formula

As noted in the “[How do I qualify for the airdrop?](#how-do-i-qualify-for-the-spk-airdrop)” section, there are certain actions that count against the airdrop on SparkLend. The full airdrop formula including the anti-cheat measure is as follows:

Full anti-cheat formula (don’t worry about this if you are using the system legitimately:

`Airdrop = 80% * (DAI Borrows + USDS Borrows - sDAI Supplies * sDAI Liquidation Threshold - sUSDS Supplies * sUSDS Liquidation Threshold) + 20% * (ETH Supplies - ETH Borrows / ETH Liquidation Threshold)`

For Aave Rewards anti-cheat formula, [read more here](#aave).

## Which geographies qualify for the pre-farming airdrop?

The pre-farming airdrop is not available to users with IPs flagged by the [Location Resilience in MIP108: Accessibility Scope Bounded Mutable Alignment Artifact.](https://mips.makerdao.com/mips/details/MIP108#8-location-resilience)

## Which networks qualify for the airdrop?

You are only able to earn SPK tokens using Spark and Aave lending markets on Ethereum mainnet. Spark and Aave lending markets on other networks do not qualify for the SPK airdrop.

## Where can I see accrued SPK tokens?

On the [Spark App](https://app.spark.fi/), once you have connected your wallet, you are able to see your accumulated SPK tokens in the top right corner.

You can also find your accumulated SPK tokens by navigating to [https://spark.blockanalitica.com/v1/ethereum/airdrop/](https://spark.blockanalitica.com/v1/ethereum/airdrop/) and searching for your wallet address.

## When is SPK released?

The SPK token will be released when the Spark Sky Star launches as part of the Sky Endgame launch season. The exact date has not yet been determined.

## How do I claim SPK?

Details on how to claim SPK will be announced on the official X accounts of [Sky (@SkyEcosystem)](https://x.com/SkyEcosystem) and [Spark (@sparkdotfi)](https://x.com/sparkdotfi) once the launch date arrives.


