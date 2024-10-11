# Solidity Coding Standards

There is an [official Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html).

This article covers common deviations from the style guide and some others are not in the style guide, but are common stylistic developer mistakes.

## First Two Lines

- Always include the SPDX-License-Identifier, just do it man.

- Fix your solidity pragma unless you're writing a library:

If you are the one compiling and deploying a contract use a fixed version:

```solidity
pragma solidity 0.8.21;
```

If you are OpenZepellin or Solady and writing a library for other people to use, you don't know which compiler version the end user will be using so do:

```solidity
pragma solidity ^0.8.0;
```

## Imports

Set the library version in the import statement. This way you can prevent unexpected changes that might occur when the library is updated.

Don't do this:

```solidity
import "@openzepplin/contracts/token/ERC20/ERC20.sol";
```

Do this instead:

```solidity
import "@openzeppelin/contracts@4.9.3/token/ERC20/ERC20.sol";
```

You can find the latest version of a library by clicking the branch dropdown on the left side of their repo in Github and clicking tags, then picking the latest release. Use the latest clean (non-rc, i.e. non-release-candidate) version.

### 4. Use named imports instead of importing the entire namespace

Don't do this:

```solidity
import "@openzeppelin/contracts@4.9.3/token/ERC20/ERC20.sol";
```

Do this instead:

```solidity
import {ERC20} from "@openzeppelin/contracts@4.9.3/token/ERC20/ERC20.sol";
```

### 5. Delete unused imports

If you use a smart contract security tool like Slither, this will be caught automatically. But be sure to remove these. Don’t be afraid to delete code.

## Contract Level

### 6. Apply contract-level natspec

The point of natspec (natural language specification) is to provide an easily human-readable inline documentation.

Example:

```solidity
/// @title Liquidity token for Foo protocol
/// @author Foo Incorporated
/// @notice Notes for non-technical readers/
/// @dev Notes for people who understand Solidity
contract LiquidityToken {

}
```

### 7. Lay out the contract structure per the style guide

The functions should be sorted by “externality” first then “state-changingness” second.

They should be ordered as follows:

1. receive and fallback functions (if applicable)
2. external functions
3. public functions
4. internal functions
5. private functions

Within those groups, the payable functions go on top, then non-payable, then view, then pure.

## Constants

### 8. Replace magic numbers with constants

If you see the number 100 just sitting in the code, what is it? 100 percent? 100 basis points?

Generally, numbers should be written as a constant at the top of the contract.

### 9. If numbers are used to measure ether or time, use the solidity keywords

Don't do this:

```solidity
require(msg.value == 10**18 / 10, "must send 0.1 ether");
```

Do this instead:

```solidity
require(msg.value == 0.1 ether, "must send 0.1 ether");
```

### 10. Use underscores to make large numbers more readable

```solidity
// Instead of:
10000
// write:
10_000
```

## Functions

### 11. Remove the virtual modifier from functions that will not be overridden

The virtual modifier means “overridable by a child contract.” But if you know you will not be overriding the function (because you are the deployer), then this modifier is superfluous. Just delete it.

Example of virtual modifier:

```solidity
// Parent contract
pragma solidity ^0.8.0;

contract Parent {
    // This function can be overridden by child contracts because it's marked as `virtual`
    function greet() public virtual returns (string memory) {
        return "Hello from Parent";
    }
}

// Child contract
contract Child is Parent {
    // This overrides the greet() function from the Parent contract
    function greet() public override returns (string memory) {
        return "Hello from Child";
    }
}
```

### 12. Put function modifiers in the correct order visibility, mutability, virtual, override custom modifier

The following is correct

```solidity
// visibility (payability), [virtual], [override], [custom]
function foo() public payable onlyAdmin {

}


function bar() internal view virtual override onlyAdmin {

}
```

## General cleanliness

### 14. Remove commented out code

Self-explanatory.

### 15. Give variables descriptive and useful names

- Don’t use two different nouns to apply to the same real-world entity. For example, if “depositor” and “liquidityProvider” refer to the same entity in the real world, just stick to one term, don’t use both in the code.
- Include units in variable names. Instead of “interestRate” do “interestRatesBasisPoints” or “feeInWei”.
- State changing functions should have a verb in the name.
- using “get” for viewing data and “set” for changing data is a widely followed programming convention. Consider incorporating it.

## Additional Tricks for organizing large codebases

- If you have a lot of storage variables, you can define all the storage variables in a single contract, then inherit from that contract to gain access to those storage variables.

- If your functions require a significant amount of parameters, use a struct to pass the information around.

- If you need a lot of imports, you can import all the files and types into one solidity file, then import that file (you would need to intentionally break the rule about named imports).

- Use libraries to group functions of the same category together and make files smaller.

- Study codebases of large established projects.

[Original Article](https://www.rareskills.io/post/solidity-style-guide)
