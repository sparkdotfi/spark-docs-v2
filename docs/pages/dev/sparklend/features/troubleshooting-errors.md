# Troubleshooting

## Error Codes

In order to reduce gas usage and code size, /spark-protocol contracts return numbered errors. If you are making calls to the protocol and receive numbered errors, you can use the reference below to know what is the error. Alternatively, you can also find what the numbers represent by checking the [`Errors.sol`](https://github.com/aave/aave-v3-core/blob/master/contracts/protocol/libraries/helpers/Errors.sol)

### Reference Guide

Error codes are returned as string.

| ERROR CODE (string) | ERROR NAME                                          | ERROR DESCRIPTION                                                                                         |
| ------------------- | --------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| 1                   | CALLER\_NOT\_POOL\_ADMIN                            | The caller of the function is not a pool admin                                                            |
| 2                   | CALLER\_NOT\_EMERGENCY\_ADMIN                       | The caller of the function is not an emergency admin                                                      |
| 3                   | CALLER\_NOT\_POOL\_OR\_EMERGENCY\_ADMIN             | The caller of the function is not a pool or emergency admin                                               |
| 4                   | CALLER\_NOT\_RISK\_OR\_POOL\_ADMIN                  | The caller of the function is not a risk or pool admin                                                    |
| 5                   | CALLER\_NOT\_ASSET\_LISTING\_OR\_POOL\_ADMIN        | The caller of the function is not an asset listing or pool admin                                          |
| 6                   | CALLER\_NOT\_BRIDGE                                 | The caller of the function is not a bridge                                                                |
| 7                   | ADDRESSES\_PROVIDER\_NOT\_REGISTERED                | Pool addresses provider is not registered                                                                 |
| 8                   | INVALID\_ADDRESSES\_PROVIDER\_ID                    | Invalid id for the pool addresses provider                                                                |
| 9                   | NOT\_CONTRACT                                       | Address is not a contract                                                                                 |
| 10                  | CALLER\_NOT\_POOL\_CONFIGURATOR                     | The caller of the function is not the pool configurator                                                   |
| 11                  | CALLER\_NOT\_ATOKEN                                 | The caller of the function is not an SpToken                                                              |
| 12                  | INVALID\_ADDRESSES\_PROVIDER                        | The address of the pool addresses provider is invalid                                                     |
| 13                  | INVALID\_FLASHLOAN\_EXECUTOR\_RETURN                | Invalid return value of the flashloan executor function                                                   |
| 14                  | RESERVE\_ALREADY\_ADDED                             | Reserve has already been added to reserve list                                                            |
| 15                  | NO\_MORE\_RESERVES\_ALLOWED                         | Maximum amount of reserves in the pool reached                                                            |
| 16                  | EMODE\_CATEGORY\_RESERVED                           | Zero eMode category is reserved for volatile heterogeneous assets                                         |
| 17                  | INVALID\_EMODE\_CATEGORY\_ASSIGNMENT                | Invalid eMode category assignment to asset                                                                |
| 18                  | RESERVE\_LIQUIDITY\_NOT\_ZERO                       | The liquidity of the reserve needs to be 0                                                                |
| 19                  | FLASHLOAN\_PREMIUM\_INVALID                         | Invalid flashloan premium                                                                                 |
| 20                  | INVALID\_RESERVE\_PARAMS                            | Invalid risk parameters for the reserve                                                                   |
| 21                  | INVALID\_EMODE\_CATEGORY\_PARAMS                    | Invalid risk parameters for the eMode category                                                            |
| 22                  | BRIDGE\_PROTOCOL\_FEE\_INVALID                      | Invalid bridge protocol fee                                                                               |
| 23                  | CALLER\_MUST\_BE\_POOL                              | The caller of this function must be a pool                                                                |
| 24                  | INVALID\_MINT\_AMOUNT                               | Invalid amount to mint                                                                                    |
| 25                  | INVALID\_BURN\_AMOUNT                               | Invalid amount to burn                                                                                    |
| 26                  | INVALID\_AMOUNT                                     | Amount must be greater than 0                                                                             |
| 27                  | RESERVE\_INACTIVE                                   | Action requires an active reserve                                                                         |
| 28                  | RESERVE\_FROZEN                                     | Action cannot be performed because the reserve is frozen                                                  |
| 29                  | RESERVE\_PAUSED                                     | Action cannot be performed because the reserve is paused                                                  |
| 30                  | BORROWING\_NOT\_ENABLED                             | Borrowing is not enabled                                                                                  |
| 31                  | STABLE\_BORROWING\_NOT\_ENABLED                     | Stable borrowing is not enabled                                                                           |
| 32                  | NOT\_ENOUGH\_AVAILABLE\_USER\_BALANCE               | User cannot withdraw more than the available balance                                                      |
| 33                  | INVALID\_INTEREST\_RATE\_MODE\_SELECTED             | Invalid interest rate mode selected                                                                       |
| 34                  | COLLATERAL\_BALANCE\_IS\_ZERO                       | The collateral balance is 0                                                                               |
| 35                  | HEALTH\_FACTOR\_LOWER\_THAN\_LIQUIDATION\_THRESHOLD | Health factor is lesser than the liquidation threshold                                                    |
| 36                  | COLLATERAL\_CANNOT\_COVER\_NEW\_BORROW              | There is not enough collateral to cover a new borrow                                                      |
| 37                  | COLLATERAL\_SAME\_AS\_BORROWING\_CURRENCY           | Collateral is (mostly) the same currency that is being borrowed                                           |
| 38                  | AMOUNT\_BIGGER\_THAN\_MAX\_LOAN\_SIZE\_STABLE       | The requested amount is greater than the max loan size in stable rate mode                                |
| 39                  | NO\_DEBT\_OF\_SELECTED\_TYPE                        | For repayment of a specific type of debt, the user needs to have debt that type                           |
| 40                  | NO\_EXPLICIT\_AMOUNT\_TO\_REPAY\_ON\_BEHALF         | To repay on behalf of a user an explicit amount to repay is needed                                        |
| 41                  | NO\_OUTSTANDING\_STABLE\_DEBT                       | User does not have outstanding stable rate debt on this reserve                                           |
| 42                  | NO\_OUTSTANDING\_VARIABLE\_DEBT                     | User does not have outstanding variable rate debt on this reserve                                         |
| 43                  | UNDERLYING\_BALANCE\_ZERO                           | The underlying balance needs to be greater than 0                                                         |
| 44                  | INTEREST\_RATE\_REBALANCE\_CONDITIONS\_NOT\_MET     | Interest rate rebalance conditions were not met                                                           |
| 45                  | HEALTH\_FACTOR\_NOT\_BELOW\_THRESHOLD               | Health factor is not below the threshold                                                                  |
| 46                  | COLLATERAL\_CANNOT\_BE\_LIQUIDATED                  | The collateral chosen cannot be liquidated                                                                |
| 47                  | SPECIFIED\_CURRENCY\_NOT\_BORROWED\_BY\_USER        | User did not borrow the specified currency                                                                |
| 48                  | SAME\_BLOCK\_BORROW\_REPAY                          | Borrow and repay in same block is not allowed                                                             |
| 49                  | INCONSISTENT\_FLASHLOAN\_PARAMS                     | Inconsistent flashloan parameters                                                                         |
| 50                  | BORROW\_CAP\_EXCEEDED                               | Borrow cap is exceeded                                                                                    |
| 51                  | SUPPLY\_CAP\_EXCEEDED                               | Supply cap is exceeded                                                                                    |
| 52                  | UNBACKED\_MINT\_CAP\_EXCEEDED                       | Unbacked mint cap is exceeded                                                                             |
| 53                  | DEBT\_CEILING\_EXCEEDED                             | Debt ceiling is exceeded                                                                                  |
| 54                  | ATOKEN\_SUPPLY\_NOT\_ZERO                           | SpToken supply is not zero                                                                                |
| 55                  | STABLE\_DEBT\_NOT\_ZERO                             | Stable debt supply is not zero                                                                            |
| 56                  | VARIABLE\_DEBT\_SUPPLY\_NOT\_ZERO                   | Variable debt supply is not zero                                                                          |
| 57                  | LTV\_VALIDATION\_FAILED                             | Ltv validation failed                                                                                     |
| 58                  | INCONSISTENT\_EMODE\_CATEGORY                       | Inconsistent eMode category                                                                               |
| 59                  | PRICE\_ORACLE\_SENTINEL\_CHECK\_FAILED              | Price oracle sentinel validation failed                                                                   |
| 60                  | ASSET\_NOT\_BORROWABLE\_IN\_ISOLATION               | Asset is not borrowable in isolation mode                                                                 |
| 61                  | RESERVE\_ALREADY\_INITIALIZED                       | Reserve has already been initialized                                                                      |
| 62                  | USER\_IN\_ISOLATION\_MODE                           | User is in isolation mode                                                                                 |
| 63                  | INVALID\_LTV                                        | Invalid ltv parameter for the reserve                                                                     |
| 64                  | INVALID\_LIQ\_THRESHOLD                             | Invalid liquidity threshold parameter for the reserve                                                     |
| 65                  | INVALID\_LIQ\_BONUS                                 | Invalid liquidity bonus parameter for the reserve                                                         |
| 66                  | INVALID\_DECIMALS                                   | Invalid decimals parameter of the underlying asset of the reserve                                         |
| 67                  | INVALID\_RESERVE\_FACTOR                            | Invalid reserve factor parameter for the reserve                                                          |
| 68                  | INVALID\_BORROW\_CAP                                | Invalid borrow cap for the reserve                                                                        |
| 69                  | INVALID\_SUPPLY\_CAP                                | Invalid supply cap for the reserve                                                                        |
| 70                  | INVALID\_LIQUIDATION\_PROTOCOL\_FEE                 | Invalid liquidation protocol fee for the reserve                                                          |
| 71                  | INVALID\_EMODE\_CATEGORY                            | Invalid eMode category for the reserve                                                                    |
| 72                  | INVALID\_UNBACKED\_MINT\_CAP                        | Invalid unbacked mint cap for the reserve                                                                 |
| 73                  | INVALID\_DEBT\_CEILING                              | Invalid debt ceiling for the reserve                                                                      |
| 74                  | INVALID\_RESERVE\_INDEX                             | Invalid reserve index                                                                                     |
| 75                  | ACL\_ADMIN\_CANNOT\_BE\_ZERO                        | ACL admin cannot be set to the zero address                                                               |
| 76                  | INCONSISTENT\_PARAMS\_LENGTH                        | Array parameters that should be equal length are not                                                      |
| 77                  | ZERO\_ADDRESS\_NOT\_VALID                           | Zero address not valid                                                                                    |
| 78                  | INVALID\_EXPIRATION                                 | Invalid expiration                                                                                        |
| 79                  | INVALID\_SIGNATURE                                  | Invalid signature                                                                                         |
| 80                  | OPERATION\_NOT\_SUPPORTED                           | Operation not supported                                                                                   |
| 81                  | DEBT\_CEILING\_NOT\_ZERO                            | Debt ceiling is not zero                                                                                  |
| 82                  | ASSET\_NOT\_LISTED                                  | Asset is not listed                                                                                       |
| 83                  | INVALID\_OPTIMAL\_USAGE\_RATIO                      | Invalid optimal usage ratio                                                                               |
| 84                  | INVALID\_OPTIMAL\_STABLE\_TO\_TOTAL\_DEBT\_RATIO    | Invalid optimal stable to total debt ratio                                                                |
| 85                  | UNDERLYING\_CANNOT\_BE\_RESCUED                     | The underlying asset cannot be rescued                                                                    |
| 86                  | ADDRESSES\_PROVIDER\_ALREADY\_ADDED                 | Reserve has already been added to reserve list                                                            |
| 87                  | POOL\_ADDRESSES\_DO\_NOT\_MATCH                     | The token implementation pool address and the pool address provided by the initializing pool do not match |
| 88                  | STABLE\_BORROWING\_ENABLED                          | Stable borrowing is enabled                                                                               |
| 89                  | SILOED\_BORROWING\_VIOLATION                        | User is trying to borrow multiple assets including a siloed one                                           |
| 90                  | RESERVE\_DEBT\_NOT\_ZERO                            | // the total debt of the reserve needs to be 0                                                            |
