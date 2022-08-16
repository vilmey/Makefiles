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

# Some makefile wildcards

A makefile is based on targets, dependencies and rules, as follows

`target: dependencies
    rules`

It is important to notice that Makefiles only accept tabs, so do not use spaces on it.

## $@
 The `$@` references to the target name

## $^
 The `$^` holds the dependencies names

## $(@D)
 Whenever you need the relative path to the file you are working with, this is the wildcard you should use

## Example
 Build a file
```
$(BINARY): $(OBJECTS)
@echo "If the directory ($(@D)) does not exists, create it"
@mkdir -p $(@D)
@echo "Make the binary target ($@) based on the dependency ($^)"
$(CC) -o $@ $^
```

