# Confidential Contract

## Overview

Welcome to the Confidential Contract, a Solidity smart contract designed to manage a confidential value and a private text string on the Ethereum blockchain. This contract features functions for setting and retrieving the confidential value, incorporating specific constraints to ensure the security and controlled access of sensitive information.

## Key Features

### Set Confidential Value

The `setConfidentialValue` function empowers users to modify the confidential value. Notably, this function enforces a constraint allowing only even numbers or the specific value of 35 to be assigned.

```solidity
function setConfidentialValue(uint NEW_key) public {
    require(NEW_key % 2 == 0 || NEW_key == 35, "Only even numbers or 35 are allowed");
    confidentialValue = NEW_key;
}
```

### Retrieve Confidential Value

The `getConfidentialValue` function provides a secure way to retrieve the current confidential value. An `assert` statement safeguards against unexpected scenarios, ensuring the value is non-zero.

```solidity
function getConfidentialValue() public view returns (uint) {
    assert(confidentialValue != 0);
    return confidentialValue;
}
```

### Reveal Private Text

For those meeting specific conditions, the `revealPrivateText` function allows access to a private text string. This condition mandates that the confidential value must be precisely equal to 35. If not met, a `revert` statement is triggered.

```solidity
function revealPrivateText() public view returns (string memory) {
    if (confidentialValue != 35) {
        revert("Confidential value is not the expected value");
    }
    return privateText;
}
```

## License

This smart contract operates under the MIT License. Refer to the SPDX-License-Identifier in the source code for comprehensive details.

```solidity
// SPDX-License-Identifier: MIT
```
