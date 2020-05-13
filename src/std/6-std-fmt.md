# Fmt

The **fmt** module provides string formatting capabilities.

All the given examples assume the following imports:
```
let fmt = import('std/fmt');
let io = import('std/io');
```

## Functions
- [Fmt](#fmt)
  - [Functions](#functions)
    - [template](#template)

### template
```
fmt.template(string) -> string
```
Takes a template string, evaluates it, and returns the final string. Does **not** modify the original string.
A template string contains snippets of code in between the usual string content. These snippets of code must be valid Feral expressions and enclosed between opening and closing **braces** (`{<expression here>}`).

Example:
```
let x = 5, y = 10;
let template_str = '{x} + {y} = {x + y}';
io.println(fmt.template(template_str));
```

Gives the output:
```
5 + 10 = 15
```

Note that to avoid a pair of `{` and `}` being considered as part of template when calling `fmt.template`, just escape the opening brace (`{`) with **double** backslash (`\\` (one for lexer, other for template function)). This will also leave the pair of braces as it is.

Example:
```
let x = 5, y = 10;
let template_str = '\\{x} + \\{y} = {x + y}';
io.println(fmt.template(template_str));
```

Gives the output:
```
{x} + {y} = 15
```

Nested templates are possible as well should they be required.