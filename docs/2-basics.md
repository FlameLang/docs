# Basics

## Constants

To declare a constant we write `name: value`. For example:

```flame
pi: 3.1415
```

We can now use `pi` whenever we would like to use `3.1415`.

Constants can never be reassigned.

## Variables

To declare a variable we write `name Type = value` where the `= value` part is optional. For example:

```flame
quote String = "Not all those who wander are lost."
```

The type of a variable determines what values can be assigned to it.
Above, we declared `quote` to be of type [`String`](https://en.wikipedia.org/wiki/String_(computer_science)).
We can assign a new value to `quote`, as long as it is also of type `String`:

```flame
quote = "There is nothing permanent except change."
```

Let's declare a variable without specifying a value:

```flame
count Int
```

We declared `count` to be of type `Int` (as in [integer](https://en.wikipedia.org/wiki/Integer)), but we didn't assign it a value.
If we try to use `count` before assigning it a value, we will get an error.
When we do assign a value to `count`, it will have to be of type `Int`.

:::important
Once a variable is declared its type can never be changed.
:::

Let's create a variable of type `Any`:

```flame
joker Any
```

That means `joker` can hold a value of any type. For example, we can assign it a `String`, or and `Int`:

```flame
joker = "king"
joker = 7
```

## Types

Flame types are like [sets](https://en.wikipedia.org/wiki/Set_(mathematics)), and values are like set elements.
A type is just a collection, finite or infinite, of possible values.

When we declare a variable to be of a type we are specifying that the variable can only hold values that exist in the set determined by that type.
That's why we don't specify a type when declaring a constant - a constant can only ever hold one value.
The type of a constant would be analogous to a set with one element - its value.

Since values can satisfy multiple types (e.g. `12` is both of type `Int` and of type `Any`), when we declare a variable we need to be explicit about what kinds of values we want to allow it to hold.

These are the built-in language types:

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
In fact, while variables always start with a lowercase letter (or underscore), types always start with an uppercase letter.
Symbols, on the other hand, use exclusively uppercase letters.

### Type expressions

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
