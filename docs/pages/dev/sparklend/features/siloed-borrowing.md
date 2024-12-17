# Siloed Borrowing

This feature allow assets with potentially manipulatable oracles (for example illiquid Uni V3 pairs) to be listed on SparkLend as single borrow asset i.e. if user borrows siloed asset, they cannot borrow any other asset. This helps mitigating the risk associated with such assets from impacting the overall solvency of the protocol.

:::info
[Risk or Pool admin](/dev/sparklend/core-contracts/aclmanager#roles), selected by Maker Governance, can call [`setSiloedBorrowing`](/dev/sparklend/core-contracts/poolconfigurator#setsiloedborrowing) to set an asset in _Siloed Borrowing_ mode.
:::

## Supply Siloed Assets

A user can supply S\_iloed Asset\_ just like any other asset using [`supply()`](/dev/sparklend/core-contracts/pool#supply) method in `pool.sol`, though, the asset will not be enabled to use as collateral i.e. supplied amount will not add to total collateral balance of the user.

### Borrow Siloed Assets

:::danger
User borrowing a _siloed asset_ will \_ **not**\_ be allowed to \_\_ borrow \_\_ any other asset\_.\_
:::

User can borrow _Siloed Assets_ using [`borrow()`](/dev/sparklend/core-contracts/pool#borrow) method in `pool.sol` , only if:

* It is first borrow onBehalf of the address

OR

* Existing user debt is of the same _siloed asset._

To check if user is in Siloed Borrowing state, you can see if underlying asset borrowed by user is s\_iloed\_ using [`getSiloedBorrowing()`](dev/sparklend/core-contracts/aavedataprovider#getsiloedborrowing) method on AaveDataProvider.sol.

### Check if Reserved for Siloed Borrowing

```solidity
import {AaveProtocolDataProvider} from '@aave/core-v3/contracts/misc/AaveProtocolDataProvider.sol';
AaveProtocolDataProvider poolDataProvider = AaveProtocolDataProvider(provider.getPoolDataProvider());
// address of the underlying asset
address asset = "0x...";

protocolDataProvider.getSiloedBorrowing(asset);
```

### FAQ

#### How can user enter siloed borrowing state?

User automatically enters siloed borrowing state on their first successful borrow of siloed asset.

#### How does user exit siloed borrowing state?

User must repay all their debt to exist siloed borrowing state.
