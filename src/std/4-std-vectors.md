# Vectors

The **vec** module defines the `vector` type and all the vector manipulation related functions.

A `vector` is a sequence container that can store heterogeneous types.

All the given examples assume that the **vec** module was imported using:
```
vec = import('std/vec');
```

## Functions
 - [new](#new)

## `vector` Member Functions

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
- [each](#each)
- [slice](#slice)
- [next](#next)

### new
```
vec.new(elems...) -> vector
```

Creates a new vector using the given elements

Example:
```
let io = import('std/io');
let v = vec.new(12, 'Hello', 3.14);
io.println(v);
```

Gives the output:
```
[12, Hello, 3.14000000000000012434]
```

### len
```
vector.len() -> int
```
Returns the number of elements inside the vector

Example:
```
let io = import('std/io');
io.println(vec.new(0, 1, 2).len());
```

Gives the output:
```
3
```

### empty
```
vector.empty() -> bool
```
Checks whether the vector is empty

Example:
```
let io = import('std/io');
io.println(vec.new(0, 1, 2).empty());
io.println(vec.new().empty());
```

Gives the output:
```
false
true
```

### front
```
vector.front() -> value
```
Returns the first element of the vector, or `nil` if the vector is empty

Example:
```
let io = import('std/io');
io.println(vec.new(0, 1, 2).front());
io.println(vec.new().front());
```

Gives the output:
```
0
(nil)
```

### back
```
vector.back() -> value
```
Returns the last element of the vector, or `nil` if the vector is empty

Example:
```
let io = import('std/io');
io.println(vec.new(0, 1, 2).back());
io.println(vec.new().back());
```

Gives the output:
```
2
(nil)
```

### push
```
vector.push(elem) -> vector
```
Appends `elem` to the vector and returns the modified vector

Example:
```
let io = import('std/io');
let v = vec.new(0);
v.push(1);
io.println(v.push(2));
```

Gives the output:
```
[0, 1, 2]
```

### pop
```
vector.pop() -> vector
```
Removes the last element and returns the modified vector

Example:
```
let io = import('std/io');
let v = vec.new(0, 1, 2);
v.pop();
io.println(v.pop());
```

Gives the output:
```
[0]
```

### insert
```
vector.insert(idx: int, elem) -> vector
```
Inserts the `elem` element at index `idx` and returns the modified vector

Example:
```
let io = import('std/io');
let v = vec.new(0, 2);
v.insert(2, 3);
io.println(v.insert(1, 1));
```

Gives the output:
```
[0, 1, 2, 3]
```

### erase
```
vector.erase(idx: int) -> vector
```
Removes one element at index `idx` and returns the modified vector

Example:
```
let io = import('std/io');
let v = vec.new(0, 1, 9, 12, 2);
v.erase(3);
io.println(v.erase(2));
```

Gives the output:
```
[0, 1, 2]
```

### lastidx
```
vector.lastidx() -> int
```
Returns the index of the last element. Equivalent to `len() - 1` 

Example:
```
let v = vec.new(0, 1, 2);
io.println(v.lastidx());
```

Gives the output:
```
2
```

### set
```
vector.set(idx: int, elem) -> vector
```
Replaces the element at index `idx` with `elem` and returns the modified vector

Example:
```
let io = import('std/io');
let v = vec.new(0, 0, 0);
v.set(0, 2);
io.println(v.set(1, 1));
```

Gives the output:
```
[2, 1, 0]
```

### at
```
vector.at(idx: int) -> value
```
Returns the element at index `idx`, or `nil` if out of range

Example:
```
let io = import('std/io');
let v = vec.new(0, 1, 2);
io.println(v.at(2));
io.println(v.at(3));
```

Gives the output:
```
2
(nil)
```
### operator []
```
vector[idx: int] -> value
```
Returns the element at index `idx`, or `nil` if out of range

Example:
```
let io = import('std/io');
let v = vec.new(0, 1, 2);
io.println(v[2]);
io.println(v[3]);
```

Gives the output:
```
2
(nil)
```

### slice
```
vector.slice(start: int, end: int = -1) -> vector
```
Extracts the elements from `start` to `end - 1` and returns them in a new vector. If `end == -1` then the slice ends at the end of the vector

Example:
```
let io = import('std/io');
let v = vec.new(0, 1, 2, 3);
io.println(v.slice(1));
io.println(v.slice(1, 3));
```

Gives the output:
```
[1, 2, 3]
[1, 2]
```

### each
```
vector.each() -> iterator
```
Returns an iterator pointing to the first element, allowing easy vector iteration

Example:
```
let io = import('std/io');
let v = vec.new(0, 1, 2);
for elem in v.each() {
    io.println(elem);
}
```

Gives the output:
```
0
1
2
```

### next
```
iterator.next() -> value
```
Returns the value pointed by the iterator, or `nil` if out of range, and then advances the iterator to the next element

Example:
```
let io = import('std/io');
let v = vec.new(0, 1, 2, 3);
let iter = v.each();
for i in range(v.len() + 1) {
    io.println(iter.next());
}
```

Gives the output:
```
0
1
2
3
(nil)
```