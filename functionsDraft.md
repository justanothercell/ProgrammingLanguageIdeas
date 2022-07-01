# Functional Concept

The concept aims to makef fuctions and scopes work uniformly. 
This uniform handling makes extracting code to local functions easy and allows for cool syntactic stuff.

### Example
Some arbitary calculation to demonstrate function concept.
Of course this calculation can be done in one line, this is just demonstration!

Typing is done python style (for now) but thats not the main concern of this idea.
Some types maybe can eb automatically inferred and thus omitted in code, 
but it should be possible to explicitely type always. 
I dislike the types beign in front of the `{`, but thats still better than the types
being after the `}` like this: `}: int`, which would be asthetically better maybe, but 

The semicolon indicates immediate scope execution.
The advantage of this is, that an if/for loop body is automatically a scope and we can even make this body a syntactic sugar.

Idk if all is syntactically valid and its just a draft, but it seems like a good idea.

###### Normal execuion in current scope
```c#
x: int = 8;
v: int = sqrt(x);
y: int = x*x+v;
println(y);
```

#### Scoping
First we will extract the calculation to an extra scope which will be executed immediately.

###### Scoping the calculation
v is now a local variable in this new scope. variables from outer scope usable.
```c#
int x = 8;
int y;
{
  int v = sqrt(x);
  y = x*x+v;
};
println(y);
```

###### Scoping the calculation with returning value
```c#
int x = 8;
int y = int {
  int v = sqrt(x);
  return x*x+v;
};
println(y);
```

###### Scoping the calculation with returning value, but its inside a function so you cant use a semicolon to make sure its executed
```c#
int x = 8;
println(int {
  int v = sqrt(x);
  return x*x+v;
}());
```

###### Scoping the calculation with returning value and input
```c#
x: int = 8;
y: int = in: int -> int {
  int v = sqrt(x);
  return x*x+v;
}(x);
println(y);
```

#### Functions from Scoping
Now we store that as a named function and then execute it.
As you can see, this is not much work at all. 

###### Funcing the calculation
```c#
int x = 8;
int y;
calc: func = {
  int v = sqrt(x);
  y = x*x+v;
}
calc();
println(y);
```

###### Funcing the calculation with returning value
```c#
int x = 8;
calc: func = int {
  int v = sqrt(x);
  return x*x+v;
}
int y = calc();
println(y);
```

###### Funcing the calculation with returning value and input
```c#
x: int = 8;
calc: func = in: int -> int {
  int v = sqrt(x);
  return x*x+v;
}
inty y = calc(x);
println(y);

// super explicit typing:
x: int = 8;
calc: func > int -> int = in: int -> int {
  int v = sqrt(x);
  return x*x+v;
}
inty y = calc(x);
println(y);
```

### Making syntactic sugar out of this scoping functionality

###### A "standard" implementation of this
```c#
Optional<HTTPResult> result = HTTP.get("url");
if(result.ok()){ // returns true if the optional is not null, idk what the coneentional function name is
  print(result.whatever());
}
```
###### Using inline functions
```c#
Optional<HTTPResult> result = HTTP.get("url");
result.ok({
  print(result.whatever());
});
```
###### Using syntactic sugar to do exactly the same as the above
```c#
Optional<HTTPResult> result = HTTP.get("url");
result.ok(){
  print(result.whatever());
}
```
###### Second approach using inline functions
```c#
HTTP.get("url", HTTPResult result -> {
  print(result.whatever());
});
```
###### Second approach using syntactic sugar to do exactly the same as the above
```c#
HTTP.get("url") HTTPResult result -> {
  print(result.whatever());
}
```
####### Implementation of HTTP.get() for thr ttwo above
```c#
get: func = url: String, onSuccess: func > HTTPResult {
  res: HTTPResult = doSomeQueriesAndOtherStuff(url, stuff, importantParam, theObligatoryConstant);
  if(res.returnCode() == 200) onSuccess();
}
```
