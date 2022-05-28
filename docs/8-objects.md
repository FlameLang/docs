# Objects

We can create an object by specifying its properties and values inside braces:

```flame
emptyObject = {}

human = {
    name: "Daniel",
    age: 29,
}
```

We can access an object's properties using dot-notation:

```flame
human.age + 10 # 39
```

We can alter an object's properties using dot notation as well:

```flame
human.age = 100
```

## Types

We can create object types like so:

```flame
Person {
    name String,
    age Int
}
```

We can specify a default value for each field:

```flame
Vec2 {
    x Float = 0.0,
    y Float = 0.0,
}
```

Each object type implicitly defines an object constructor (using the default values if any):

```flame
pos = Vec2() # creates a new Vector2
```

If any object fields don't have a default value, the implicit constructor needs to be called with those values:

```flame
SomeObjType {
    x Float,
    y Int = 1,
}

obj1 = SomeObjType(x: 1.2)
obj2 = SomeObjType(x: 1.2, y: 5) # overriding default value
```

## Methods

In Flame a method is just a property of an object whose type is a function instance (i.e. a constant value).
For example, `sum` below is a method:

```flame
Vec2 {
    x Int = 0
    y Int = 0
    sum () => x + y
}
```

Whenever a method is called it has access to all of the object's properties as if they were in scope.
