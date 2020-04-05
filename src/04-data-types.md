# Data Types

The data we use and store always has some type. The computer does not really need it, but we do because we don't want to work in binary.
Data types are abstractions over binary sequences which define what kind of data will a variable using a said data type will contain,
and how will that data be represented in memory.

If you have prior experience in programming, you may know very well about this. Data types are ubiquitous across programming and are virtually essential for writing software.
Some common data types are:
```
char (character)
int (integer)
float (floating point)
bool (boolean)
string (sequence of characters)
```

In Feral, the `char` data type does not exist as even a single character, in Feral, is a string.
Therefore, all these data types except `char` are fundamental types in Feral.

However, Feral is a `dynamically typed` language. This means that when we create variables, we do not provide types for the variable.
Instead, these are deduced by the interpreter at run time based on the value that we provide to the variable. There are some pros and cons
to this method. The biggest pro being that writing code is quicker, while the biggest con is that the code may be difficult to understand
at a glance.

For example, if we write something like:
```py
let s = 'hi';
let i = 5;
```
Then, `s` is a variable which is deduced by the interpreter to be of type `string` because the expression `hi` is a string,
whereas `i` is a variable that is deduced by the interpreter to be of type `int` because `5` is an integer.

There are also complex data types in Feral which are created by grouping of fundamental types.
We will understand that in later chapters.

For now, let's understand a bit in-depth about the fundamental data types in Feral.

## Fundamental Types

These data types are always available for the programmer and are easily deduced by the interpreter based on values.
Without these types, a lot of things would not be possible in Feral. For example, if the `int` type was absent,
you would not be able to write any code requiring calculations. Booleans are exceptions to this as you can imitate
the booleans using integers (say, integer `1` for `true`, integer `0` for `false`).

There are some important things to understand about these data types, so let's do that first.

### Integers

Integers represent all the negative and positive numbers in Feral - all the numbers without decimal that is.
Theoretically, it can contain any number in the range: `(-∞,∞)`.

Note that unlike many (especially compiled) languages, numbers are not limited to 32, 64, or even 128 bit.
So yes, you can have as big a number as you like, so long as it fits your system's memory.

For example,
```py
let num = 13721736912389172367234538762354786253478652374587235648923749872394623864;
let negative = -12378126387512836512678358761253871625365412578631263816287357125387123123768162;
```
are both valid integer variables.

### Floats

Floating point numbers are the decimal numbers - any number which is an imperfect fraction.
These are useful when precise mathematical calculations are required, as integers won't provide decimal precision.
As with integers, floating point values can also be arbitrarily long with a very high precision.
For example,
```py
let flt = 13721736912389172367234538.762354786253478652374587235648923749872394623864;
let negative = -123781263875128365.12678358761253871625365412578631263816287357125387123123768162;
```

Do note that to classify a number as floating point, the use of decimal point (.) to signify decimal is a **must**,
even if the number does not actually have anything after the decimal point (.), in which case,
we can simply have a `zero (0)` after that.
For example,
```py
let flt = 12.0;
```

### Bools

Booleans are the `true` and `false` values in Feral. These are used when you want to know something in a yes or no fashion.
The `true` and `false` are special (constant) variables in Feral which signify their respective boolean values.
These two special variables cannot be reassigned and are always available globally throughout the program's life.

For example,
```py
let t = true;
let f = false;
```

### Strings

Strings are, essentially, sequences of characters that are, well, just that! From a single character on your keyboard,
to even entire articles written by you, can be considered and contained in strings. These strings, in Feral, are often referred
to as constant strings (const strings) when they are hardcoded in your code. Strings are also how input is received in Feral,
which will be covered in the next chapter of the book. There are 3 ways to write constant strings in Feral:

1. Enclosing in between single quotes ('\<some string\>')
2. Enclosing in between double quotes ("\<some string\>")
3. Enclosing in between back ticks (\`\<some string\>\`)

All of them are identical and can span multiple lines, but the variety often helps in nested use cases, discussed later in this chapter.
For example,
```pyuby
let s1 = 'string in "single" quotes';
let s2 = "string in 'double' quotes";
let s3 = `string in between back ticks with 'single' and "double" quotes inside`;
```

An important thing to consider is that Feral does interpret some escape sequences. They are:
```
\a - Alert bell
\b - Backspace
\f - Formfeed page break
\n - New line
\r - Carriage return
\t - Tab (horizontal)
\v - Tab (vertical)
\\ - Simple backslash
\" - Simple double quote
\' - Simple single quote
```
We saw these being used in our hello world program for printing newline with the `print` function.

The single, double, and back quoted constant strings, although identical, do exist for a reason - if we enclose a string inside double quotes,
we can use single quotes inside them freely and vice versa. And if we enclose a string in backticks,
we can use single as well as double quotes inside it. If, say, only single quoted constant strings existed,
we would have to continually escape the single quotes inside it to avoid them being considered end of string quotes.
For example:
```py
# here, 'this' will be shown in quotes
io.println('this is a string and \'this\' is literally quoted');
# if we use double quotes, we don't have to use escape sequences
io.println("this is a string and 'this' is literally quoted");
# same thing as above, but quotes are swapped
io.println('this is a string and "this" is literally quoted');
```
As we can see, it can be quite useful to have this style. Also, if we want to use both types of quotes as literals, we could enclose them inside
the back ticks:
```go
io.println(`this is 'a' quoted "string"`);
```

# Conclusion

That should be more than sufficient information about strings at this point. We will learn more as we need.
For now, it's time for the next chapter in which we will learn about taking input from the user!