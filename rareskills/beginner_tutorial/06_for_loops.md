# For Loops

Just like if statements, there is nothing surprising about for loops.

Here is the code to add up all the numbers from 1 to 99

```solidity
contract ExampleContract {
    function addNumbers()
        public
        pure
        returns (uint256) {
            uint256 sum = 0;
            for (uint256 i = 0; i < 100; i++) {
                sum += i;
            }
            return sum;
    }
}
```

A very natural use-case for for loops is iterating over an array. But we haven’t introduced arrays yet, so we’ll explain it at that point.

Like other languages, you can do an early return from a function inside a for loop. This code will loop from 2 to the number until it finds a prime factor.
