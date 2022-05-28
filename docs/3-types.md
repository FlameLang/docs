# Types

Flame is a gradually-typed language.
That means you can use types as little or as much as you like.
For example, you can quickly prototype without types and then add them to increase robustness and safety as ideas solidify.

As we'll see later, types allow you to create some abstractions that are fundamental to developing robust applications.
Types also help your code interface with external libraries, and help you communicate with other developers.
In the future they may even help with performance!

These are the built-in types:

| Type     | Represents                                                                              | Examples
| -------- | --------------------------------------------------------------------------------------- | ----------------
| `Bool`   | [boolean](https://en.wikipedia.org/wiki/Boolean_data_type)                              | `true` or `false` 
| `Int`    | 64-bit integer                                                                          | `1`, `2`, `32`, `122`
| `Float`  | 64-bit [floating point](https://en.wikipedia.org/wiki/Floating-point_arithmetic) number | `64.5`, `32.9`
| `Char`   | character ([unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value)) | `'a'`, `'z'`
| `String` | sequence of characters                                                                  | `"Pharaoh"`, `"Beagle"`
| `Symbol` | immutable [interned](https://en.wikipedia.org/wiki/Interning_(computer_science)) string | `RED`, `EVENT`, `NAME`

As you may have noticed, all types above are capitalized.
That's not an accident.
In fact, while variables always start with a lowercase letter, types always start with an uppercase letter.
Symbols, on the other hand, use exclusively uppercase letters.

## Values are types

In Flame, there is a very important concept which is that all values are also types.

If you are into set theory, Flame types are like sets and values are like set elements. A value type is analogous to a set with one element.

For example, the integer value `1` can be used as a type when creating a variable:

```flame
one 1
```

:::important
When a variable is declared with a value as a type it is automatically initialized with that value, and it cannot be assigned or reassigned.
:::

Variables with value types, like `one` above, are **constants**.

Let's declare a constant for [pi](https://en.wikipedia.org/wiki/Pi):

```flame
pi 3.1415
```

Let's declare some constants of other types:

```flame
emoji 🔥
eventType UPDATE
greeting "Howdy!"
```

## Type unions

A type union is a combination of two or more types.

To illustrate, let's create a variable that can only ever be assigned `1` or `2`:

```flame
oneOrTwo 1|2 = 1
```

`1|2` is a *type union*.

Here are more examples of type unions:

```flame
hiOrAge "hi"|Int = 32
number Int|Float = 1.2
event CREATE|READ|UPDATE|DELETE = READ
```

Let's declare the types we used above:

```flame
HiOrInt "hi"|Int
Num Int|Float
Crud CREATE|READ|UPDATE|DELETE 
```

Note how they are all capitalized. That's what differentiates the above from variable declarations.
Let's use the types we created:

```flame
hiOrAge HiOrInt = 32
number Num = 1.2
event Crud = READ
```

## Values are of multiple types

The value `10` is of type `Int`. It is also of type `Any`.
To say that a value "is of a type" means that the value is inside the "set" defined by that type.

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
