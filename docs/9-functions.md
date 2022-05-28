# Functions

A function is created using the `() -> {}` notation. The parentheses are always necessary. If the function body is only a single expression then the braces can be omitted:

```flame
add = (a, b) -> a + b
```

If a function's body is a single expression, then it evaluates and returns that expression.
If the body of the function is a block then you can use explicit `return` statements.
If the last statement in the body block is an expression - then the function returns the result of that last expression.
If no explicit `return` is reached and the last statement isn't an expression, the function implicitly returns `nil`.
`() -> nil` is both the value and type of a function that takes no arguments and returns nothing.

## Concise `$`-notation

Simple functions can be created concisely using `$`-notation.

Using `$` as a term inside an expression creates a single-expression function that takes a single parameter:

```flame
# These are equivalent:
addOne = (a) -> a + 1
addOne = $ + 1
```

## Closures

You can easily create closures.

TODO.
