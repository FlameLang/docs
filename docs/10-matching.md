# Matching

Flame has a powerful construct called matching. It's similar to Rust's `match` statement.

```flame
num = 141 # Try other values!
result = num ~ {
    1 => "small",
    2 | 3 | 4 => "medium",
    5..100 => "large",
    _ => "other",
}
```


## Single match branch

if num ~ 1..100 { ... }


## Matching function arguments

It's common to match a function's arguments.

Instead of writing

```flame
func = (a: Int, b: Float) -> {
    (a, b) ~ {
        # match body
    }
}
```

Flame has a shorthand using `~>` instead of `->`:

```flame
func = (a: Int, b: Float) ~> {
    # match body
}
```

This is very useful for functional-style functions like:

```flame
maximum = (list: [Any]) ~> Any? {
    [] => ("),
    [x] => x,
    [x, ..tail] => max(x, maximum(tail))
}
```





v = v ~ { ... }
can be shortened to
v ~= { ... }



## Destructuring

TODO
