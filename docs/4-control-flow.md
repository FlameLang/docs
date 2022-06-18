# Control Flow

## Conditionals

A conditional is an expression that, based on one or more boolean conditions, executes some code and returns a value.

```flame
rate 120
status if rate > 100 { "high" } else { "low" }
```

Above, `status` will be set to "high".

An `else` block is not required for a conditional expression to be valid:

```flame
message if rate < 10 { "caution!" }
```

Above, `message` will be set to the empty value `nil` since the condition evaluates to `false` and there is no `else` block.

Additionally, a `nil` condition is treated as `false`.

The result of a conditional doesn't have to be bound or assigned, and conditionals can be chained:

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

## Loops

There are four types of loops in Flame.
All of them support the keywords `stop` and `skip`.

* `stop` stops the execution of the loop (equivalent to `break` in some other languages).
* `skip` skips the current iteration of the loop and goes straight to the next (equivalent to `continue` in some other languages).

### Loop

A loop that repeats forever or until a `stop`:

```flame
loop { ... }
```

### While

In a `while` loop, first the condition is evaluated and, if it is `true`, the code block is executed.
The loop repeats while the condition evaluates to `true`.

```flame
while <condition> { ... }
```

### Until

In a `until` loop, first the code block is executed and then the condition is evaluated.
The loop repeats until the condition evaluates to `true`.

```flame
until <condition> { ... }
```

### For-in

A loop that calls `next()` on an iterator (`Iter`)

```flame
for <value> in <iterator> { ... }
```

To loop over an array:

```flame
numbers [10, 20, 30]
for x in numbers {
    print(x)
}
```

Ranges:

```
for i in 0..10 { ... }  # doesn't include 10
for i in 0..=10 { ... } # includes 10
```

## Pattern Matching

Pattern matching is a powerful way to check multiple conditions in sequence.

```flame
intSize getSomeInt() ~ {
    1 => "small",
    2 | 3 | 4 => "medium",
    5..100 => "large",
    _ => "huge",
}
```

### Single match branch

```flame
if num ~ 1..100 { ... }
```

### Matching function arguments

It's common to want to match a function's arguments. Instead of writing

```flame
someFunc (a: Int, b: Float) -> {
    (a, b) ~ {
        # match body
    }
}
```

You can use a "match arrow" `~>` to write:

```flame
someFunc (a: Int, b: Float) ~> {
    # match body
}
```

This is very useful for functional-style programming e.g.:

```flame
maximum (list: [T Any]) ~> T! {
    [] => error("list is empty"),
    [x] => x,
    [x, ..tail] => max(x, maximum(tail))
}
```

## Propagation of Optionals and Results

When calling a function that returns an optional `Type?` from inside a function that also returns an optional, we can append a trailing question mark to indicate that a `nil` should be propagated upwards. That is, if the inner function returns `nil`, the outer function will immediately return `nil` as well:

```flame
outer () -> TypeA? {
    # ...
    inner()?
    # ...
}
inner () -> TypeB? { ... }
```

A similar propagation of `Err`s happens to nested functions that return a result `Type!`:

```flame
outer () -> TypeA! {
    # ...
    inner()?
    # ...
}
inner () -> TypeB! { ... }
```

To return a result when an inner function returns an optional we can write:

```flame
outer () -> Type! {
    return inner() | error(...)
}
inner () -> Type? { ... }
```

To return an optional when an inner function returns a result we can write:

```flame
outer () -> Type? {
    res inner()
    if res ~ Err {
        return nil
    }
    return res
}
inner () -> Type! { ... }
```
