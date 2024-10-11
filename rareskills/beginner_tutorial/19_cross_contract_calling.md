# Calling other Contracts

Everything we’ve been doing up to this point is calling smart contracts directly. But it’s also possible, and in fact, desirable, for smart contracts to be able to communicate with each other.

See example:

```solidity
contract ExampleContract {
    function askTheMeaningOfLife(address source)
        public
        returns (uint256) {
            (bool ok, bytes memory result) = source.call(
                abi.encodeWithSignature("meaningOfLifeAndAllExistence()")
            );
            require(ok, "call failed");

            return abi.decode(result, (uint256));
    }
}

contract AnotherContract {
    function meaningOfLifeAndAllExistence()
        public
        pure
        returns (uint256) {
            return 42;
    }
}
```

[Original Article](https://www.rareskills.io/learn-solidity/cross-contract-call)
