```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.12;

import "./SimpleStorage.sol";

contract ExtraStorage is SimpleStorage {
    function store(uint _favouriteNumber) public override {
        favouriteNumber = _favouriteNumber * 5;
    }
}
```
