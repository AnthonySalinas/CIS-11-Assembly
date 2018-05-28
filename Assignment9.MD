 Briefly describe the concept of "Stack Frame" (1 through 5 points depending on quality of the answer)
Hint: https://en.wikipedia.org/wiki/X86_calling_conventions

stack frames are frames of data that get pushed onto the stack. For example, in a call stack a stack frame would represent a function call and its argument data. The structure of a stack frame is directly affected by a program’s memory model and its choice
of argument passing convention.

 Briefly describe the concept of a "Calling Convention" (1 through 5 points depending on quality of the answer)
 Why do the book examples always start functions with "push ebp" and "mov ebp,esp" (2 points)
 What is the x64 equivalent to "push ebp" and "mov ebp,esp)" (2 points)
 
 Calling conventions describe the interface of called code as well as the order in which atomic parameters or individual parts of a complex parameter are allocated, how parameters are passed, which registers the called function must preserve for the caller,
and how the task of preparing the stack for a function call is divided between the caller and the callee.
 
 What are the differences between "Microsoft x64 calling convention" and "System V AMD64 ABI calling convention" (2 points)
Hint: https://en.wikipedia.org/wiki/X86_calling_conventions

They both use different registers, and x86 requires a 32bit shadowspace to be reserved. The AMD has a 128 bit safe zone for variables 


void myFunction(int a, int b, int c, int d, int e, int f)  {
  //some code here
}
 Upon entry to myFunction (above), what does the stack look like when using Microsoft x64 calling convention? (3 points)

Hint: https://docs.microsoft.com/en-us/cpp/build/parameter-passing

 Upon entry to myFunction (above), what does the stack look like when using stdcall convention (3 points)

Hint: https://en.wikipedia.org/wiki/X86_calling_conventions
