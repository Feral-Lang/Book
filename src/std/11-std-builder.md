# Builder (Deprecated)

The **builder** module defines a `builder_t` type that allows to build and install external modules to be used with Feral

A guide on how to write and build modules for Feral can be read [here](https://medium.com/p/writing-c-modules-for-feral-391c30ac7739?source=email-852839018f8a--writer.postDistributed&sk=b2de39e5f849e75e3b4ea9bdeeb1b4db).

All the given examples assume that the **builder** module was imported using:
```
let builder = import('std/builder');
let io = import('std/io');
let sys = import('std/sys');
```

## Functions
- [new](#new)

## `builder_t` Member Functions
- [Builder (Deprecated)](#builder-deprecated)
  - [Functions](#functions)
  - [`builder_t` Member Functions](#buildert-member-functions)
    - [new](#new)
    - [make_dll](#makedll)
    - [add_comp_opts](#addcompopts)
    - [add_inc](#addinc)
    - [add_lib](#addlib)
    - [add_src](#addsrc)
    - [perform](#perform)

### new
```
builder.new() -> builder_t
```
Creates a new builder with default build settings

Example:
```
let build = builder.new();
io.println(build);
```

Possible output:
```
builder_t{linker_flags:  , lib_flags:  -lferalvm -lgmpxx -lgmp -lmpfr , lib_dirs:  -L/usr/lib -L/usr/local/lib/feral , srcs:  , ccache: /usr/bin/ccache , compiler: g++, is_dll: false, compiler_opts:  -std=c++11 -O2 , inc_dirs:  -I/usr/include }
```

### make_dll
```
builder.make_dll() -> builder_t
```
Indicates that the module should be built as a dynamic library instead of an executable program

Example:
```
let build = builder.new();
io.println("Is DLL? ", build.is_dll, ". Compiler options: ", build.compiler_opts);
build.make_dll();
io.println("Is DLL? ", build.is_dll, ". Compiler options: ", build.compiler_opts);
```

Possible output:
```
Is DLL? false. Compiler options:  -std=c++11 -O2 
Is DLL? true. Compiler options:  -std=c++11 -O2 -shared -fPIC -rdynamic -Wl,-rpath,/home/feral/.feral/lib
```

### add_comp_opts
```
builder.add_comp_opts(opt: string) -> builder_t
```
Adds `opt` to the list of options passed to the compiler

Example:
```
let build = builder.new();
io.println("Compiler options: ", build.compiler_opts);
build.add_comp_opts('-g');
io.println("Compiler options: ", build.compiler_opts);
```

Possible output:
```
Compiler options:  -std=c++11 -O2 
Compiler options:  -std=c++11 -O2 -g
```

### add_inc
```
builder.add_inc(inc_dir: string) -> builder_t
```
Adds `inc_dir` to the list of include directories passed to the compiler

Example:
```
let build = builder.new();
io.println("Include directories: ", build.inc_dirs);
build.add_inc('-I/usr/local/include');
io.println("Include directories: ", build.inc_dirs);
```

Possible output:
```
Include directories:  -I/usr/include 
Include directories:  -I/usr/include -I/usr/local/include 
```

### add_lib
```
builder.add_lib(lib_flag : string, lib_dir = '' : string) -> builder_t
```
Adds `lib_flag` and `lib_dir` to the list of libraries and library directories passed to the compiler

Example:
```
let build = builder.new();
io.println("Libraries and directories \n\t", build.lib_flags, "\n\t", build.lib_dirs);                      
build.add_lib('-lcurl', '-L/usr/local/lib');
io.println("Libraries and directories \n\t", build.lib_flags, "\n\t", build.lib_dirs);
```

Possible output:
```
Libraries and directories 
	 -lferalvm -lgmpxx -lgmp -lmpfr 
	 -L/usr/lib -L/usr/local/lib/feral 
Libraries and directories 
	 -lferalvm -lgmpxx -lgmp -lmpfr -lcurl 
	 -L/usr/lib -L/usr/local/lib/feral -L/usr/local/lib
```

### add_src
```
builder.add_src(src: string) -> builder_t
```
Adds `src` to the list of source files passed to the compiler

Example:
```
let build = builder.new();
io.println("Source files: ", build.srcs);
build.add_src('src/hello.cpp');
io.println("Source files: ", build.srcs);
```

Possible output:
```
Source files:  
Source files:  src/hello.cpp
```

### perform
```
builder.perform(output_file: string, .kw_args) -> int
```
Builds the module and produces the `output_file` binary output and returns zero on success or an error code on failure. The possible keyword arguments are:
- `src`: Additional source files to build. Default if empty
- `inc`: Include files location. Default is `include`
- `lib`: Library files location. Default is `build`
- `bin`: Executable files location. Default is `bin`

The build is also influenced by the following command line arguments:
- `dry` : Dry run
- `install` : Install the module in addition of building it

Example:
```
let build = builder.new().make_dll();
build.add_src('src/learn.cpp');
sys.exit(build.perform('learn'));
```

Possible output:
```
$ feral install
Building ...
=> build/libferallearn.so
Installing ...
=> build/* -> /home/feral/.feral/lib/ ...
Installation successful!
```