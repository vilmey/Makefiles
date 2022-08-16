# Makefiles
Basic Makefile introduction

# Introduction

Directory dedicated to Makefiles

In order to build a project, there are couple of steps that need to be taken in order to generate a binary (executable) image.

Usually the commonly taken path follows the generation of object files '.o' of each source file '.c'. And after that the object files are used to generate a binary image.

```dot
diagram A {
    main.c -> main.o
    message.c -> message.o
    message.o -> output
    main.o -> output
}
```

In order to `main.c` generate `main.o` we call gcc with the -c flag, telling the compiler not to generate an executable. In other words the we only generate the object files and do not perform the linking stage.

`gcc -c main.c -o main.o`
`gcc -c message.c -o message.o`

The linking process is done when all the needed object files are ready.

`gcc main.o message.o -o output`

Separating the build process in this way, it is possible to track changes on each file and only perform build commands when needed, on specific files.
