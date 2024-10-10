# Constructor

In a previous code example, we did something a little weird, we set the banker variable directly in the contract:

```solidity
contract ERC20 {
    address public banker = 0x5B38Da6a701c568545dCfcB03FcB875f56beddC4;

    mapping(address => uint256) public balances;
    // ... rest of code
}
```

What if someone wants to deploy the contract and set themselves to be the banker? How could they achieve this?

Smart contracts have a special function that is called at deployment time called the constructor:

```solidity
contract ExampleContract {

    address public banker;

    constructor() {
        deployer = msg.sender;
    }
}
```

Note that we don’t specify `public` because **constructors can’t be modified with things like pure, view, public**.

If you wanted the banker to be configured by the person deploying the contract, then you could use it as a function argument.

```solidity
contract ExampleContract {

    address public banker;

    constructor(address _banker) {
        banker = _banker;
    }
}
```

You’ll see this pattern `variable = _variable` a lot in constructors. Solidity doesn’t require you to do that, but it's a convention.

For reasons we cannot get into right now, `calldata` cannot be used in constructor arguments. I know, it seems like a very weird and random restriction, but it will make sense later, after you understand how Ethereum works under the hood.

Again, **if you want to pass a string or an array to the constructor function, you need to use `memory` or `storage`**.

```solidity
contract ExampleContract {
    string public name;

    // if you use calldata, it won't compile
    constructor(string memory _name) {
        name = _name;
    }
}
```

But, preguntándole a chatGPT me aclara esto: **The `calldata` keyword cannot be used in constructors or state variables. You need to use either `memory` or `storage`**.

Again, in this case, `memory` would be the most appropriate, but `storage` will also compile.

Also, in case you were wondering, constructors cannot return values.

[Original Article](https://www.rareskills.io/learn-solidity/constructor)
