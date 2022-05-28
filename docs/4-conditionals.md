# Conditionals

A conditional is an expression that returns a value based on one or more boolean conditions:

```flame
status = if rate > 100 { "high" } else { "low" }
```

You don't need an `else` block to have a valid conditional expression:

```flame
result = if false { "unreachable!" }
```

Above, `result` will be set to the empty value `nil` since the condition evaluates to `false`.

Additionally, a `nil` condition is treated as `false`.

Conditionals can be chained:

```flame
if condition1 {
    result1
} else if condition2 {
    result2
} else if condition3 {
    result3
} else {
    result4
}
```
