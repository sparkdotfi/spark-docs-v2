# DelegationAwareSpToken

The special type of spToken that are minted and burned upon supply and withdraw of assets that has voting power associated _(which can be delegated)_ with them. These _spTokens_ are enabled to delegate voting power of the underlying asset to a different address.

_DelegationAwarespToken_ enables/implements all the methods available for spTokens with additional `delegateUnderlyingTo` method.

Refer [_spToken_](/dev/sparklend/tokens/sptoken) docs for full list of contract API

### delegateUnderlyingTo

`function delegateUnderlyingTo(address delegatee)`

Delegates voting power of the underlying asset to a `delegatee` address.

:::danger
This method can only be called by `POOL_ADMIN.`
:::
