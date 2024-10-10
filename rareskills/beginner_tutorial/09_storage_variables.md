# Storage Variables

Up until now, our functions have just returned values that purely depend on the arguments. They don't depend on anything else than the immediate input, that's why they're called _pure_ functions. They are not aware of the blockchain state or anything that has happened in the past.

If we wanted to keep track of how much money is owed to someone or the points of someone in a game, we would fall short.

Now we introduce the **storage variable**.

Let’s look at an example and then analyze it:

```solidity
contract ExampleContract {

    uint256 internal x;

    function setX(
        uint256 newValue
    )
        public {
            x = newValue;
    }

    function getX()
        public
        view
        returns (uint256) {
            return x;
    }
}
```

**Variables declared outside of functions are storage variables. They keep their value after the transaction ends.**

Note that `getX()` has the modifier view instead of pure. That’s because it views the blockchain state, I.e. what is stored in the variable `x`. If you change `view` to `pure` in this example, the code will not compile. You can also think of `view` as read-only.

Second, note that `setX` does not have a `view` or a `pure` modifier. That’s because it is a state changing function. Functions that change storage variables, or make some other lasting change to the blockchain cannot have the `view` or `pure` modifier, this is because they are not read only and thus cannot be labelled as `view`, and certainly not `pure`.

Note that the variable `x` itself has the modifier `internal`. This means other smart contracts cannot see the value.

**Just because a variable is internal does not mean it is hidden. It’s still stored on the blockchain and anyone can parse the blockchain to get the value!**

The code will still compile if you don't set it to `internal` but it’s considered bad practice because you aren’t being explicit about your intentions for the visibility of `X`.

You could also use `public` instead of `internal`. When a variable is declared `public`, it means other smart contracts can read the value but not modify it.

Sounds confusing but remember: **public functions can modify variables, but public variables cannot be modified unless there is a function to change their value.**

Most important to remember:

- Storage variables are declared outside of functions
- Public functions that do not have a view or pure modifier can change storage variables
- Pure functions cannot access storage variables

[Original Article](https://www.rareskills.io/learn-solidity/storage-variables)
