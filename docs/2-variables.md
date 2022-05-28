# Variables

Let's create a variable and assign it a value:

```flame
universe = 42
```

Variables have types. Since we didn't specify one in the snippet above, the type of `universe` is `Any`.
That means `universe` can hold a value of any type. For example, we can assign it a value of type [`String`](https://en.wikipedia.org/wiki/String_(computer_science)):

```flame
universe = "Not all those who wander are lost."
```

If we want, we can specify a type explicitly when creating a variable:

```flame
count Int = 3791
```

`count` has type `Int` (as in [integer](https://en.wikipedia.org/wiki/Integer)). If we try assigning `count` a value of any other type we will get an error.

:::important
Once a variable is created its type can never be changed.
:::

We can also declare a variable without assigning it a value:

```flame
lit Bool
```

If we try to use `lit` before assigning it a value, we will get an error.
When we do assign a value to `lit` it will have to be of type `Bool` (as in [boolean](https://en.wikipedia.org/wiki/Boolean_data_type)):

To summarize, the three different ways to create a variable are:

| Syntax              | Value         | Variable Type  |
| ------------------- | :-----------: | :------------: |
| `name = value`      | `value`       | `Any `         |
| `name Type = value` | `value`       | `Type`         |
| `name Type`         | uninitialized | `Type`         |
