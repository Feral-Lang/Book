# Functions

## What are Functions

In simple words, functions are groups of statements/instructions that are combined to perform some tasks, and can be used repeatedly. We can say, functions are made to perform an often repetitive set of procedures, multiple times, without having to repeat the procedures.

When we create a function with its group of statements, it is called `function definition`. The group of statements is called
`function body`. And, when we use the function, it is called a `function call`.

We may need to provide functions with some additional data, or retrieve some data from it. For that, we use `function arguments`
and `function return values` respectively.

Now, let's move on to how these functions are implemented in Feral.

## Functions in Feral

Feral allows functions to be written in two different modes, each with two different styles, totalling four total varities for writing functions.
They are:
1. As C++ functions - Since Feral interpreter is written in C++ programming language, its functions can be written in it too, allowing you to bind C++ and Feral, essentially, enabling use of the plethora of C++ libraries.
2. As Feral functions - Feral allows you to write functions in the Feral language itself, which is what you will be doing for the most part and what this guide will elaborate on.

Both of these types have 2 styles each - as plain global functions, and as `pseudo member` functions. We will understand this in more detail but let's first grasp the concepts of simple (plain) functions.

### Our First Function!
In Feral, we define functions using the keyword `fn`. This marks the beginning of a function definition and we then describe the function.
Let's work on this using our dear old `Hello world` example.

Last time, we were able to ask user to enter their name, store it in a variable, and display our hello message to the user in the `Hello, <user>` format.
This time, we will create a function named `hello` to which we will pass the name of the user as an argument and that function will print
the hello message for us.

So, here's the code for that.
```py
let io = import('std/io');
# function definition
let hello = fn(name) {
	io.println('Hello, ', name);
};

let name = io.scan('Enter your name: ');
# function call
hello(name);
```
Do note that variable names can be anything you like. The names given here are **not** set in stone.
But yes, congratulations on making your first function in Feral! Now, to understand what we have written.

Function definitions start with the keyword `fn`. Then comes the argument names for the function within parenthesis - multiple arguments separated by commas and empty parentheses for no argument, and then we have our function body within curly braces.

To use a function, we simply call it by using the function name with parentheses and the actual arguments (our data) within the parentheses.
Again, for no arguments, empty parentheses are required.

Since functions are expressions in Feral, they can be stored in variables too! This is how we assigned an `anonymous function` - a nameless function, to the variable `hello` in this case. Hence, just like any other variable, we can pass this around to functions, as well make a new variable out of it, like so.
```py
let func1 = fn(a, b) {
	return a + b;
};

let func2 = func1; # now func2 is also the same function as func1
```