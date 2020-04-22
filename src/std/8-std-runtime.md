# Runtime

The **runtime** module allows to inspect the programs at runtime

All the given examples assume the following imports:
```
let rt = import('std/runtime');
let io = import('std/io');
```

## Functions
 - [var_exists](#var_exists)

### var_exists
```
runtime.var_exists(name: str) -> bool
```
Checks if the given variable name in known to the virtual machine

Example:
```
io.println(rt.var_exists('hello'));
let hello = 'Hello, world!';
io.println(rt.var_exists('hello'));
```

Gives the output:
```
false
true
```