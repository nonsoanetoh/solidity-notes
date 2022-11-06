```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.12;

contract Mapping {
    // syntax - mapping(keyType => valueType).

    // assigns a uint256 value for every string key
    mapping(string => uint256) public simpleMap;
    mapping(string => mapping(string => uint256)) public nestedMap;

    uint public min = type(uint).max;

    function addToSimpleMap(string memory _key, uint256 _value) public {
        simpleMap[_key] = _value;
    }

    function fetchSimpleMapValue(string memory _key) public view returns (uint256) {
        return simpleMap[_key];
    }

    // resets the value to its default - which in this case is 0
    function deleteSimpleMapValue(string memory _key) public {
        delete simpleMap[_key];
    }

    function addtoNestedMap(string memory _key, string memory _position, uint256 _value ) public {
        nestedMap[_key][_position] = _value;
    }

    function fetchNestedMapValue(string memory _key, string memory _position) public view returns (uint256) {
        return nestedMap[_key][_position];
    }

    function deleteNestedMapValue(string memory _key, string memory _position) public  {
        delete nestedMap[_key][_position];
    }
}
```
