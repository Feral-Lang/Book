# Sys

The **sys** module provides information and control of the feral interpreter

All the given examples assume the following imports:
```
let sys = import('std/sys');
let io = import('std/io');
```

## Functions
- [var_exists](#var_exists)
- [exit](#exit)

## Variables
- [args](#args)
- [self_binary](#self_binary)
- [prefix](#prefix)

### var_exists
```
sys.var_exists(name: str) -> bool
```
Checks if the given variable name in known to the virtual machine

Example:
```
io.println(sys.var_exists('hello'));
let hello = 'Hello, world!';
io.println(sys.var_exists('hello'));
```

Gives the output:
```
false
true
```

### exit
```
sys.exit(code: int = 0) -> nil
```
Exits the program using the given return `code`. A return code of zero (default value) indicates a graceful exit while a non-zero value indicates a failure in running the program

Example:
```
let success = true;
if success {
    sys.exit();
}
else {
    sys.exit(-1);
}
```

### args
```
sys.args: vector<string>
```
Contains the arguments passed to feral, after the main source file

Example (*args.fer*):
```
io.println(sys.args);
```

Possible output:
```
$ feral args.fer 1 2 3
[1, 2, 3]
$ feral args.fer hello world
[hello, world]
```

### self_binary
```
sys.self_binary: string
```
Contains the location of the interpreter, as executed on the command line

Example (*loc.fer*):
```
io.println(sys.self_binary);
```

Possible output:
```
$ /usr/local/bin/feral loc.fer
/usr/local/bin/feral
$ feral loc.fer
feral
```

### prefix
```
sys.prefix: string
```
Contains the path to the user modules directory

Example:
```
io.println(sys.prefix);
```

Possible output:
```
/usr/local
```