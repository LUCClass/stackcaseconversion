# Case Conversion a la Stack

In this assignment, you will convert the solution of the case conversion homework to use local variables on the stack. You will write a function called `to_upper` that converts a string from lowercase to uppercase and prints the string. It should not modify the original string--it should instead create a copy the original string and convert the copy to uppercase. The copy will be stored in a local array allocated on the function's stack. I have drawn a stack diagram below.



```
Stack frame for to_upper:

|------------------------------|
| Return address to main (LR)  |  4 bytes
|------------------------------|
| Pointer to original string   |  4 bytes
|------------------------------|
|                              |  Variable
| Copy of original string      |
|                              |
|------------------------------|
```

0. Create your `main` function. Write a prologue and epilogue for `main` to stash and restore the link register. Your main function will call `to_upper`
1. Create a string to be converted to uppercase. The string should be located in the `.data` segment.
2. Create a new function called `to_upper`. Write a prologue and epilogue for `to_upper` to stash and restore the link register (see stack diagram above). This function will have one input: a pointer to the string to convert from lowercase to uppercase. The parameter will be passed to `to_upper` in register `r0`. In your prologue, save the input parameter on the stack frame by pushing `r0`. `to_upper` should do the following things:
    1. Compute the length of the original string by calling `strlen`, which takes one parameter, the string pointer in `r0`. It returns the length of the string in `r0`.
    2. Allocate space on your stack frame to store a copy of the original string. Do this by subtracting the string length from your stack pointer.
    3. Copy the original string into local array using `strcpy`, which takes two parameters: destination pointer in `r0` and source pointer in `r1`.
    4. Convert the copy to uppercase. You can use the same code from your last homework assignment.
    5. Print the uppercase string by calling `puts`.
    6. Collapse the stack frame (epilogue) and return.

