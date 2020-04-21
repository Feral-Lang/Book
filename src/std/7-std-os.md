# OS

The **os** module allow to access to some functionalities of the underlying operating system

All the given examples assume the following imports:
```
let os = import('std/os');
let io = import('std/io');
```

## Functions
 - [sleep](#sleep)
 - [get_env](#get_env)
 - [set_env](#set_env)
 - [exec](#exec)
 - [find_exec](#find_exec)
 - [install](#install)
 - [get_cwd](#get_cwd)
 - [set_cwd](#set_cwd)
 - [mkdir](#mkdir)
 - [rm](#rm)
 - [copy](#copy)
 - [chmod](#chmod)

## Variables
 - [name](#name)
  
### exists
```
os.sleep(ms: int) -> nil
```
Pauses the program execution for `ms` milliseconds. Please not that the exact sleep time might be greater than `ms` because of how OS scheduler works.

Example:
```
io.println('Waiting a bit...');
os.sleep(1000);
io.println('Done!');
```

Gives the output:
```
Waiting a bit...
# one second later
Done!
```

### get_env
```
os.get_env(var: string) -> string
```
Returns the content of the environment variable `var` if it exists or an empty string otherwise

Example:
```
io.println('$HOME=', os.get_env('HOME'));
```

Possible output:
```
$HOME=/home/feral
```

### set_env
```
os.set_env(var: string, value: string, overwite: bool = false) -> int
```
Sets the content of the environment variable `var` with the content of `value`. If `var` already exists, it won't be overwritten unless `overwrite` is `true`. The function returns `0` on success and `-1` on error

Example:
```
io.println('$FOOBAR=', os.get_env('FOOBAR'));
os.set_env('FOOBAR', 'Hello');
io.println('$FOOBAR=', os.get_env('FOOBAR'));
os.set_env('FOOBAR', 'Hello, world!');
io.println('$FOOBAR=', os.get_env('FOOBAR'));
os.set_env('FOOBAR', 'Hello, world!', true);
io.println('$FOOBAR=', os.get_env('FOOBAR'));
```

Gives the ouput:
```
$FOOBAR=
$FOOBAR=Hello
$FOOBAR=Hello
$FOOBAR=Hello, world!
```

### exec
```
os.exec(cmd: string) -> int
```
Executes the command `cmd` and returns its result. All text printed by `cmd` will be redirected to the standard output

Example:
```
io.println(os.exec('uname'));
```

Possible ouput:
```
Linux
0
```

### find_exec
```
os.find_exec(exec: string) -> string
```
Search in `PATH` for the executable `exec` and returns its path if found or an empty string otherwise

Example:
```
io.println(os.find_exec('ls'));
```

Possible ouput:
```
/usr/bin/ls
```

### install
```
os.install(src: string, dest: string) -> int
```
Copies all the content of the source file or folder `src` into `dest`. The path leading to `dest` will be created if necessary. The function returns `0` on success and `-1` on error

Example:
```
os.install('/home/feral/Documents', '/mnt/backup');
```

### get_cwd
```
os.get_cwd() -> string
```
Returns the current working directory

Example:
```
io.println(os.get_cwd());
```

Possible output:
```
/home/feral
```

### set_cwd
```
os.set_cwd(wd: string) -> int
```
Changes the current working directory to be `wd`. The function returns `0` on success and `-1` on error

Example:
```
io.println(os.get_cwd());
os.set_cwd('/home/feral/Documents');
io.println(os.get_cwd());
```

Possible output:
```
/home/feral
/home/feral/Documents
```

### mkdir
```
os.mkdir(dir...: string) -> int
```
Creates all given directories. The function returns `0` on success and `-1` on error

Example:
```
os.mkdir('/home/feral/Build', '/home/feral/Tests');
```

### rm
```
os.rm(path...: string) -> int
```
Removes all given files and directories. The function returns `0` on success and `-1` on error

Example:
```
os.rm('/home/feral/Build', '/home/feral/Tests');
```

### copy
```
os.copy(src...: string, dest: string) -> int
```
Copies all given files and directories to `dest`. The function returns `0` on success and `-1` on error

Example:
```
os.copy('/home/feral/Build', '/home/feral/Tests', '/tmp');
```

### chmod
```
os.chmod(dest: string, mode: string = '755', recurse: bool = 'true') -> int
```
Changes the permission of `dest` to `mode`, and recursively to its content if `recurse` is `true`. The function returns `0` on success and `-1` on error

Example:
```
os.chmod('/home/feral/Build', '777', false);
```

### name
```
os.name: string
```
The name of the OS. Current possible values are `linux`, `macos`, `bsd` and `android`

Example:
```
io.println(os.name;
```

Possible ouput:
```
linux
```
