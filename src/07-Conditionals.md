# Conditionals

Conditionals are the decision making constructs in programming - and in Feral. In essence, if we want some actions - statements to be executed based on some prerequisites or criteria, we use conditionals.

In Feral, like most languages, conditional construct exists in the format:
```py
if <some expression> {
	# do something;
} elif <perhaps, some other expression> {
	# do some other thing;
} else {
	# oh well, none of the above worked, so let's just do this
}
```

Do note that the `elif` and `else` portions are not mandatory. But the order - first `if`, then `elif`, then `else` is absolute. Also, a conditional can have any number of `elif`s.

`if` states the starting of a conditional. Right after `if`, Feral expects an expression (a set of calculations & function calls that return some value) that evaluates to a boolean value. The boolean, if `true` will cause the block of `if`, which is right after the expression - beginning with an opening brace, to be executed. If the boolean, however, is `false`, the block is not executed. Instead, if there is `elif`, its expression will be checked and this process will continue. If none of the conditions work, and there is an `else` block, that will be executed.

For example,
```py
let io = import('std/io');

let a = 2;
if a == 1 {
	io.println('one');
} elif a == 2 {
	io.println('two');
} else {
	io.println('i dunno');
}
```
In this case, the `elif` block will be executed since `a == 2` will evaluate to `true`.

That's it for conditionals actually. Next up, we'll be learning about the loops (and its types!).