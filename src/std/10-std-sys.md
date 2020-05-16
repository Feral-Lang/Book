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
- [install_prefix](#install_prefix)
- [self_bin](#self_bin)
- [self_base](#self_base)

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

### self_bin
```
sys.self_bin: string
```
Contains the full path of the interpreter, according to binary's location

Example (*loc.fer*):
```
io.println(sys.self_bin);
```

### self_base
```
sys.self_base: string
```
Contains the base directory of the interpreter, according to binary's location

Example (*loc.fer*):
```
io.println(sys.self_base);
```

Possible output:
```
$ /usr/local/bin/feral loc.fer
/usr/local
$ feral loc.fer
feral
```

### install_prefix
```
sys.install_prefix: string
```
Contains the path to the feral installation directory

Example:
```
io.println(sys.install_prefix);
```

Possible output:
```
/usr/local
```