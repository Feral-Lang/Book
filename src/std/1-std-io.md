# IO

The **IO** module gives access to a variety of functions to print text to a terminal or to a file and read user input.

All the given examples assume that the **IO** module was imported using:
```
let io = import('std/io');
```

## Functions

- [print](#print)
- [println](#println)
- [fprint](#fprint)
- [fprintln](#fprintln)
- [cprint](#cprint)
- [cprintln](#cprintln)
- [cdprint](#cdprint)
- [cdprintln](#cdprintln)
- [scan](#scan)
- [scaneof](#scaneof)
- [fflush](#fflush)

## Variables
- [stdout](#stdout)
- [stderr](#stderr)

### print
```
print(args...) -> nil
```
Prints all given `args` to the standard output without adding a new line after the last one

Example:
```
let name = 'John';
let age = '21';
io.print('My name is ', name, '.');
io.print('I am ', 21, '.');
```
Gives the output:
```
My name is John. I am 21.
```

### println
```
println(args...) -> nil
```
Prints all given `args` to the standard output and add a new line after the last one

Example:
```
let name = 'John';
let age = '21';
io.print('My name is ', name, '.');
io.print('I am ', 21, '.');
```
Gives the output:
```
My name is John. 
I am 21.
```


### fprint
```
fprint(file: file, args...) -> nil
```
Writes all given `args` to `file` without adding a new line after the last one

Example:
```
let fs = import('std/fs');
let file = fs.open('hello.txt', 'w')
let name = 'John';
let age = '21';
io.fprint(file, 'My name is ', name, '.');
io.fprint(file, 'I am ', 21, '.');
```
Produces a *hello.txt* file with the following content:
```
My name is John. I am 21.
```

### fprintln
```
fprintln(file: file, args...) -> nil
```
Writes all given `args` to `file` and add a new line after the last one

Example:
```
let fs = import('std/fs');
let file = fs.open('hello.txt', 'w')
let name = 'John';
let age = '21';
io.fprint(file, 'My name is ', name, '.');
io.fprint(file, 'I am ', 21, '.');
```
Produces a *hello.txt* file with the following content: 
```
My name is John. 
I am 21.
```

### cprint
```
print(args...) -> nil
```
Prints all given `args` to the standard output without adding a new line after the last one and interpret color codes to change the text color. A color change is not bound to a single `cprint` call and will remain active until another one comes in.

Example:
```
io.cprint('{r}ERROR: Unexpected failure.');       # Printed in red
io.cprint('ERROR: Failed to connect to server.'); # Printed in red
io.cprint('{y}WARNING: Something went wrong.');   # Printed in yellow
io.cprint('{0}INFO: Operation successful.');      # Printed in default color
```
The possible color codes are the following:

- `{0}` : Default color
- `{r}` : Red
- `{g}` : Green
- `{y}` : Yellow
- `{b}` : Blue
- `{m}` : Purple
- `{c}` : Cyan
- `{w}` : White
- `{br}` : Bold red
- `{bg}` : Bold green
- `{by}` : Bold yellow
- `{bb}` : Bold blue
- `{bm}` : Bold purple
- `{bc}` : Bold cyan
- `{bw}` : Bold white

### cprintln
```
cprintln(args...) -> nil
```
Prints all given `args` to the standard output and add a new line after the last one and interpret color codes to change the text color. A color change is not bound to a single `cprintln` call and will remain active until another one comes in.

Example:
```
io.cprintln('{r}ERROR: Unexpected failure.');       # Printed in red
io.cprintln('ERROR: Failed to connect to server.'); # Printed in red, on a new line
io.cprintln('{y}WARNING: Something went wrong.');   # Printed in yellow, on a new line
io.cprintln('{0}INFO: Operation successful.');      # Printed in default color, on a new line
```

For the list of available color codes, please refer to [cprint](#cprint)

### cdprint
```
cdprint(args...) -> nil
```
Prints all given `args` to the error output without adding a new line after the last one and interpret color codes to change the text color. A color change is not bound to a single `cprint` call and will remain active until another one comes in.

Example:
```
io.cprint('{r}ERROR: Unexpected failure.');       # Printed in red on `stderr`
io.cprint('ERROR: Failed to connect to server.'); # Printed in red on `stderr`
io.cprint('{y}WARNING: Something went wrong.');   # Printed in yellow on `stderr`
io.cprint('{0}INFO: Operation successful.');      # Printed in default color on `stderr`
```

For the list of available color codes, please refer to [cprint](#cprint)

### cdprintln
```
cdprintln(args...) -> nil
```
Prints all given `args` to the standard output and add a new line after the last one and interpret color codes to change the text color. A color change is not bound to a single `cprintln` call and will remain active until another one comes in.

Example:
```
io.cprintln('{r}ERROR: Unexpected failure.');       # Printed in red on `stderr`
io.cprintln('ERROR: Failed to connect to server.'); # Printed in red, on a new line on `stderr`
io.cprintln('{y}WARNING: Something went wrong.');   # Printed in yellow, on a new line on `stderr`
io.cprintln('{0}INFO: Operation successful.');      # Printed in default color, on a new line on `stderr`
```

For the list of available color codes, please refer to [cprint](#cprint)

### scan
```
scan(prompt: string = '') -> string
```
Reads a single line of text from the standard input. 

An optional `prompt` parameter can be passed to write the given string before reading the standard input.

Example:
```
let input = io.scan('Enter your age: ');
io.println('You are ', input, ' years old');
```

Possible output:
```
Enter your age: 21
You are 21 years old
```

### scaneof
```
scaneof(prompt: string = '') -> string
```
Reads text from the standard input until *EOF* is found. Even id *EOF* can be emitted by a user (usually *CTRL-D* on UNIX), `scaneof` is more likely to be useful when a **Feral** script takes as an input the output of another program.

An optional `prompt` parameter can be passed to write the given string before reading the standard input.

Example (*bio.fer*):
```
let input = io.scaneof();
io.println('Here is everything we know about you:\n', input);
```

Possible output:
```
echo "My name is John Doe,
I am 21 years old,
I live on Mars" | feral bio.fer
Here is everything we know about you:
My name is John Doe,I am 21 years old,I live on Mars
```

### fflush
```
fflush(file: file) -> nil
```
Forces all unwritten data to be written to the `file`.

`fflush` is useful because writes to `stdout`, `stderr` or any typical files are usually buffered and their content may not immediately be updated.

Example:
```
io.print('Enter your age: ');
io.fflush(io.stdout); # Force the prompt to be displayed before scan is called
let input = io.scan();
io.println('You are ', input, ' years old');
```

Possible output:
```
Enter your age: 21
You are 21 years old
```

### stdout
```
stdout: file
```
Special file associated with the standard output stream.

Example (*status.fer*):
```
io.fprintln(io.stdout, 'Everything is fine');
io.fprintln(io.stderr, 'We have a problem');
```

Possible usage:
```
feral status.fer 2> /dev/null # redirect stderr to /dev/null
```

Gives the output:
```
Everything is fine
```

### stderr
```
stderr: file
```
Special file associated with the standard error output stream.

Example (*status.fer*):
```
io.fprintln(io.stdout, 'Everything is fine');
io.fprintln(io.stderr, 'We have a problem');
```

Possible usage:
```
feral status.fer 1> /dev/null # redirect stdout to /dev/null
```

Gives the output:
```
We have a problem
```
