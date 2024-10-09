# If Statements

If statements behave exactly the same as other languages. But, unlike in dynamic languages such as Python or JavaScript, you cannot do the following:

```
function isNotZero(uint256 x)
    public
    pure
    returns (bool) {
        if (x) {
            return true;
        } else {
            return false;
        }
}
```

Solidity does not have a switch statement.

[Original Article](https://www.rareskills.io/learn-solidity/if-statements)
