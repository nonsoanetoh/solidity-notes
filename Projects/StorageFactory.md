```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.12;

import "./SimpleStorage.sol";

contract StorageFactory {
    SimpleStorage[] public simpleStorage;

    function createSimpleStorage() public {
        SimpleStorage newSimpleStorage = new SimpleStorage();
        simpleStorage.push(newSimpleStorage);
    }

    function saveValueToStorage(uint256 _simpleStorageIndex, uint256 _favouriteNumber) public {
        simpleStorage[_simpleStorageIndex].store(_favouriteNumber);
    }

    function readSimpleStorageValue(uint256 _simpleStorageIndex) public view returns(uint256) {
        return simpleStorage[_simpleStorageIndex].retrieve();
    }

}
```
