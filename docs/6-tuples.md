# Tuples

A tuple is an ordered, fixed-size, finite collection of values:

```flame
person = ("John", 31)
```

Tuple fields can be accessed and updated using *dot*-notation:

```flame
if person.0 == "John" {
    print("It's John!")
    person.1 = 32 # increase age
}
```
