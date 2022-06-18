# Basics

## Constants

Constants are named values that can never be reassigned.
To declare a constant we write `name value`. For example:

```flame
pi 3.1415
```

We can now use `pi` wherever we would like to use `3.1415`.

## Variables

Variables are named values that can be reassigned.
Once a variable is declared its type can never be changed.

There are three ways to declare a variable in Flame.

1. Write `name Type` to specify the variable's type without assigning it a value:

    ```flame
    count Int
    ```

    If we try to use `count` before assigning it a value we will get an error.

2. Write `name Type = value` to specify the variable's type and also assign it an initial value:

    ```flame
    ready Bool = true
    ```

3. Write `name: value` to specify only an initial value and have Flame infer its type:

    ```flame
    quote: "Not all those who wander are lost."
    ```

    Above, `quote` took the type of the value we assigned to it, which in this case is [`String`](https://en.wikipedia.org/wiki/String_(computer_science)).

    We can assign a new value to `quote`, as long as it is also of type `String`:
        
    ```flame
    quote = "There is nothing permanent except change."
    ```

## Lists

A list is an ordered collection of values.
To create a list we use square brackets:

```flame
somePrimes [1, 2, 3, 5, 7, 11]
emptyList []
multi [1, "hi", SYMBOL]
```

List elements can be accessed via indexing:

```flame
somePrimes[0] # The first element of `somePrimes`
multi[2] = "cat" # Update the third element of `multi`
```

To append an element to the end of a list use `push`:

```flame
multi.push(🔥)
```

## Objects

An object is an unordered collection of named values.
To create an object we specify its properties' names and values inside parentheses:

```flame
person (name: "Daniel, age: 29)
```

Object properties can be accessed and updated:

```flame
person.name # "Daniel"
person.age = 30 # Update person.age
```

## Functions

A function is a reusable block of code.
To create a function we specify its arguments in parentheses, followed by an arrow, followed by the return type and function body:

```flame
add (a Int, b Int) -> Int { a + b }
```

The parentheses are always necessary.
If the function body is only a single expression then the return type and braces can be omitted:

```flame
hello (name String) -> print("Hello @name!")
```

To call the functions:

```flame
res add(1, 2) # 3
hello("Flame") # prints "Hello Flame!"
```
