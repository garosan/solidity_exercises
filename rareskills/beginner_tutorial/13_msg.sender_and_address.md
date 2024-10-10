# msg.sender and address(this)

Remember our previous example of a bad ERC20 token?

The issue was that we have no idea who is calling the function.

Luckily, Solidity has a mechanism to identify who is calling the smart contract: `msg.sender`.
`msg.sender` returns the address of who is invoking the smart contract function.

The following code will return the address that called the contract:

```solidity
contract ExampleContract {
    function whoami()
        public
        view
        returns (address) {
            address sender = msg.sender;
            return sender;
    }
}
```

By combining msg.sender with an if statement, you can give certain addresses special privileges.

### tx.origin

There is another mechanism to get the sender, `tx.origin`, but you should not use it. We won’t explain the security issues around `tx.origin` yet, but the point is, don't use it unless you understand exactly what it does and its security issues.

### address(this)

A smart contract can know its own address with the following code

```solidity
contract ExampleContract {

    function whoami()
        public
        view
        returns (address) {
            return address(this);
    }
}
```

[Original Article](https://www.rareskills.io/learn-solidity/msg-sender-address-this)
