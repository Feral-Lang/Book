# Strings

The **str** module defines the `string` type and all string manipulation related functions.

A `string` is a sequence of characters. There is no character type in **Feral** and so are represented are one character strings.

All the given examples assume that the **str** module was imported using:
```
import('std/str');
```

## `string` Member Functions

- [len](#len)
- [empty](#empty)
- [front](#front)
- [back](#back)
- [push](#push)
- [pop](#pop)
- [insert](#insert)
- [erase](#erase)
- [lastidx](#lastidx)
- [set](#set)
- [at](#at)
- [operator []](#operator-)
- [trim](#trim)
- [split](#split)
- [c_to_i](#c_to_i)
- [i_to_c](#i_to_c)

### len
```
len() -> int
```
Returns the number of characters

Example:
```
let io = import('std/io');
io.println('hello'.len());
```

Gives the output:
```
5
```

### empty
```
empty() -> bool
```
Checks whether the string is empty 

Example:
```
let io = import('std/io');
io.println('hello'.empty());
io.println(''.empty());
```

Gives the output:
```
false
true
```

### front
```
front() -> string
```
Returns the first character of the string, or `nil` if the string is empty

Example:
```
let io = import('std/io');
io.println('hello'.push(' world'));

```

Gives the output:
```
h
(nil)
```

### back
```
front() -> string
```
Returns the last character of the string, or `nil` if the string is empty

Example:
```
let io = import('std/io');
io.println('hello'.front());
io.println(''.empty());
```

Gives the output:
```
o
(nil)
```

### push
```
push(str: string) -> string
```
Appends `str` to the string and returns the modified string

Example:
```
let io = import('std/io');
let hello = 'hello';
hello.push(', ');
io.println(hello.push('world!'));
```

Gives the output:
```
hello, world!
```

### pop
```
string.pop() -> string
```
Removes the last character and returns the modified string

Example:
```
let io = import('std/io');
let hello = 'hello';
hello.pop();
io.println(hello.pop());
```

Gives the output:
```
hel
```

### insert
```
string.insert(idx: int, str: string) -> string
```
Inserts the `str` string at index `idx` and returns the modified string

Example:
```
let io = import('std/io');
let hello = 'heo';
hello.insert(2, 'll');
io.println(hello);
```

Gives the output:
```
hello
```

### erase
```
string.erase(idx: int) -> string
```
Removes one character at index `idx` and returns the modified string

Example:
```
let io = import('std/io');
let hello = 'helloo';
hello.erase(4);
io.println(hello);
```

Gives the output:
```
hello
```

### lastidx
```
string.lastidx() -> int
```
Returns the index of the last character. Equivalent to `len() - 1` 

Example:
```
let io = import('std/io');
io.println('hello'.lastidx());
```

Gives the output:
```
4
```

### set
```
string.set(idx: int, char: string) -> string
```
Replaces the character at index `idx` with `char` and returns the modified string

Example:
```
let io = import('std/io');
let hello = 'hello_';
hello.set(5, '!');
io.println(hello);
```

Gives the output:
```
hello!
```

### at
```
string.at(idx: int) -> string
```
Returns the character at index `idx`, or `nil` if out of range

Example:
```
let io = import('std/io');
io.println('hello'.at(0));
```

Gives the output:
```
h
```
### operator []
```
string[idx: int] -> string
```
Returns the character at index `idx`, or `nil` if out of range

Example:
```
let io = import('std/io');
io.println('hello'[0]);
```

Gives the output:
```
h
```

### trim
```
string.trim() -> string
```
Removes all whitespace characters at the beginning and at the end of the string and returns the modified string

Example:
```
let io = import('std/io');
io.println('_', '   hello   '.trim(), '_');
```

Gives the output:
```
_hello_
```

### split
```
string.split(delim: string = ':') -> vector<string>
```
Splits the string using `delim` as a single character delimiter and returns a vector of strings

Example:
```
let io = import('std/io');
io.println('hello;world'.split(';'));
```

Gives the output:
```
[hello, world]
```

### c_to_i
```
string.c_to_i() -> int
```
Converts the first character to its ASCII integer representation. Returns 0 if the string is empty

Example:
```
let io = import('std/io');
io.println('0'.c_to_i());
```

Gives the output:
```
48
```

### i_to_c
```
int.i_to_c() -> string
```
Converts an integer from its ASCII integer representation to a string

Example:
```
let io = import('std/io');
io.println(48.i_to_c());
```

Gives the output:
```
0
```