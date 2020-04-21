# FS

The **fs** module allow to access and manipulate the file system

All the given examples assume the following imports:
```
let fs = import('std/fs');
let io = import('std/io');
```
And that the following file hierarchy exists in the file system:
```
- dir1
 |- foo.txt
 |- bar.txt
 |- dir2
    |- hello.txt
    |- world.txt
```

## Functions
 - [exists](#exists)
 - [open](#open)
 - [walkdir](#walkdir)

## `file` Member Functions
 - [lines](#lines)
 - [read_blocks](#read_blocks)
 - [seek](#seek)
 - [each_line](#each_line)
 - [next](#next)

### exists
```
fs.exists(path: string) -> bool
```
Returns true if the given `path` exists in the file system and false otherwise

Example:
```
io.println(fs.exists('dir1/foo.txt'));
io.println(fs.exists('dir2/foo.txt'));
```

Gives the output:
```
true
false
```

### open
```
fs.open(path: string, mode: string = 'r') -> file
```
Opens the given file `path` using the (optional) `mode`. `mode` can be any of the following:

| Mode | Description                  |
| ---- | ---------------------------- |
| r    | Open a file for reading      |
| w    | Create a file for writing    |
| a    | Append to a file             |
| r+   | Open a file for read/write   |
| w+   | Create a file for read/write |
| a+   | Open a file for read/write   |

Note: Appending 'x' to either 'w' or 'w+' will cause the function to fail if the file already exists. This may prevents overwriting existing files.

Example:
```
let file = fs.open('dir1/foo.txt', 'r');
```

### walkdir
```
fs.walkdir(dir: string, mode: int = WALK_RECURSE, regex: string = '(.*)') -> vector
```
Returns a vector of all file paths in `path` using the (optional) `mode` and `regex`. `mode` can be any combination of the following:

| Mode            | Description           |
| --------------- | --------------------- |
| fs.WALK_FILES   | List only files       |
| fs.WALK_DIRS    | List only directories |
| fs.WALK_RECURSE | Search recursively    |

The default `regex` matches all file names.

Example:
```
# Recursively finds all files in dir1 ending with o.txt
let files = fs.walkdir('dir1', fs.WALK_FILES + fs.WALK_RECURSE, '(.*o\.txt)');
io.println(files);
```

Gives the output:
```
[dir1/foo.txt, dir1/dir2/hello.txt]
```

### lines
```
file.lines() -> vector
```
Returns a vector containing all lines in the file

Example:
```
let file = fs.open('dir1/bar.txt');
io.println(file.lines());
```

Gives output:
```
[My, name, is, John]
```

Given the file `dir1/bar.txt`:
```
My
name
is
John
```

### read_blocks
```
file.read_blocks(begin: string, end: string) -> vector
```
Returns an iterator pointing to the first line, allowing easy vector iteration

Example:
```
import('std/vec');

let file = fs.open('dir1/foo.txt');
let quotes = file.read_blocks('"', '"');
io.println("Quotes found:");
for quote in quotes.each() {
    io.println(" - ", quote);
}
```

Gives output:
```
Quotes found:
 - The greatest glory in living lies not in never falling, but in rising every time we fall.
 - The way to get started is to quit talking and begin doing.
 - Your time is limited, so don't waste it living someone else's life. Don't be trapped by dogma – which is living with the results of other people's thinking.
```

Given the file `dir1/foo.txt`:
```
Top quotes:
"The greatest glory in living lies not in never falling, but in rising every time we fall." -Nelson Mandela
"The way to get started is to quit talking and begin doing." -Walt Disney
"Your time is limited, so don't waste it living someone else's life. Don't be trapped by dogma – which is living with the results of other people's thinking." -Steve Jobs
```

### seek
```
file.seek(offset: int, origin: int) -> int
```
Moves the file position indicator to the given `offset` starting at `origin`. `origin` can be any of the following:

| Origin   | Description           |
| -------- | --------------------- |
| SEEK_SET | Beginning of the file |
| SEEK_CUR | Current file position |
| SEEK_END | End of the file       |

Example:
```
let file = fs.open('dir1/bar.txt');
io.println(file.lines());
file.seek(5, fs.SEEK_SET);
io.println(file.lines());
file.seek(-5, fs.SEEK_END);
io.println(file.lines());
```

Gives the output:
```
[My, name, is, John]
[me, is, John]
[John]
```

Given the file `dir1/bar.txt`:
```
My
name
is
John
```

### each_lines
```
file.each_lines() -> iterator
```
Returns an iterator pointing to the first line, allowing easy vector iteration

Example:
```
let file = fs.open('dir1/bar.txt');
for line in file.each_line() {
    io.println(line);
}
```

Gives output:
```
[My, name, is, John]
```

Given the file `dir1/bar.txt`:
```
My
name
is
John
```

### next
```
iterator.next() -> string
```
Returns the line pointed by the iterator, or `nil` if out of range, and then advances the iterator to the next line

Example:
```
let file = fs.open('dir1/bar.txt');
let iter = file.each_line();
while true {
    let line = iter.next();
    if line != nil {
        io.println(line);
    }
    else {
        break;
    }
}
```

Gives the output:
```
My
name
is
John
```

Given the file `dir1/bar.txt`:
```
My
name
is
John
```