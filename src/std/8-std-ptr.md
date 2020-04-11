# Ptr

The **ptr** module defines the `ptr` type for pointer-like referencing and modification of existing variables

All the given examples assume the following imports:
```
let ptr = import('std/ptr');
let io = import('std/io');
```

## Functions
 - [new](#new)

## `ptr` Member Functions
 - [set](#set)
 - [get](#get)
 
### new
```
ptr.new(var = nil) -> ptr
```
Creates a new pointer, optionally pointing to the given variable `var`.

Example:
```
let answer = 42;
let answer_ptr = ptr.new(answer);
```
 
### get
```
ptr.get() -> value
```
Returns the value pointed to, or `nil` or nil if it does not point to a variable. Can be used to modify to pointed variable

Example:
```
let answer = 42;
let answer_ptr = ptr.new(answer);
io.println(answer_ptr.get());
answer_ptr.get() = 12;
io.println(answer);
let nil_ptr = ptr.new();    
io.println(nil_ptr.get());
```

Gives the output:
```
42
12
(nil)
```
 
### set
```
ptr.set(value) -> ptr
```
Makes the pointer point to `value`

Example:
```
let answer = 42;
let pi = 3.14;
let answer_ptr = ptr.new(answer);
io.println(answer_ptr.get());
answer_ptr.set(pi);
io.println(answer_ptr.get());
```

Gives the output:
```
42
3.14
```