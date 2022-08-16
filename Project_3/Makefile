# -*- Makefile -*

# Compiler options
# Compiler
CC=gcc
# Include
INCDIRS=-I
# Optimization
OPT=-O0
# Build flags
CFLAGS=-Wall -Wextra -g $(INCDIRS) $(OPT)

# Direcotory structure
# Where the objects will be stored
OBJ_DIR=obj
# Where the executable will reside
BIN_DIR=bin

# Files used on the build
# The source files
CFILES=src/main.c util/message.c
# Direcotry for the objects
OBJECTS=$(OBJ_DIR)/src/main.o $(OBJ_DIR)/util/message.o
# Directory for the binary executable
BINARY=$(BIN_DIR)/output

all: $(BINARY)

$(BINARY): $(OBJECTS)
	@echo "If the directory ($(@D)) does not exists, create it"
	@mkdir -p $(@D)
	@echo "Make the binary target ($@) based on the dependency ($^)"
	$(CC) -o $@ $^

$(OBJ_DIR)/%.o: %.c
	@echo "If the directory ($(@D)) does not exists, create it"
	@mkdir -p $(@D)
	@echo "Create the objects ($@) with the .c files ($^)"
	$(CC) $(CFLAGS) -c -o $@ $^

clean:
	@echo "Clean the objects and the binary file"
	rm -rf $(BINARY) obj/*
