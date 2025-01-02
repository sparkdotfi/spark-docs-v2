# ACLManager

## ACLManager

_**Access Control List Manager**_ is the main registry of system roles and permissions.

ACLManager allows a _**Role Admin**_ to manage roles. _**Role Admin**_ is itself a role that is managed by the `DEFAULT_ADMIN_ROLE`.

`DEFAULT_ADMIN_ROLE` is held by the _ACLAdmin,_ which is initialised in `PoolAddressesProvider`.

:::info
On Ethereum chain `PoolAddressesProvider`, is owned by Maker Governance. In networks other than Ethereum, either the _Crosschain Governance Bridges_ or _Community Multisigs_ are used to manage the `PoolAddressesProvider`.
:::

## Roles

Below we outline the powers/responsibilities of the roles and the specific methods that are only accessible to the holders of these roles.

| Role                  | Responsibilities / Powers                                                                                                                                                                                                                                      | Methods Accessible                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `FLASH_BORROWER`      | Flash loan premium is waived for the holders of this role.⛔️ Does not include flashLoanSimple                                                                                                                                                    | `flashLoan`                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `BRIDGE`              | Can leverage the Portal feature                                                                                                                                                                                                                                | mintUnbacked backUnbacked                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `ASSET_LISTING_ADMIN` | Can update asset oracle sources  fallback oracle  add new assets to the Spark market                                                                                                                                       |  setAssetSources setFallbackOracle  initReserves                                                                                                                                                                                                                                                                                                                                                                                                           |
| `RISK_ADMIN`          | Can update grace period of Oracle Sentinels  reserve params  unbacked mint cap  liquidation protocol fee  existing eMode categories and create new. (not category 0)  add/remove asset in silo mode   |  setGracePeriod  setReserveBorrowing  configureReserveAsCollateral  setReserveStableRateBorrowing  setReserveFreeze  setBorrowableInIsolation  setReserveFactor  setDebtCeiling  setBorrowCap  setSupplyCap  setLiquidationProtocolFee  setEModeCategory  setAssetEModeCategory  setUnbackedMintCap  setReserveInterestRateStrategyAddress  setSiloedBorrowing   |
| `ACL_ADMIN`           | Manage the role admins in the ACLManager                                                                                                                                                                                                                       |  setRoleAdmin  addPoolAdmin  removePoolAdmin  addEmergencyAdmin  removeEmergencyAdmin  addRiskAdmin  removeRiskAdmin  addFlashBorrower  removeFlashBorrower  addBridge  removeBridge  addAssetListingAdmin  removeAssetListingAdmin                                                                                                                                                   |
| `EMERGENCY_ADMIN`     | Can pause/unpause the pool or individual reserve                                                                                                                                                                                                               | setPoolPause                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `POOL_ADMIN`          | Can update token implementations  drop reserves  pause/unpause reserves  activate/deactivate reserves  update premiums  do all the things available to RISK_ADMIN   ASSET_LISTING_ADMIN          |  all methods available to <code>RISK_ADMIN</code>  all methods available to <code>ASSET_LISTING_ADMIN</code>  dropReserve  updateSpToken  updateStableDebtToken  updateVariableDebtToken  setReserveActive  updateBridgeProtocolFee  updateFlashloanPremiumTotal  updateFlashloanPremiumToProtocol                                                                                                         |


## View Methods

### isPoolAdmin

`function isPoolAdmin(address admin)`

Returns `true` if the address has `POOL_ADMIN` role.

### isEmergencyAdmin

`function isEmergencyAdmin(address admin)`

Returns `true` if the address has `EMERGENCY_ADMIN` role.

### isRiskAdmin

`function isRiskAdmin(address admin)`

Returns `true` if the address has `RISK_ADMIN` role.

### isFlashBorrower

`function isFlashBorrower(address borrower)`

Returns `true` if the address has `FLASH_BORROWER` role.

### isBridge

`function isBridge(address bridge)`

Returns `true` if the address has `BRIDGE` role.

### isAssetListingAdmin

`function isAssetListingAdmin(address admin)`

Returns `true` if the address has `ASSET_LISTING_ADMIN` role.

## Write Methods

### setRoleAdmin

`setRoleAdmin(bytes32 role, bytes32 adminRole)`

Setup admin to manage Roles.

:::info
This method can only be called by address with `DEFAULT_ADMIN_ROLE`.
:::

Call Params

| Name      | Type    | Description                                                                                                                                                                             |
| --------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| role      | bytes32 | keccak256 hash of one of the following: POOL_ADMIN  EMERGENCY_ADMIN  RISK_ADMIN  FLASH_BORROWER  BRIDGE  ASSET_LISTING_ADMIN   |
| adminRole | bytes32 | adminRole responsible for role. 0x00 is reserved for DEFAULT\_ADMIN\_ROLE                                                                                                               |

### addPoolAdmin

`addPoolAdmin(address admin)`

Add address to the list of members in `POOL_ADMIN` role. Holders of this role can update token implementations, drop, (un)pause and (de)activate reserves, update premiums and do everything the `ASSET_LISTING_ADMIN` and `RISK_ADMIN` can do.

:::info
Can be called only by _Role Admin_, specified by _Maker Governance_, responsible for managing `POOL_ADMIN` role.
:::

Call Params

| Name  | Type    | Description                                     |
| ----- | ------- | ----------------------------------------------- |
| admin | address | address which will be granted POOL\_ADMIN role. |

### removePoolAdmin

`removePoolAdmin(address admin)`

Remove given address from the list of members in `POOL_ADMIN` role.

:::info
Can be called only by _Role Admin_, specified by _Maker Governance_, responsible for managing `POOL_ADMIN` role.
:::

Call Params

| Name  | Type    | Description                                                     |
| ----- | ------- | --------------------------------------------------------------- |
| admin | address | address for which POOL\_ADMIN role permissions must be revoked. |

### addEmergencyAdmin

`addEmergencyAdmin(address admin)`

Add address to the list of members in `EMERGENCY_ADMIN` role. Holders of this role can pause and unpause the pool or an individual reserve.

:::info
Can be called only by _Role Admin_, specified by _Maker Governance_, responsible for managing`EMERGENCY_ADMIN` role.
:::

| Name  | Type    | Description                                          |
| ----- | ------- | ---------------------------------------------------- |
| admin | address | address which will be granted EMERGENCY\_ADMIN role. |

### removeEmergencyAdmin

`function removeEmergencyAdmin(address admin)`

Remove given address from the list of members in `EMERGENCY_ADMIN` role.

:::info
Can be called only by _Role Admin_, specified by _Maker Governance_, responsible for managing `EMERGENCY_ADMIN` role.
:::

| Name  | Type    | Description                                                          |
| ----- | ------- | -------------------------------------------------------------------- |
| admin | address | address for which EMERGENCY\_ADMIN role permissions must be revoked. |

### addRiskAdmin

`function addRiskAdmin(address admin)`

Add address to the list of members in `RISK_ADMIN` role. Holders of this role can update grace period of Oracle Sentinels, reserve params, unbacked mint cap, liquidation fee and eMode categories.

| Name  | Type    | Description                                     |
| ----- | ------- | ----------------------------------------------- |
| admin | address | address which will be granted RISK\_ADMIN role. |

### removeRiskAdmin

Remove given address from the list of members in `RISK_ADMIN` role.

| Name  | Type    | Description                                                     |
| ----- | ------- | --------------------------------------------------------------- |
| admin | address | address for which RISK\_ADMIN role permissions must be revoked. |

### addFlashBorrower

`function addFlashBorrower(address borrower)`

Add address to the list of members in `FLASH_BORROWER` role. Holders of this role do not pay premium for flash loan (Does not apply to `flashLonaSimple`).

### removeFlashBorrower

`function removeFlashBorrower(address borrower)`

Remove given address from the list of members in `FLASH_BORROWER` role.

| Name  | Type    | Description                                                         |
| ----- | ------- | ------------------------------------------------------------------- |
| admin | address | address for which FLASH\_BORROWER role permissions must be revoked. |

### addBridge

`addBridge(address bridge)`

Add contract address to the list of _**bridges**_. Holders of this role can leverage the Portal feature to seamlessly move supplied assets across Spark Lend markets on different networks.

:::info
 Can be called only by _Role Admin_, specified by _Maker Governance_, responsible for managing `BRIDGE` role.
:::

| Name   | Type    | Description                                |
| ------ | ------- | ------------------------------------------ |
| bridge | address | address which will be granted BRIDGE role. |

### removeBridge

`removeBridge(address bridge)`

Remove contract address from the list of _**bridges**_.

:::info
 Can be called only by _Role Admin_, specified by _Maker Governance_, responsible for managing `BRIDGE` role.
:::

| Name   | Type    | Description                                                |
| ------ | ------- | ---------------------------------------------------------- |
| bridge | address | address for which BRIDGE role permissions must be revoked. |

### addAssetListingAdmin

`function addAssetListingAdmin(address admin)`

Add address to the list of member in `ASSET_LISTING_ADMIN` role. Holder of this role can update oracles & add new asset to the Spark market.

| Name  | Type    | Description                                               |
| ----- | ------- | --------------------------------------------------------- |
| admin | address | address which will be granted ASSET\_LISTING\_ADMIN role. |

### removeAssetListingAdmin

`function removeAssetListingAdmin(address admin)`

Remove address from the list of members in `ASSET_LISTING_ADMIN` role.

| Name  | Type    | Description                                                               |
| ----- | ------- | ------------------------------------------------------------------------- |
| admin | address | address for which ASSET\_LISTING\_ADMIN role permissions must be revoked. |

## ABI

```
[
    {
        "inputs": [
            {
                "internalType": "contract IPoolAddressesProvider",
                "name": "provider",
                "type": "address"
            }
        ],
        "stateMutability": "nonpayable",
        "type": "constructor"
    },
    {
        "anonymous": false,
        "inputs": [
            {
                "indexed": true,
                "internalType": "bytes32",
                "name": "role",
                "type": "bytes32"
            },
            {
                "indexed": true,
                "internalType": "bytes32",
                "name": "previousAdminRole",
                "type": "bytes32"
            },
            {
                "indexed": true,
                "internalType": "bytes32",
                "name": "newAdminRole",
                "type": "bytes32"
            }
        ],
        "name": "RoleAdminChanged",
        "type": "event"
    },
    {
        "anonymous": false,
        "inputs": [
            {
                "indexed": true,
                "internalType": "bytes32",
                "name": "role",
                "type": "bytes32"
            },
            {
                "indexed": true,
                "internalType": "address",
                "name": "account",
                "type": "address"
            },
            {
                "indexed": true,
                "internalType": "address",
                "name": "sender",
                "type": "address"
            }
        ],
        "name": "RoleGranted",
        "type": "event"
    },
    {
        "anonymous": false,
        "inputs": [
            {
                "indexed": true,
                "internalType": "bytes32",
                "name": "role",
                "type": "bytes32"
            },
            {
                "indexed": true,
                "internalType": "address",
                "name": "account",
                "type": "address"
            },
            {
                "indexed": true,
                "internalType": "address",
                "name": "sender",
                "type": "address"
            }
        ],
        "name": "RoleRevoked",
        "type": "event"
    },
    {
        "inputs": [],
        "name": "ADDRESSES_PROVIDER",
        "outputs": [
            {
                "internalType": "contract IPoolAddressesProvider",
                "name": "",
                "type": "address"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [],
        "name": "ASSET_LISTING_ADMIN_ROLE",
        "outputs": [
            {
                "internalType": "bytes32",
                "name": "",
                "type": "bytes32"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [],
        "name": "BRIDGE_ROLE",
        "outputs": [
            {
                "internalType": "bytes32",
                "name": "",
                "type": "bytes32"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [],
        "name": "DEFAULT_ADMIN_ROLE",
        "outputs": [
            {
                "internalType": "bytes32",
                "name": "",
                "type": "bytes32"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [],
        "name": "EMERGENCY_ADMIN_ROLE",
        "outputs": [
            {
                "internalType": "bytes32",
                "name": "",
                "type": "bytes32"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [],
        "name": "FLASH_BORROWER_ROLE",
        "outputs": [
            {
                "internalType": "bytes32",
                "name": "",
                "type": "bytes32"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [],
        "name": "POOL_ADMIN_ROLE",
        "outputs": [
            {
                "internalType": "bytes32",
                "name": "",
                "type": "bytes32"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [],
        "name": "RISK_ADMIN_ROLE",
        "outputs": [
            {
                "internalType": "bytes32",
                "name": "",
                "type": "bytes32"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "admin",
                "type": "address"
            }
        ],
        "name": "addAssetListingAdmin",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "bridge",
                "type": "address"
            }
        ],
        "name": "addBridge",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "admin",
                "type": "address"
            }
        ],
        "name": "addEmergencyAdmin",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "borrower",
                "type": "address"
            }
        ],
        "name": "addFlashBorrower",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "admin",
                "type": "address"
            }
        ],
        "name": "addPoolAdmin",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "admin",
                "type": "address"
            }
        ],
        "name": "addRiskAdmin",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "bytes32",
                "name": "role",
                "type": "bytes32"
            }
        ],
        "name": "getRoleAdmin",
        "outputs": [
            {
                "internalType": "bytes32",
                "name": "",
                "type": "bytes32"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "bytes32",
                "name": "role",
                "type": "bytes32"
            },
            {
                "internalType": "address",
                "name": "account",
                "type": "address"
            }
        ],
        "name": "grantRole",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "bytes32",
                "name": "role",
                "type": "bytes32"
            },
            {
                "internalType": "address",
                "name": "account",
                "type": "address"
            }
        ],
        "name": "hasRole",
        "outputs": [
            {
                "internalType": "bool",
                "name": "",
                "type": "bool"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "admin",
                "type": "address"
            }
        ],
        "name": "isAssetListingAdmin",
        "outputs": [
            {
                "internalType": "bool",
                "name": "",
                "type": "bool"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "bridge",
                "type": "address"
            }
        ],
        "name": "isBridge",
        "outputs": [
            {
                "internalType": "bool",
                "name": "",
                "type": "bool"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "admin",
                "type": "address"
            }
        ],
        "name": "isEmergencyAdmin",
        "outputs": [
            {
                "internalType": "bool",
                "name": "",
                "type": "bool"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "borrower",
                "type": "address"
            }
        ],
        "name": "isFlashBorrower",
        "outputs": [
            {
                "internalType": "bool",
                "name": "",
                "type": "bool"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "admin",
                "type": "address"
            }
        ],
        "name": "isPoolAdmin",
        "outputs": [
            {
                "internalType": "bool",
                "name": "",
                "type": "bool"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "admin",
                "type": "address"
            }
        ],
        "name": "isRiskAdmin",
        "outputs": [
            {
                "internalType": "bool",
                "name": "",
                "type": "bool"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "admin",
                "type": "address"
            }
        ],
        "name": "removeAssetListingAdmin",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "bridge",
                "type": "address"
            }
        ],
        "name": "removeBridge",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "admin",
                "type": "address"
            }
        ],
        "name": "removeEmergencyAdmin",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "borrower",
                "type": "address"
            }
        ],
        "name": "removeFlashBorrower",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "admin",
                "type": "address"
            }
        ],
        "name": "removePoolAdmin",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "address",
                "name": "admin",
                "type": "address"
            }
        ],
        "name": "removeRiskAdmin",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "bytes32",
                "name": "role",
                "type": "bytes32"
            },
            {
                "internalType": "address",
                "name": "account",
                "type": "address"
            }
        ],
        "name": "renounceRole",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "bytes32",
                "name": "role",
                "type": "bytes32"
            },
            {
                "internalType": "address",
                "name": "account",
                "type": "address"
            }
        ],
        "name": "revokeRole",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "bytes32",
                "name": "role",
                "type": "bytes32"
            },
            {
                "internalType": "bytes32",
                "name": "adminRole",
                "type": "bytes32"
            }
        ],
        "name": "setRoleAdmin",
        "outputs": [],
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "inputs": [
            {
                "internalType": "bytes4",
                "name": "interfaceId",
                "type": "bytes4"
            }
        ],
        "name": "supportsInterface",
        "outputs": [
            {
                "internalType": "bool",
                "name": "",
                "type": "bool"
            }
        ],
        "stateMutability": "view",
        "type": "function"
    }
]
```

</details>
