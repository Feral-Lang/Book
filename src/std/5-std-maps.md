# Maps

The **map** module defines the `map` type and all the vector manipulation related functions.

A `map` is an associative container that can store heterogeneous types.

All the given examples assume that the **map** module was imported using:
```
map = import('std/map');
```

## Functions
 - [new](#new)

## `map` Member Functions
 - [len](#len)
 - [insert](#insert)
 - [erase](#erase)
 - [get](#get)
 - [operator []](#operator-)
 - [find](#find)
 - [each](#each)
 - [next](#next)
 
### new
```
map.new(key1, value1, key2, value2, ...) -> map
```
Creates a new map using the given key/value pairs. The keys must be convertible to `string`s. Also, it must correspond a value to each key, meaning that the number of arguments must always be even

Example:
```
let io = import('std/io');
let m = map.new(0, "Zero", 1, "One", "Answer?", 42);
io.println(m);
```

Gives the output:
```
{Answer?: 42, 0: Zero, 1: One}
```
 
Note that the elements are not stored in the order they are given. They are lexicographically sorted

### len
```
map.len() -> int
```
Returns the number of key/value pairs inside the map

Example:
```
let io = import('std/io');
io.println(map.new(0, "Zero", 1, "One", "Answer?", 42).len());
```

Gives the output:
```
3
```

### insert
```
map.insert(key, value) -> map
```
Inserts the `key`/`value` pair and returns the modified map

Example:
```
let io = import('std/io');
let m = map.new(0, "Zero");
m.insert(1, "One");
io.println(m.insert("Answer?", 42));
```

Gives the output:
```
{Answer?: 42, 0: Zero, 1: One}
```

### erase
```
map.erase(key) -> map
```
Removes the `key` and its associated value and returns the modified map

Example:
```
let io = import('std/io');
let m = map.new(0, "Zero", 1, "One", "Answer?", 42);
m.erase(1);
io.println(m.erase("Answer?"));
```

Gives the output:
```
{0: Zero}
```

### get
```
map.get(key) -> map
```
Returns the value associated with `key`, or `nil` if it doesn't exist

Example:
```
let io = import('std/io');
let m = map.new(0, "Zero", 1, "One", "Answer?", 42);
io.println(m.get("Answer?"));
io.println(m.get("Oops"));
```

Gives the output:
```
42
(nil)
```

### operator []
```
map[key] -> value
```
Returns the value associated with `key`, or `nil` if it doesn't exist

Example:
```
let io = import('std/io');
let m = map.new(0, "Zero", 1, "One", "Answer?", 42);
io.println(m["Answer?"]);
io.println(m["Oops"]);
```

Gives the output:
```
2
(nil)
```

### each
```
map.each() -> iterator
```
Returns an iterator pointing to the first key/value pair, allowing easy map iteration

Example:
```
let io = import('std/io');
let m = map.new(0, "Zero", 1, "One", "Answer?", 42);
for elem in m.each() {
    io.println(elem.0, ": ", elem.1);
}
```

Gives the output:
```
Answer?: 42
0: Zero
1: One
```

### next
```
iterator.next() -> value
```
Returns the key/value pair pointed by the iterator, or `nil` if out of range, and then advances the iterator to the next element

Example:
```
let io = import('std/io');
let m = map.new(0, "Zero", 1, "One", "Answer?", 42);
let iter = m.each();
for i in range(m.len()) {
    let elem = iter.next();
    io.println(elem.0, ': ', elem.1);
}
```

Gives the output:
```
Answer?: 42
0: Zero
1: One
```