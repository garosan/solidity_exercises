# Require

Just one more essential Solidity keyword, and then we are ready to create our own ERC20 token.

Although we could use an if statement or check who's calling a function for validation, the elegant way is to use the `require` statement. It forces the transaction to revert if some condition is not met.

Example code:

```solidity
contract ExampleContract {
    function mustNotBeFive(
        uint256 x
    )
        public
        pure
        returns (uint256) {
            require(x != 5, "five is not valid");
            return x * 2;
    }
}
```

What if you want to ensure that only the owner of the contract can make a specific change to it?

Example:

```solidity
contract OnlyOwner {

    address owner;
    uint256 public magicNumber;

    constructor(address _owner, uint256 _magicNumber) {
        owner = _owner;
        magicNumber = _magicNumber;
    }

    function updateMagicNumber(uint256 _number) public {
        require(owner == msg.sender, "Sender must be owner");
        magicNumber = _number;
    }
}
```

[Original Article](https://www.rareskills.io/learn-solidity/require)
