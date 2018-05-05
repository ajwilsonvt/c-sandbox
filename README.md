# c-sandbox

### write, compile, and run c program

```
vim program.c
clang -o program program.c
./program
```

### hierarchy of code

source code = program.c = very human readable

-> compiler ->

assembly code = program.s = somewhat human readable

-> assembler ->

object code = program.o = machine code not yet linked into complete program

-> linker ->

binary executable = program = machine code + other options and attributes of
the program

**object code & binary executable can be considered machine code**

### generate assembly code

```
clang -S program.c
```

### generate object code

```
clang -c program.c
```

### generate binary executable

```
clang -o program program.c
```

### ELF - executable and linkable format

filename extensions like 
`none, .axf, .bin, .elf, .o, .prx, .puff, .ko, .mod and .so`
are ELF files

### how to view machine code

```
brew install gdb

# run gdb in text user interface mode
gdb -tui program

# dump assembler code for function main
(gdb) disass main
```

### simpler way to view machine code

```
# disassemble, view sections expected to contain instructions
objdump -d program
```

`objdump -s program` reveals the full contents as machine code, but does not
explain the actions

`objdump -d` maps the hexadecimal actions to assembly code

### understanding machine code

https://jvns.ca/blog/2014/09/06/how-to-read-an-executable/

### readelf

can download and use `readelf` to provide more info than `nm`

### hexadecimal and binary

after disassemble using gdb, dump will contain hexadecimal value, eg:

`0x0000000100000f60`, 0x is a prefix indicating a hex value, and is not part of
the value

this hexadecimal value can be shortened to:

`0x100000f60`

hexadecimal broken up into bytes:

`01 00 00 0f 60`

this value corresponds to binary value:

`100000000000000000000111101100000`

binary broken up into bytes (8 bits):

`00000001 00000000 00000000 00001111 01100000`

