# Loops

Loops are sequences of code that run over and over again, often as long as some condition is specified. They, like functions, help a lot in reducing redundant pieces of code.

For example, if we want to make a multiplication table of 12 from 1 to 10, would we write 10 statements by hand? It would look something like this:
```py
let io = import('std/io');

io.println('12 x 1 = ', 12 * 1);
io.println('12 x 2 = ', 12 * 2);
io.println('12 x 3 = ', 12 * 3);
io.println('12 x 4 = ', 12 * 4);
io.println('12 x 5 = ', 12 * 5);
io.println('12 x 6 = ', 12 * 6);
io.println('12 x 7 = ', 12 * 7);
io.println('12 x 8 = ', 12 * 8);
io.println('12 x 9 = ', 12 * 9);
io.println('12 x 10 = ', 12 * 10);
```
Well, that works I suppose, is it convenient? Nope, but is it really hard? Well, again nope. But think about it. This is just from 1 to 10.
What about 1 to 100? Or 1 to 1000? Yeah, that becomes far more incovenient now. Downright dreadful even.

That's where loops come in to save the day! Using a loop, the above program could be written as:
```py
let io = import('std/io');

for let i = 1; i <= 10; ++i {
	io.println('12 x ', i, ' = ', 12 * i);
}
```
Yep, that's it! And if, say, we want to do this even for 1000, all we have to do is change the `i <= 10` condition to `i <= 1000`, and boom! It's done! This is a really basic example of loops but it should suffice for now.

Feral has 3 kinds of loops:
1. Simple `for` loop
2. `foreach` loop
3. `while` loop

## The `for` Loop
This is probably the most pervasive loop construct across programming languages - for good reason. The `for` loop is also the most dynamic one that can be used in virtually every situation. This form of loop contains 4 components:
1. Initialization - This component is used for initializing the loop, often with some variables - like above we initialized the variable `i` with the value `1`.
2. Execution Condition - This component is used to put a condition till which the loop should run. As long as the condition evaluates to `true`, the loop block will continue to be executed (above, `i <= 10`).
3. Increment/Decrement - This component allows for modification in some value - often to update the variable that is being looped through (above, `++i`) after each execution of the loop block.
4. Loop Block - This is the block of code that is executed as long as the condition of loop holds true.

Aside from loop block, all the other components are optional and we can also skip them all should we want to, which will make for an infinite loop - a loop that never ends.

Needless to say, the loop we wrote for generating table of `12` was a `for` loop.

## The `foreach` Loop
This form of loop is also called a `ranged based for` loop because, you guessed it, it works for a range of items. Although, this is helpful for some use cases, as well as for the purpose of readability, it is also not always feasible. For example, skipping the initialization is not possible using `foreach`. In any case, it's another tool for when it is required.

The above table of 12 from 1 to 10, in terms of `foreach` would be like:
```py
let io = import('std/io');

for i in range(1, 11) {
	io.println('12 x ', i, ' = ', 12 * i);
}
```
Note that we used `1` to `11` in `range()` function, instead of `1` to `10`. This is because `foreach` loop runs till the variable is **less than** the end expression. Therefore we have to increase the expression by one. In this case, the condition in terms of `for` loop would be `i < 11` which actually is equivalent to `i <= 10`.

## The `while` Loop
Imagine `for` loop, but remove the initialization and increment/decrement components. That literally is `while` loop. This loop can be represented by `for` as well, but hey, it's syntactic sugar! It avoids the awkwardness of having two useless semicolons (';') that we have to deal with if we use `for` loop without the initialization and increment/decrement components.

An example of the `while` loop using vectors/lists can be:
```py
let io = import('std/io');
let vec = import('std/vec');

let v = vec.new(1, 2, 3, 4);

while !v.empty() {
	v.pop();
}
```
This is a simple program that just keeps on deleting the last element of the vector until there is nothing left. The same thing, using normal `for` loop would be:
```py
let io = import('std/io');
let vec = import('std/vec');

let v = vec.new(1, 2, 3, 4);

for ; !v.empty(); {
	v.pop();
}
```
Not quite pleasing, is it!

Anyway, that's the fundamentals of loops. Next up, we are going to cover the `member functions` in Feral.