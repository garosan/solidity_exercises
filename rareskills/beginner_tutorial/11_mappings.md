# Mappings

Mapping, Hashmap, maps, whatever you want to call it, Solidity has it.

Example:

```solidity
contract ExampleContract {

    mapping(uint256 => uint256) public myMapping;

    function setMapping(uint256 key, uint256 value)
        public {
            myMapping[key] = value;
    }

    function getValue(uint256 key)
        public
        view
        returns (uint256) {
            return myMapping[key];
    }
}
```

**If you access a mapping with a key that has not been set, you will NOT get a revert. The mapping will just return the “zero value” of the datatype for the value.**

In the following example, the mapping will return false if you supply a number that hasn’t been set.

```solidity
contract ExampleContract {
    // returns false by default
    mapping(uint256 => bool) public mapToBool;

    // returns 0 by default
    mapping(uint256 => uint256) public mapToUint;

    // returns 0x0000000000000000000000000000000000000000 by default
    mapping(uint256 => address) public mapToAddress;

}
```

By the way, ERC20 tokens use mappings to store how many tokens someone has! They map an address to how many tokens someone owns.

```solidity
contract ERC20Token {

    mapping(address => uint256) public balances;

    function setSomeonesBalance(address owner, uint256 amount)
        public {
            balances[owner] = amount;
    }

    function transferTokensBetweenAddresses(
            address sender,
            address receiver,
            uint256 amount)
        public {
            balances[sender] -= amount;   // deduct/debit the sender's balance
            balances[receiver] += amount; // credit the reciever's balance
    }
}
```

This implementation has a flaw that anyone can invoke the public functions and send tokens between addresses willy-nilly, but don't mind that for now.

**ERC20 tokens are not stored in cryptocurrency wallets, they are simply a uint256 associated with your address in a smart contract. “ERC20 tokens” are simply a smart contract.**

[This](https://etherscan.io/token/0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48) is the smart contract for USDC, an ERC20 token.

And [this](https://etherscan.io/token/0x4d224452801aced8b2f0aebe155379bb5d594381) is the token for ApeCoin, the currency of the Bored Ape Yacht Club ecosystem.

### Surprise 1: Mappings can only be declared as storage, you cannot declare them inside a function

This may seem like a very odd restriction, but this has to do with how the Ethereum Virtual machine works. Blockchains in general don’t like hashmaps because of their unpredictable runtime.

### Surprise 2: Mappings cannot be iterated over

### Surprise 3: Mappings cannot be returned

Maps are not a valid return type for solidity functions.

[Original Article](https://www.rareskills.io/learn-solidity/mapping)
