# WOM-PROXY

**Secure Token Upgradability.** Build on a solid foundation of community-vetted code, utilizing [open-zeppelin industry standards](https://github.com/OpenZeppelin/openzeppelin-contracts). 

 * [WOMProxyAdmin.sol](contracts/WOMProxyAdmin.sol) is build using OpenZeppelin [ProxyAdmin.sol](https://github.com/OpenZeppelin/openzeppelin-sdk/blob/master/packages/lib/contracts/upgradeability/ProxyAdmin.sol) contract.  This is a contract that acts as the `Proxy Admin` of the deployed [WomTokenProxy.sol](contracts/WomTokenProxy.sol) contract.  By doing this you are able to execute non-transactional view functions to obtain the `implementation()` and `admin()` which is not available without deploying the [WOMProxyAdmin.sol](contracts/WOMProxyAdmin.sol) contract.
 * [WomToken.sol](contracts/WomToken.sol) uses your previous implementation.  Please see [this diff](https://www.diffchecker.com/0Ce4XKPg) to validate that there has not been any changes apart from `constructor()` to `intiailize()` which is required for [OpenZeppelin Proxy contracts to operate successfully](https://docs.openzeppelin.com/upgrades-plugins/1.x/writing-upgradeable).
 * [WomTokenProxy.sol](contracts/WomTokenProxy.sol) is a proxy contract that utilizes OpenZeppelin [AdminUpgradeabilityProxy.sol](https://github.com/OpenZeppelin/openzeppelin-sdk/blob/master/packages/lib/contracts/upgradeability/AdminUpgradeabilityProxy.sol). 



## Overview

Code base has been tested 100% to ensure no unforeseen bugs, and will help the internal team understand how proxy contracts operate.  [UpgradeExample.sol](contracts/upgrade/UpgradeExample.sol) shows an example for when you upgrade your contracts, and this can be seen within the [WOMProxy.test.js](test/WOMProxy.test.js) as well.

## Diff
[Visit here](https://www.diffchecker.com/0Ce4XKPg) to see the diff in contracts.  You'll notice that the only change is the `name, symbol, decimals, and initialSupply` moving from `constant` to public, and from `constructor()` to `initialize()`.  Additionally, the order of the contracts within one flattened contract is different but that doesn't imply a change in the codebase. 

## Security

Please report any security issues you find to info@womprotocol.io, and good luck ¯\_(ツ)_/¯.