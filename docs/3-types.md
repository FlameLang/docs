# Types

Flame types are [sets](https://en.wikipedia.org/wiki/Set_(mathematics)) whose elements are values. 

## Built-in Types

These are the built-in language types:

| Type     | Represents                                                                              | Examples                |
| -------- | --------------------------------------------------------------------------------------- | ----------------------- |
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

## Declaring Types

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

To create a function type we write `(Type, Type, ... ) -> Type`:

```flame
Summation (Int, Int) -> Int
ToString () -> String
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

## Type Expressions

TODO
