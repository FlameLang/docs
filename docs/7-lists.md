# Lists

A list is an ordered, variable-size, finite collection of values:

```flame
emptyList = []
somePrimes = [1, 2, 3, 5, 7, 11]
random = [1, "hi", SYMBOL]
```

List elements can be accessed via indexing:

```flame
somePrimes[0] # The first element of `somePrimes`
random[2] = "cat" # Update the third element of `random`
```

To append an element to the end of a list use `push`:

```flame
random.push(🧙‍♂️)
```
