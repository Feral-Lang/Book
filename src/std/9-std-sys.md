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
 - [self_binary](#self_binary)
 - [args](#args)
 - [inc_load_loc](#inc_load_loc)
 - [dll_load_loc](#dll_load_loc)
 - [dll_core_load_loc](#dll_core_load_loc)
 - [feral_home_dir](#feral_home_dir)

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

### inc_load_loc
```
sys.inc_load_loc: string
```
Contains the path to the user modules includes directory

Example:
```
io.println(sys.inc_load_loc);
```

Possible output:
```
/home/feral/.feral/include
```

### dll_load_loc
```
sys.dll_load_loc: string
```
Contains the path to the user modules libraries directory

Example:
```
io.println(sys.dll_load_loc);
```

Possible output:
```
/home/feral/.feral/lib
```

### feral_home_dir
```
sys.feral_home_dir: string
```
Contains the path to the user modules directory

Example:
```
io.println(sys.feral_home_dir);
```

Possible output:
```
/home/feral/.feral
```

### dll_core_load_loc
```
sys.dll_core_load_loc: string
```
Contains the path to the core modules libraries directory

Example:
```
io.println(sys.dll_core_load_loc);
```

Possible output:
```
/usr/local/lib/feral
```
