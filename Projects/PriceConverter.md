```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.12;

import "@chainlink/contracts/src/v0.8/interfaces/AggregatorV3Interface.sol";

library PriceConverter {

    // Get price feed version
    function getFeedVersion() internal view returns (uint256) {
        AggregatorV3Interface priceFeed =
        AggregatorV3Interface(0xD4a33860578De61DBAbDc8BFdb98FD742fA7028e);
        return priceFeed.version();
    }

    // Get Eth Price in USD
    function getETHPrice() internal view returns (uint256) {
        AggregatorV3Interface priceFeed =
        AggregatorV3Interface(0xD4a33860578De61DBAbDc8BFdb98FD742fA7028e);
        (, int256 price, , , ) = priceFeed.latestRoundData();
        // this returns the eth value to 8 decimal places
        // to ensure that it matches the message value which is in wei (18 decimal places), multiply the value by 1e10
        return uint256(price * 1e10);
    }

    // Get Conversion Rate
    function getConversionRate(uint256 ethAmountInWei)
        internal
        view
        returns (uint256)
    {
        uint256 ethPrice = getETHPrice();
        uint256 ethAmountInUSD = (ethPrice * ethAmountInWei) / 1e18;
        return ethAmountInUSD;
    }
}
```
