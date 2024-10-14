# ERC20 Tokens

ERC20 tokens typically have a name and a symbol. For example, ApeCoin has the name “ApeCoin” but the symbol “APE.” The name of the token generally doesn’t change, so we’ll set it in the constructor and not provide any functions to change it later. We’ll make these variables public so that anyone can check the name and symbol of the contract.

We also need to store everyone's balances.

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

We say “balanceOf” because that is part of the ERC20 specification. ERC20 as a specification means that people can call the function “balanceOf” on your contract, supply an address, and get how many tokens that address owns.

Everyone’s balance is zero right now, so we need a way to bring tokens into existence. We’ll allow a special address, the person who deployed the contract, to create tokens at will:

```solidity
contract ERC20 {
    string public name;
    string public symbol;

    mapping(address => uint256) public balanceOf;
    address public owner;

    constructor(string memory _name, string memory _symbol) {
        name = _name;
        symbol = _symbol;

        owner = msg.sender;
    }

    function mint(address to, uint256 amount) public {
        require(msg.sender == owner, "only owner can create tokens");
        balanceOf[owner] += amount;
    }
}
```

[Original Article](https://www.rareskills.io/learn-solidity/erc20-tuotrial)
