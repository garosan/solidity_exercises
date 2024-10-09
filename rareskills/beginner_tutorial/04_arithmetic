# Arithmetic

Arithmetic in Solidity behaves exactly the same as in other languages, so we won’t belabor the point here.

You can add numbers:

```solidity
uint256 sum = 10 + 5; // sum == 15
```

Exponents are the same as in other C-like languages.

```solidity
uint256 exp = 2 ** 3; // exp == 8
```

And so is the modulus:

```solidity
uint256 remainder = 10 % 4; // remainder == 2
```

Subtracting, multiplying, and dividing are obvious, so this guy won't insult our intelligence by teaching us that xD.

### Solidity does not have floats

If you try to divide 5 by 2, you won't get 2.5. You’ll get 2. Remember, uint256 is an unsigned Integer. So any division you do is integer division.

What if you wanted to calculate the 10% of 200?

```solidity
uint256 interest = 200 * 0.1; // fails, 0.1 is not valid
```

The solution to this is to convert x 0.1 into x 1 / 10. This is valid and will produce the correct answer.

```solidity
uint256 interest = 200 / 10;
```

If your interest was some amount like 7.5%, then you would need to do the following:

```solidity
uint256 interest = 200 * 75 / 1000;
```

If you wanted to know the percentage population of a city relative to a nation, you cannot do the following.

```solidity
uint256 cityPopulation = 1000;
uint256 nationPopulation = 10000;

uint256 fractionOfPopulation = cityPopulation / nationPopulation;
//fractionOfPopulation is zero!
```

This requires a more advanced solution we will describe later.

Note: Why doesn’t solidity support floats? Floats are not always deterministic, and blockchains must be deterministic otherwise nodes won’t agree on the outcomes of transactions.

For example, if you divide 2/3, some computers will return 0.6666, and others 0.66667. This disagreement could cause the blockchain network to split up!

### Solidity does not underflow or overflow, it stops the execution

Consider this code:

```solidity
function subtract(uint256 x, uint256 y)
        public
        pure
        returns (uint256) {
            uint256 difference = x - y;
            return difference;
}
```

What happens if x is 2 and y is 5? You won’t get negative 3. Actually, what happens is the execution will halt with a revert.

Solidity doesn’t throw exceptions, but you can think of a revert as the equivalent of an uncaught exception.

It used to be the case Solidity would allow overflows and underflows, but this led to enough smart contracts breaking or getting hacked that the language built overflow and underflow protection into the language. This feature was added after Solidity version 0.8.0.

### If you want to allow underflow and overflow, you need to use an unchecked block

You can use an unchecked block to allow underflow and overflow. This is not recommended unless you have a very good reason to do so. An unchecked block can be used like this:

```
uint256 x = 1;
uint256 y = 2;

unchecked {
    uint256 z = x - y; // z == 2**256 - 1
}
```

Note that anything inside the unchecked block will not revert even if it overflows or underflows. **This is a very advanced feature that you should not use unless you know what you are doing.**

[Original Article](https://www.rareskills.io/learn-solidity/arithmetic)
