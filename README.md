# Unveiling the Mysteries of Compilation: The Four Stages in C Programming

Hello, #CProgramming Community!

Today, we're peeling back the layers of the compilation process. Let's take a simple C program, `test.c`, performing a sum operation:

```c
#include <stdio.h>

int main() {
    int a = 5, b = 10;
    printf("Sum is: %d\n", a+b);
    return 0;
}
```

## Let's walk through the four stages of compilation and what you might expect:

### 1. Preprocessing
In this stage, `#include` gets replaced with the contents of the header file `stdio.h`. You can use the `-E` flag to output the preprocessed code:

```bash
gcc -E test.c -o test.i
```

### 2. Compilation
The preprocessed code is turned into assembly instructions specific to your processor. Use the -S flag to output the assembly code:

```bash
gcc -S test.i -o test.s
```

The output test.s will contain the assembly code of our program.

### 3. Assembly
The assembly code is converted into machine instructions (object code). Use the -c flag to output the object code:


```bash
gcc -c test.s -o test.o
```

The file test.o will contain binary code, which is not human-readable but can be inspected using tools like objdump.


`objdump` is a command-line utility that is used to display information about object files, executable files, and shared libraries. It is available on various Unix-like operating systems, including Linux. The basic syntax of objdump is as follows:

```
objdump [options] file
```

Here, file represents the binary file (object file, executable file, or shared library) that you want to analyze with objdump. You can use various options to specify the type of information you want to display and the format in which it should be presented.

Commonly used options with objdump are:

-d or --disassemble: Display the disassembled machine instructions of the code sections in the binary file.
-S or --source: Display the disassembled code interleaved with the corresponding source code if available.
-t or --syms: Display the symbol table, showing the symbols (e.g., functions, variables) defined in the binary file.
-h or --headers: Display the headers and sections of the binary file.
-r or --reloc: Display the relocation entries (if any) in the binary file.
-x or --all-headers: Display more detailed information about headers and sections.
Example usage of objdump:

Display disassembled machine instructions:
```
objdump -d executable_file
```

Display disassembled code interleaved with source code:
```
objdump -S executable_file
```

Display the symbol table:
```
objdump -t executable_file
```

Display headers and sections:
```
objdump -h executable_file
```

These examples assume you have objdump installed on your system, and you replace executable_file with the path to the binary file you want to analyze.


### 4. Linking

All the object files and libraries are linked together to create a single executable:

```bash
gcc test.o -o test
```

The output test is an executable file. You can run it with ./test, and it will print "Sum is: 15".

Demystifying these stages helps us understand what happens under the hood when we compile a C program. It's a vital part of learning C and crucial when debugging and optimizing code.