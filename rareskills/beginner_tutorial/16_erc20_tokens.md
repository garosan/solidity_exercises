# ERC20 Tokens

ERC20 tokens typically have a name and a symbol. For example, ApeCoin has the name “ApeCoin” but the symbol “APE.” The name of the token generally doesn’t change, so we’ll set it in the constructor and not provide any functions to change it later. We’ll make these variables public so that anyone can check the name and symbol of the contract.

We also need to store everyone’s balances.

Code so far:

```solidity
contract ERC20 {
    string public name;
    string public symbol;

    mapping(address => uint256) public balanceOf;

    constructor(string memory _name, string memory _symbol) {
        name = _name;
        symbol = _symbol;
    }
}
```

[Original Article](https://www.rareskills.io/learn-solidity/erc20-tuotrial)
