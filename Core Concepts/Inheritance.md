```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.12;

contract A {

    string public message = "I am contract A";

    function display() public view virtual returns(string memory) {
        return message;
    }
}

contract B is A {
    function display() public view override(A) virtual returns(string memory) {
        return string.concat(super.display(), " B");
    }
}

contract C is B {
    function display() public view override(B) virtual returns(string memory) {
        return string.concat(super.display(), " C");
    }
}
```
