# Tuples

We will introduce the tuple data type, because it is a prerequisite for upcoming sections.

The tuple is an array of fixed size, but the types inside of it can be a mixture.

Here’s an example of a function that returns a tuple:

```solidity
contract ExampleContract {

    function getTopLeaderboardScore()
        public
        pure
        returns (address, uint256) {
            return (
                0xd8da6bf26964af9d7eed9e03e53415d37aa96045,
                100
            );
    }
}
```

**Note that tuples are implied. The keyword 'tuple' never appears in Solidity.**

Tuples can also be 'unpacked' to get the variables inside, example:

```solidity
contract ExampleContract {

    function getTopLeaderboardScore()
        public
        pure
        returns (address, uint256) {
            return (
                0xd8da6bf26964af9d7eed9e03e53415d37aa96045,
                100
            );
    }

    function highestScoreIsOver9000()
        public
        pure
        returns (bool) {
            (address leader, uint256 score) =
                getTopLeaderboardScore();

            if (score > 9000) {
                return true;
            }

            return false;
    }
}
```

Can you spot exactly which line in the above code is doing the unpacking? For me, unpacking sounds a lot like the destructuring concept of JavaScript. Here, unpacking means taking the values that are inside of the tuple and assigning them to variables so that you can use those variables directly later in your code.

This is the exact line that achieves it:

```solidity
(address leader, uint256 score) = getTopLeaderboardScore();
```

[Original Article](https://www.rareskills.io/learn-solidity/tuples)
