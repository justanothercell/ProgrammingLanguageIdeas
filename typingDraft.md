# Typing

Typing half pyton style. Just ideas, when i show multiple optons to do the same thing
that doesnt mean all can coexist.

#### Simpel typing example
```c#
// explicit typing
pi: float = 3.1415f;

// quicktype/autoinferred options:
pi := 3.1415f;
// or
pi: var = 3.1415f;
// or
pi: ? = 3.1415f;
```

#### Having fun with egnerics and functions to see whether it works
```c#
// explicit typing
myFunc: func > int, int, (func > object) -> Optional<int> = a: int, b: int, printer: (func > object) -> Optional<int> { ... }
// less typing
// in this case var is the whole sinature.
myFunc: func > var = a: int, b: int, printer: (func > object) -> Optional<int> { ... }
myFunc: var = a: int, b: int, printer: (func > object) -> Optional<int> { ... }
myFunc := a: int, b: int, printer: (func > object) -> Optional<int> { ... }


// inner func has return
myFunc2 := a: int, b: int, printer: (func > object -> string) -> Optional<int> { ... }

result: Optional<int> = myFunc(1, 2, println);
```
### Option two, function signatures are just generics (probably more intuitive(?))
```c#
// explicit typing
myFunc: func<int, int, func<object> -> Optional<int>> = a: int, b: int, printer: func<object> -> Optional<int> { ... }

// less typing
// in this case var is the whole sinature.
myFunc: func<var> = a: int, b: int, printer: func<object> -> Optional<int> { ... }
myFunc: var = a: int, b: int, printer: func<object> -> Optional<int> { ... }
myFunc := a: int, b: int, printer: func<object> -> Optional<int> { ... }


// inner func has return
myFunc2 := a: int, b: int, printer: func<object -> string> -> Optional<int> { ... }

result: Optional<int> = myFunc(1, 2, println);
```
### classes
```c#
Player: class = Entity {
  health: int = 10;
  position: Vector2f = Vector2f(0, 0);
  
  update := delta: float {
    ...
  }
}

Optional: class<T> = {
  obj: T = null; // allow nullables? debate for another day...
  
  __init__ := obj: T {
    this.obj = obj;
  }
}
```
