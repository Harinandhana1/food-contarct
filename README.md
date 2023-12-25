# Food Purchase 

## Overview

The Food Purchase Contract is a Solidity smart contract designed for facilitating food purchases from a restaurant. It ensures that buyers send the correct amount of Ether, prevents the restaurant from purchasing its own food, and enforces certain rules on the minimum and maximum order amounts.

## Smart Contract Details

### State Variables

- **restaurant**: The address of the restaurant that offers the food.
- **orderAmount**: A mapping from buyer addresses to the total amount they have ordered.

### Events

- **FoodPurchased**: Triggered when a buyer successfully purchases food, providing information about the buyer's address and the purchased amount.

### Constructor

- **FoodPurchaseContract(address _restaurant)**: Initializes the contract with the address of the restaurant.

### Functions

- **purchaseFood(uint256 _amount)**: Allows buyers to purchase food by sending the correct amount of Ether. It checks that the buyer is not the restaurant, enforces a minimum purchase amount of 200, and restricts the maximum order per person to 1000. It updates the order amount for the buyer and emits an event upon successful purchase.

## Usage

1. Deploy the contract by providing the address of the restaurant as a parameter in the constructor.

```solidity
FoodPurchaseContract myContract = new FoodPurchaseContract(restaurantAddress);
```

2. Buyers can then call the `purchaseFood` function, specifying the desired amount of food to purchase. The function ensures that the buyer sends the correct amount of Ether, is not the restaurant, and adheres to the minimum and maximum order constraints.

```solidity
myContract.purchaseFood{value: msg.value}(orderAmount);
```

## License

This code is licensed under the MIT License. See the SPDX-License-Identifier in the source code for details.

