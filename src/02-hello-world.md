# Hello World!

A simple **hello world** program in Feral can be written as:
```py
let io = import('std/io');
io.println('hello, world');
```

Save the code in a file named, say `hello.fer`, and run it using the `feral` binary which we built in the [installation](./01-install.md) document.
Assuming that no `PREFIX_DIR` was set, the binary would be created in the `build/bin/` directory of the cloned repostory. Hence, the command to run our script would be:
```bash
./build/bin/feral hello.fer
```

This will output `hello world` on the display.

Congratulations! You have successfully written your first program in Feral!

# Additional Notes

The `io.println` function adds a new line at the end of each call, so we did not have to write a new line character (`\n`).
But if we want to explicitly write new line characters wherever required without the function doing that internally,
we can use the `io.print` function for that.

For example, if we want to display multiple statements without newline, using `print`:
```py
io.print('first line');
io.print('second line');
```

The output would be:
```
first linesecond line
```

To correct this, we will add a new line at the end of the first `print` call.
```py
io.print('first line\n');
io.print('second line');
```

which then gives us the correct output:
```
first line
second line
```

One more important thing to add here is that `print` and `println` can take any number of arguments (but at least one for `print`) by separating each argument with a comma (,). So, something like this is possible:
```py
io.println('Hello, ', 'world');
```

Finally, please remember that for using `print(ln)`, the `io` module must be loaded. We will talk about modules later, but from now on,
it will be assumed that wherever `print(ln)` is used, the `io` module has been already imported.

## Conclusion

The `print` function is different from `println` in that it will not automatically add new line character at the end. Also, the `print` function requires at least one argument, whereas the `println` function requires no argument - in which case, it will simply enter a new line. For all other intents and purposes, the `print` and `println` functions are identical.

Next, we are going to dive deeper in the language and understand Feral's variable system.