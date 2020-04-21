# Core Functions

- [Global](#global)
- [Structures](#structures)
- [All types](#all-types)
- [nil](#nil)
- [bool](#bool)
- [int](#int)
- [flt](#flt)
- [string](#string)

## Global
|    Function     | Description |
| :-------------: | ----------- |
|     `mload`     |             |
|    `import`     |             |
| `__ismainsrc__` |             |

## Structures
|    Function    | Description |
| :------------: | ----------- |
| `set_typename` |             |


## All types
| Function | Description |
| :------: | ----------- |
|   `==`   |             |
|   `!=`   |             |
|  `copy`  |             |
|  `str`   |             |

## nil
| Function | Description |
| :------: | ----------- |
|   `==`   |             |
|   `!=`   |             |

## bool
| Function | Description |
| :------: | ----------- |
|   `<`    |             |
|   `>`    |             |
|   `<=`   |             |
|   `>=`   |             |
|   `==`   |             |
|   `!=`   |             |
|   `!`    |             |

## int
| Function | Description |
| :------: | ----------- |
|   `+`    |             |
|   `-`    |             |
|   `*`    |             |
|   `/`    |             |
|   `%`    |             |
|   `+=`   |             |
|   `-=`   |             |
|   `*=`   |             |
|   `/=`   |             |
|   `%=`   |             |
|   `**`   |             |
|  `++x`   |             |
|  `x++`   |             |
|  `--x`   |             |
|  `x--`   |             |
|   `u-`   |             |
|   `<`    |             |
|   `>`    |             |
|   `<=`   |             |
|   `>=`   |             |
|   `==`   |             |
|   `!=`   |             |

## flt
| Function | Description |
| :------: | ----------- |
|   `+`    |             |
|   `-`    |             |
|   `*`    |             |
|   `/`    |             |
|   `+=`   |             |
|   `-=`   |             |
|   `*=`   |             |
|   `/=`   |             |
|  `++x`   |             |
|  `x++`   |             |
|  `--x`   |             |
|  `x--`   |             |
|   `u-`   |             |
| `round`  |             |
|   `<`    |             |
|   `>`    |             |
|   `<=`   |             |
|   `>=`   |             |
|   `==`   |             |
|   `!=`   |             |

## string
|         Function         | Description                                                    |
| :----------------------: | -------------------------------------------------------------- |
|           `+`            |                                                                |
|           `*`            |                                                                |
|           `+=`           |                                                                |
|           `*=`           |                                                                |
|           `<`            |                                                                |
|           `<=`           |                                                                |
|           `>=`           |                                                                |
|           `==`           |                                                                |
|           `!=`           |                                                                |
| `at(idx: int) -> string` | Returns the character at index `idx`, or `nil` if out of range |
|  `[idx: int] -> string`  | Returns the character at index `idx`, or `nil` if out of range |

Examples:
```
let io = import('std/io');
let hello = 'hello!';
io.println(hello.at(0));
io.println(hello[5]);
```

Output:
```
h
(nil)
```