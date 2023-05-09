# Monty Interpreter in C

Monty 0.98 is a scripting language that is first compiled into Monty byte codes (Just like Python). It relies on a unique stack, with specific instructions to manipulate it. The goal of this project was to create an interpreter for Monty ByteCodes files in C language.


![enter image description here](https://www.holbertonschool.com/holberton-logo.png)


# Synopsis

**Monty byte code files**

Files containing Monty byte codes usually have the  `.m`  extension. Most of the industry uses this standard but it is not required by the specification of the language. There is not more than one instruction per line. There can be any number of spaces before or after the opcode and its argument and the file can contain blank lines (empty or made of spaces only, and any additional text after the opcode or its required argument is not taken into account:

    Example:
    File monty_test.m

```
push 0 Push 0 onto the stack$
push 1 Push 1 onto the stack$

push 2
  push 3
                   pall    


                           
push 4

    push 5    
      push    6        

pall This is the end of our program. Monty is awesome!$
```

**Program Usage:**

The Interpreter must be given a valid Monty byte code file and run in the way:

Usage: `monty file`

As mentioned before, the file extension is optional.

```
Example:

test@ubuntu:~/monty$ cat -e bytecodes/00.m
push 1$
push 2$
push 3$
pall$
test@ubuntu:~/monty$ ./monty bytecodes/00.m
3
2
1
test@ubuntu:~/monty$
```

The bytecodes that can be interpreted by the program are the following:


|Bytecode| Function |
|--|--|
| push | Pushes an element to the stack (Requires an integer argument)|
| pall | Prints all the values on the stack, starting from the top of the stack |
| pint | Prints the value at the top of the stack, followed by a new line |
| pop | Removes the top element of the stack |
| swap | Swaps the top two elements of the stack |
| add | Adds the top two elements of the stack |
| nop | Doesn’t do anything |
| sub | Subtracts the top element of the stack from the second top element of the stack |
| div | Divides the second top element of the stack by the top element of the stack. |
| mul | Multiplies the second top element of the stack with the top element of the stack |
| mod | Computes the rest of the division of the second top element of the stack by the top element of the stack |
| pchar | Prints the char at the top of the stack, followed by a new line |
| pstr | Prints the string starting at the top of the stack, followed by a new line |
| rotl | Rotates the stack to the top |
| rotr | Rotates the stack to the bottom |
| stack | Sets the format of the data to a stack (LIFO). This is the default behavior of the program |
| queue | sets the format of the data to a queue (FIFO) |


**Comments:**

Besides the bytecodes interpreted, the program allows for commentary in the monty files.

For this when the first non-space character of a line is `#`, the line won't be taken into account in execution.


```
Example:

test@ubuntu:~/monty$ cat -e bytecodes/00.m
push 1$
push 2$
#Comment$
push 3$
pall$
test@ubuntu:~/monty$ ./monty bytecodes/00.m
3
2
1
test@ubuntu:~/monty$
```


# Getting Started

These instructions will get you a copy of the project up and running on your local machine (Linux distro) for development and testing purposes.

## Installing

You will need to clone the repository of the project from Github. This will contain the Monty Interpreter program and all of its dependencies. 

    https://github.com/jzamora5/monty.git

After cloning the repository you will have a folder called monty. In here there will be several files that allow the program to work.

The main code of the shell

> main_monty.c

Functions for checking and executing byte codes

> opcode.c / op_funcs1.c / op_funcs2.c /op_funcs3.c / _op_funcs 4.c

Functions for handling doubly linked lists (for stacks and queues)

> dll_funcs.c  

Auxiliary Functions

> aux_funcs1.c 

A header file connecting all functions and global variables
> monty.h 

## Testing


**Compilation:**

In order to test the monty interpreter, you will need to open a terminal in a Linux distribution and go to the folder you just cloned from GitHub. In there, you will need to compile the program, which was tested in GNU GCC 5.5.0 with different error flags such as:

> **-Wall:**  Enables all the warnings about constructions.
> 
> **-Wextra :**  Enables some extra warning flags that are not enabled by  **-Wall**.
> 
> **-Werror:**  Makes all warnings into hard errors.
> 
> **-pedantic:**  Issue all the mandatory diagnostics listed in the C standard.

The compilation code goes as follows:

    test@ubuntu:~/simple_shell$ gcc -Wall -Werror -Wextra -pedantic *.c -o monty

By default, the name of the executable will be **monty**, but you can change it if you desire to do so.

**Execution:**

    test@ubuntu:~/simple_shell$ ./monty monty_file.m

## General Use Examples

```
test@ubuntu:~/monty$ cat bytecodes/01.m 
push 1
push 2
push 3
pall
add
pall

est@ubuntu:~/monty$ ./monty bytecodes/01.m 
3
2
1
5
1
test@ubuntu:~/monty$
```


```
test@ubuntu:~/monty$ cat bytecodes/02.m 
push 72
pchar
test@ubuntu:~/monty$ ./monty bytecodes/02.m 
H
test@ubuntu:~/monty$
```


```
test@ubuntu:~/monty$ cat bytecodes/03.m 
push 1
push 2
push 3
push 4
push 5
push 6
push 7
push 8
push 9
push 0
pall
rotl
pall
test@ubuntu:~/monty$ ./monty bytecodes/03.m 
0
9
8
7
6
5
4
3
2
1
9
8
7
6
5
4
3
2
1
0
test@ubuntu:~/monty$ 
```


## Built with

Ubuntu 14.04, Emacs, Vim, and C language.

## Author

Efita Effiom


## bf Folder

There is some extra files found in the bf folder. These files correspond to different codes written in Brainf*ck programming language.

|File| Function |
|--|--|
| 1000-holberton.bf | Prints the word "Holberton" followed by a new line|
| 1001-add.bf | Adds two 1 digit numbers provided by an user (the result must be < 10) |
|1002-mul.bf | Multiplies two 1 digit numbers provided by an user (the result must be < 10) |
| 1003-mul.bf | Multiplies two 1 digit numbers provided by an user |


In order to run these files, a Brainf*ck interpreter must be used.

