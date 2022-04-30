# Basics

## Variables

Let's create a variable and assign it a value:

```flame
universe = 42
```

Variables have types. Since we didn't specify one in the snippet above, the type of `universe` is `Any`.
That means `universe` can hold a value of any type.
For example, we can assign it a value of type `String`:

```flame
universe = "Thanks for all the fish!"
```

If we want, we can specify a type explicitly when creating a variable:

```flame
galaxy: Int = 10
```

`galaxy` has type `Int` (as in [integer](https://en.wikipedia.org/wiki/Integer)).
If we try assigning `galaxy` a value of any type other than `Int` we get an error:

```flame
galaxy = "brain" # error!
```

:::important
Once a variable is created its type can never be changed.
:::

It's possible to create a variable with the type of the value we are assigning, whatever it may be:

```flame
pi := 3.1415
```

`pi` has type `Float` (as in a [floating point](https://en.wikipedia.org/wiki/Floating-point_arithmetic) number).

Sometimes we need to declare a variable without assigning it a value yet. We can do that with:

```flame
name: String
```

If we try to use `name` before assigning it a value, we will get an error.
When we do assign a value to `name` it will have to be of type `String`.

To summarize, the four ways to create a variable are

| Syntax       | Value         | Type             |
| ------------ | :-----------: | :--------------: |
| `a = 1`      | `1`           | `Any`            |
| `b := 1`     | `1`           | `Int` (inferred) |
| `c: Int = 1` | `1`           | `Int` (explicit) |
| `d: Int`     | uninitialized | `Int`            |

## Types and Constants

Flame is a gradually-typed language.
That means you can use types as little or as much as you like.
For example, you can quickly prototype without types and then add them to increase robustness and safety as ideas solidify.

As we'll see later, types allow you to create some abstractions that are fundamental to developing robust applications.
Types also help your code interface with external libraries, and help you communicate with other developers.
In the future they may even help with performance!

These are the built-in types:

| Type     | Note                                                                           |
| -------- | ------------------------------------------------------------------------------ |
| `Bool`   | `true` or `false`                                                              |
| `Int`    | 64-bit integer                                                                 |
| `Float`  | 64-bit floating point number                                                   |
| `Char`   | [unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) |
| `String` | sequence of characters                                                         |

As you may have noticed, the names of all types we've seen so far are capitalized.
In fact what distinguishes a type from a variable is capitalization.

### All values are types

In Flame, there is a very important concept which is that all values are also types.

For example, the number `1` can be used as a type:

```flame
one: 1
```
:::important
When a variable is declared with a value as a type then it is also initialized with that value, since there is no other value that could ever be assigned to it.
:::

`one` can only ever be assigned `1`, which wouldn't change its value. Therefore `one` is a **constant**.

Let's declare a constant for [Pi](https://en.wikipedia.org/wiki/Pi):

```flame
pi: 3.1415
```

### Type expressions

We can create type expressions.

Say we want a variable that can only ever be assigned `1` or `2`. We can declare it like so:

```flame
oneOrTwo: 1 | 2
```

We'll see how to create more advanced types later.

## Operators

The standard number operations include addition, subtraction, multiplication, and division:

```flame
add = 1 + 2   # 3
sub = 25 - 17 # 8
mul = 3 * 7   # 21
div = 12 / 3  # 4
```

The equality and inequality operators return a value of type `Bool` - either `true` or `false`. In the example below, every expression returns `true`.

```flame
"hi" == "hi" # equals
10 != "cat"  # not equals
15 < 20      # less than
4 <= 5       # less than or equal to
10 > 2       # greater than
99 >= 99     # greater than or equal to
```

Boolean operators

```flame
true & false # false
true | false # true
!true        # false
```
