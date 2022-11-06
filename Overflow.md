```solidity
contract Overflow {
    // the upper limit of the variable value would be (2 ** 8) - 1 which is 255;
    // prior to solidity version ^0.8.0 - ^0.6.0, variables like uint and int were unchecked
    // this meant that when the variable value in this example would exceed its upper limit, it would reset to 0
    // in versions ^0.8.0 value would remain at 255
    uint8 public value = 255;

    function add() public {
        // value += 1;
        // to get back the original unchecked functionality, you wrap the calculation in unchecked {**calculation**}
        unchecked {value = value + 1;}
        /** a potential application of this would be saving gas when you are sure that the value
            wont pass the upper or lower limits of the data type **/
    }
}

```
