# Application Binary Interface Encoding (abi encoding)

We're gonna go on a tangent to explore the ABI.

We need to understand the following things:

- `abi.encode`
- `abi.decode`
- `abi.encodeWithSignature`

Create and deploy a random contract:

```solidity
contract ExampleContract {

    function meaningOfLifeAndAllExistence()
        public
        pure
        returns (uint256) {
            return 42;
    }
}
```

In the terminal of Remix, there is an `input` field that you can copy.

In my case I got:

`0x6080604052348015600e575f80fd5b5060af80601a5f395ff3fe6080604052348015600e575f80fd5b50600436106026575f3560e01c806392d62db514602a575b5f80fd5b60306044565b604051603b91906062565b60405180910390f35b5f602a905090565b5f819050919050565b605c81604c565b82525050565b5f60208201905060735f8301846055565b9291505056fea2646970667358221220c4d09de1dcf103bb95cb266e284bc78dcc0808d51e25db1f491809145ffe258564736f6c634300081a0033`

This is the **`function signature`** of my contract.

Whenever you _call_ a smart contract, you are actually sending an ethereum transaction with some data attached so the smart contract knows which function to execute.

Check this (don't worry about what _`bytes memory`_ and _`msg.data`_ mean for now):

```solidity
contract ExampleContract {

    function meaningOfLifeAndAllExistence()
        public
        pure
        returns (bytes memory) {
            return msg.data;
    }
}
```

//TODO: Run this through chatGPT, it's not being very clear.

https://www.rareskills.io/learn-solidity/abi

[Original Article](https://www.rareskills.io/learn-solidity/abi)
