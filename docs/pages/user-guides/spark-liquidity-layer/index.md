---
description: Learn how the Spark Liquidity Layer works.
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Spark Liquidity Layer

## What is the Spark Liquidity Layer?

The Spark Liquidity Layer (SLL) automates liquidity provision of USDS, sUSDS, and USDC directly from Sky across various blockchain networks and DeFi protocols. This enables users to easily earn the Sky Savings Rate on their preferred network using sUSDS. Additionally, it allows Spark to automate liquidity provision into DeFi markets to optimize yield.

### Easy access to yield on any chain

A key benefit of the SLL is its automation of sUSDS liquidity provision to other networks, allowing users on those networks to earn yield on stablecoins. Previously, acquiring sUSDS on networks other than Ethereum mainnet was challenging due to low liquidity. The SLL addresses this by providing sUSDS liquidity against major stablecoins directly from Sky to supported networks, starting with Base with other major networks to follow soon. The aim is to offer users on any network access to the best risk-adjusted yield on stablecoins in DeFi.

### Generating yield for Spark

The SLL also enables Spark to provide liquidity directly into risk-adjusted yield strategies on other chains and protocols. For example, it can supply stablecoin liquidity to lending markets to earn interest, similar to current practices on Ethereum mainnet with Aave and Morpho. The yield earned from these strategies contributes to funding the Sky Savings Rate, which aims to provide the best risk-adjusted yield in DeFi.

## How does the Spark Liquidity Layer work?

The SLL utilizes the Sky Allocation System to provide liquidity in USDS, sUSDS, and USDC across various networks and DeFi markets. It does this by minting USDS and sUSDS through the Sky Allocator Vaults and bridging them to other networks using SkyLink.

Minted USDS is also used to swap for USDC through the Sky Peg Stability Module and then bridged to other networks using the [Circle Cross-chain Transfer Protocol (CCTP)](https://www.circle.com/cross-chain-transfer-protocol).

The bridged USDS, sUSDS, and USDC can then be deposited into liquidity pools, DeFi protocols, lending markets, or other yield strategies on the destination chain.

Sky aims to keep 25% of USDS backing in cash reserves, primarily USDC, to ensure USDS liquidity and stability. The SLL brings this liquidity from Ethereum mainnet to any supported chain. As a result, users can easily access ample liquidity, enabling them to move into sUSDS using USDC and vice versa. This brings the stability of USDS, the yield of sUSDS, and the liquidity of the Sky PSM to all of DeFi on any supported network.

### Automated Liquidity Management

The system uses off-chain monitoring software to determine when and where to deploy stablecoin liquidity. For instance, it monitors the liquidity levels of the Spark PSM on other networks to ensure sufficient USDS and sUSDS liquidity to meet the demand. It also monitors whether USDC reserves need to be bridged back to Ethereum mainnet. When action is required, transactions are automatically submitted to rebalance funds.

### Controlled By Sky

Sky Governance controls the SLL, and no other parties have custody or access to any funds in the system. The system is hardwired to only allow deployment of funds into use cases approved by Sky Governance.

### Minting USDS and sUSDS

The SLL uses the Sky Allocator Vault to mint USDS. These vaults are a key part of the Sky Star system, enabling Stars to mint USDS for investment or liquidity provision in different markets. This represents a shift from users primarily borrowing USDS directly from the Sky Protocol to a strategy where liquidity is directly deployed into external markets. This newer method offers more flexibility, ultimately allowing Sky to optimize its liquidity and yield, and offer a more competitive Sky Savings Rate. The SLL can deposit USDS into the Sky Savings Rate to receive sUSDS.

### Bridging

The system employs various bridging solutions depending on the token being bridged, the target network, and the specific destination or yield strategy.

#### SkyLink

Initially, to provide USDS and sUSDS liquidity to the Spark PSM on other chains, the system will use Sky's own canonical bridge, SkyLink.

#### CCTP

To provide cross-chain USDC liquidity, the system will use Circle's Cross-chain Transfer Protocol (CCTP) to bridge USDC across chains.

### Deployment of Funds

Once funds have been bridged to the destination chain, they can be deployed into use cases approved by Sky Governance. Funds are strictly limited to these approved strategies and cannot be transferred arbitrarily.

## Spark Liquidity Layer Integrations

### Direct Liquidity to Aave Lido Market

The SLL supplies USDS liquidity to the Aave Lido lending market. This allows Aave users to borrow USDS against approved collateral types, generating yield for Spark. The risk parameters such as maximum amount are controlled by Sky.\
You can find the Aave Lido USDS market here: [Aave Lido USDS market](https://app.aave.com/reserve-overview/?underlyingAsset=0xdc035d45d973e3ec169d2276ddab16f1e407384f\&marketName=proto\_lido\_v3).

### Direct Liquidity to Morpho Markets

The SLL supplies Dai liquidity to a series of Morpho lending markets that accepts Ethena's USDe and sUSDe as collateral. These various markets are isolated and have different risk parameters enabling a more granular approach to risk management. This allows Morpho users to borrow Dai against USDe and sUSDe, generating yield for Spark.

You can find the Dai Morpho markets here: [Morpho Spark Dai Vault](https://app.morpho.org/vault?vault=0x73e65DBD630f90604062f6E02fAb9138e713edD9\&network=mainnet).

### Cross-chain Liquidity using Spark PSM

A key use case for the SLL is providing liquidity to the cross-chain Spark PSM. The first supported network is Base, with other major networks to follow soon.

The Spark PSM enables swapping between USDS, sUSDS, and USDC with no slippage or fee beyond network fees. It uses a hardcoded 1.00 USD price for USDS and USDC, and an exchange rate oracle for the sUSDS price. Thus, the Spark PSM is not affected by deviating market prices or slippage.

The Spark PSM brings the liquidity of the Sky PSM on Ethereum mainnet to other chains such as Base, enabling users to easily swap between these assets. As a result, users can readily swap non-yielding stablecoins to sUSDS to earn the Sky Savings Rate. Conversely, the Spark PSM will always have ample liquidity, allowing users to exit from sUSDS to stablecoins.

## FAQ

### What protocols are supported by SLL?

The following protocols are currently supported by the SLL:

* SparkLend
* Aave
* Morpho

Additional protocols will be integrated on a continuous basis.

### What networks are supported by SLL?

The following networks are currently supported by the SLL:

* Ethereum
* Base

Other major networks will be supported soon.

### How do I obtain sUSDS on other networks?

On [app.spark.fi/savings](http://app.spark.fi/savings), you can deposit accepted stablecoins such as USDS or USDC on your preferred supported network (e.g. Base) to obtain sUSDS and earn the Sky Savings Rate.

### How can I exit my sUSDS position on other networks?

If you have sUSDS, you can swap it for other stablecoins such as USDS and USDC at [app.spark.fi/savings](http://app.spark.fi/savings). The SLL ensures there is always ample liquidity to exit your sUSDS position.

### What are the liquidity constraints for cross-chain liquidty?

The SLL ensures there is always ample liquidity for users to enter or exit sUSDS on supported networks. Sky aims to keep 25% of USDS collateral backing in cash reserves, which should provide a healthy buffer for users to exit, even for large volumes.

### Has the Spark Liquidity Layer been audited?

Yes, you can find the audit reports here: [Spark Liquidity Layer Audit Reports](/dev/security/security-and-audits#spark-liquidity-layer)

### Who controls the Spark Liquidity Layer?
Sky Governance determines the use cases supported by the SLL, such as networks and protocols, as well as the accepted risk parameters for each use case, including rate limits, maximum fund amounts or maximum volumes.
