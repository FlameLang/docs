# Ideas To Explore

## Refinement Types

It would be nice to allow defining refinement types.
For example, defining a type for all prime numbers starting from integers.
One idea is to define a type based on a function over another type e.g.:

```flame
Prime isPrime(Int)
```

`Prime` would represent all integers `i` that satisfy `isPrime(i) == true`.

## Units

It would be nice to allow math with quantities that have associated units, and allow users to define their own units.

## Concise Lambda Notation

Simple functions could be created concisely using $-notation.

Using $ as a term inside an expression creates a single-expression function that takes a single parameter:

```flame
# These are equivalent:
addOne (a) -> a + 1
addOne $ + 1
```
