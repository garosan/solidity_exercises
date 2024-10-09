# Nested Arrays

Nested arrays are extremely rare in practice. If you feel like skipping this section, feel free to.

Let's look at an example here:

```solidity
contract ExampleContract {

    function containsAThree(uint256[][] calldata nestedArray)
        public
        pure
        returns (bool) {
            for (uint256 i = 0; i < nestedArray.length; i++) {
                for (uint256 j = 0; j < nestedArray[i].length; j++) {
                    if (nestedArray[i][j] == 3) {
                        return true;
                    }
                }
            }
            return false;
    }
}
```

You can declare nested arrays of fixed size:

```solidity
contract ExampleContract {

    // ACCEPTED: [[1,2],[3,4],[5,6]] -> returns 6
    function getLast(uint256[2][3] calldata nestedArray)
        public
        pure
        returns (uint256) {
            return nestedArray[2][1];

            // nestedArray[2] -> [5,6] then get the 1st index item -> 6
    }
}
```

[Original Article](https://www.rareskills.io/learn-solidity/nested-arrays)
