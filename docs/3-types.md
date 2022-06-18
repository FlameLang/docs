# Types

Flame types are [sets](https://en.wikipedia.org/wiki/Set_(mathematics)) whose elements are values. 

## Built-in Types

These are the built-in language types:

| Type     | Represents                                                                              | Examples                |
| -------- | --------------------------------------------------------------------------------------- | ----------------------- |
| `Nil`    | The lack of a value                                                                     | only `nil`              |
| `Bool`   | [boolean](https://en.wikipedia.org/wiki/Boolean_data_type)                              | `true` or `false`       |
| `Int`    | 64-bit integer                                                                          | `1`, `2`, `32`, `122`   |
| `Float`  | 64-bit [floating point](https://en.wikipedia.org/wiki/Floating-point_arithmetic) number | `64.5`, `32.9`          |
| `Char`   | [unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value)          | `'a'`, `'z'`            |
| `String` | sequence of characters                                                                  | `"Pharaoh"`, `"Beagle"` |
| `Symbol` | immutable [interned](https://en.wikipedia.org/wiki/Interning_(computer_science)) string | `RED`, `EVENT`, `NAME`  |

As you may have noticed, all types above are capitalized.
That's not an accident.
In fact, while constants and variables always start with a lowercase letter, types always start with an uppercase letter.
Symbols, on the other hand, use exclusively uppercase letters.

## Declaring New Types

To declare a type we write `Name Type`:

```flame
StatusCode Int
```

To create a list type we surround the list's element type with square brackets:

```flame
Numbers [Int]
Messages [String]
```

To create an object type we specify its properties' names and types inside parentheses:

```flame
Person (
    name String
    age Int
)
```

To create a function type we specify the types of the arguments (in order) and the returned type:

```flame
Summation (Int, Int) -> Int
ToString () -> String
Effect () -> Nil
```

Here is an example of a complex type:

```flame
EventList (
    events [(
        eventCode Int
        eventMessage String
    )]
    lastEventCode () -> Int
)
```

## Methods

A method is a function that can be called on any instance of a type.
Inside a method's body we can access the instance via `&`.
For example:

```flame
Vec2.sum (other Vec2) -> {
    &.x += other.x
    &.y += other.y
}
EventList.clear () -> {
    &.events = []
}
```

We can then call the methods:

```flame
someVec2.sum((x: 1, y: 5))
someEventList.clear()
```

## Type Unions

A type union is a combination of two or more types.
We can denote a type union by using `|` between types. A type of `A|B` means “any value which is either an A or a B (or both)”.

To illustrate, let's declare a type that is either a `String` or a `Bool`:

```flame
StringOrBool String|Bool
```

You can also use values in type unions.
Here are more examples of type unions:

```flame
DiceRoll 1|2|3|4|5|6
Num Int|Float
Crud CREATE|READ|UPDATE|DELETE 
```

## Type Intersections

A type intersection is a combination of two or more object types.
We can denote a type intersection by using `+` between types. A type of `A+B` means “any value which satisfies both A and B”.

For example let's say we have the following types:

```flame
Named (name String)
Position (x Int, y Int)
```

We can declare a new intersection type `NamedPosition` like so:

```flame
NamedPosition Named+Position
```

And use it like this:

```flame
north NamedPosition(name: "North", x: 0, y: 10)
```

## Optionals

An optional is a type union between some type and `nil`.
Flame has a shorthand for optionals - simply append a `?` at the end of a type:

```flame
OptionalInt Int? # equivalent to Int|nil
OptionalString String? # equivalent to String|nil
```

## Results

A result is a type union between some type and `Err`, where `Err` is the type of all Flame errors:

```flame
Err (err String)
```

Flame has a shorthand for results - simply append a `!` at the end of a type:

```flame
IntOrErr Int! # equivalent to Int|Err
StringOrErr String! # equivalent to String|Err
```
