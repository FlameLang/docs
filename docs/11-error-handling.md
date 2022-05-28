# Error Handling

THe optional + result type: `Type?` ? or have separate types?

Maybe have `Type?` as optional and `Type!` as result. Can combine with `Type?!`.

Can automatically propagate errors on fucntions that return a result type with `call()?` and can forcibly "unwrap" with `call()!`


```flame
Type? = Type | nil | Error


Err {
    error () -> String
}

Option<T> (T|nil)
Result<T> (T|Error)

```


```flame
res = functionThatCouldError()
if res ~ Err {
    print(res.error())
}

```
maybe use `or`-notation:
```flame
res = functionThatCouldError() or {
    print(err)
}
```


```
functionThatCouldError() is {
    String =>
    Result =>
}
```

Maybe just have Optional and result separate?

Type? = Type | nil
Result = Type | Err



if want can return String|nil which is different from String? and from (String|nil)?

Maybe use ? for OR-nil and ! for OR-error




can use `or` with potential nil-values expression i.e.


a = func() or "default"

and can use `else` for potential Err-valued expressions i.e.

b = func() else {

}


How to handle both nil and error on a tyep like MyType?! ?

a = func() or "default" else {

}

a = func() else {
    
} or "default"

actually just allow "or" notation



can we define `nil` as an empty error?
then Type? = Type | nil

what if returning a nil is not a error? i.e. can get a hashmap entry and it doesn't exist.
then could return EMPTY (a symbol) instead of nil. what if the consumer wants to propagate up?

res = hashmap.get(a) or { return nil }
if res == EMPTY { return nil }


OK what if they are separate? how to handle them separately or together?


func()? or { .. value is nil }
func() or { .. nil or err? or both? }


a = func()
a ~ {
    String => ...
    Err => ...
    nil => ...
}

if res ~ Err & res.errorType = 1 {
    .. handle error
}


OK SO SUMMARIZING:

can use `expr or expr` notation which uses the second expression if the first is nil.
why not juse `expr | expr` ? i.e. name = getName() | "John"
can also allow `expr & expr` i.e. showData & renderData()

can use `expr?` which propagates error up.
to propagate error and add default values:
`expr? | default`

if want to handle the error then need to write code
a = expr
if a ~ Err & a.error().includes("someerror") { ... }

can use `error("error")` to create a basic error
or just write
{error: ()->"not implemented"}


a = func() or {
    err...
} or "default value"

a = func() or "def" or "def

```flame
Err {
    error ()->String
    OR
    error String

}
```


SpecialErr {
    error ()->type+msg
    type String
    msg String
}


i.e.  String!

String?! means either a string or nil or an Error

Type! = Type | Err


f = () -> String! {...}

f()? propagates error up
f()! panics on error

how to handle error?

f() or "default value"
f() or {
    err defined here
}


## Optionals

TODO - maybe have a single result+optional type
think about error handling
allow calling functions with question mark at the end: call()?

It's common to write types that are `OR`-ed with `nil`:

```flame
optionalInt: Int | nil
optionalString: String | nil
```

Therefore Flame has a shorthand - simply append a `?` like so:

```flame
optionalInt: Int?
optionalString: String?
```
