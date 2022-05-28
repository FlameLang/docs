# Loops

There are four types of loops in Flame.
All of them support the keywords `stop` and `skip`.

* `stop` stops the execution of the loop (equivalent to `break` in some other languages).
* `skip` skips the current iteration of the loop and goes straight to the next (equivalent to `continue` in some other languages).

## Loop

An infinite loop that repeats forever or until a `stop`:

```flame
loop { ... }
```

## While

In a `while` loop, first the condition is evaluated and, if it is `true`, the code block is executed.
The loop repeats while the condition evaluates to `true`.

```flame
while <condition> { ... }
```

## Until

In a `until` loop, first the code block is executed and then the condition is evaluated.
The loop repeats until the condition evaluates to `true`.

```flame
until <condition> { ... }
```

## For-in

A loop that calls `next()` on an iterator (`Iter`)

```flame
for <value> in <iterator> { ... }
```

To loop over an array:

```flame
numbers = [10, 20, 30]
for x in numbers {
    print(x)
}
```

Ranges:

```
for i in 0..10 { ... }  # doesn't include 10
for i in 0..=10 { ... } # includes 10
```
