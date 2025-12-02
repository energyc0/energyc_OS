# energyc0's OS

This is my hobby OS. It is a quite interesting project where I learned a lot about boot sequence, BIOS, elf-format, x86 architecture, interrupts and more!

![Screenshot from 2025-06-19 15-03-55](https://github.com/user-attachments/assets/a23d1d3a-6b49-48b6-b758-f7c84c75d458)


### How to build on Ubuntu/Debian

Install dependencies.
```bash
$ sudo apt update
$ sudo apt install qemu-system-x86 nasm gdb
```

and run 
```bash
$ make
```

### How to run

```bash
$ make qemu
```

If you want to debug the project run
```bash
$ make debug
```

This will create a local tcp socket with port 1234, you can connect to it using gdb. You need to configure gdb before running it. I recommend using **.gdbinit** file containing:

```
define hook-stop
x/1i $pc
end

target remote localhost:1234
layout split
set architecture i8086
symbol-file build/kernel/kernel.dbg
b kmain
```

Now run
```bash
$ gdb
```

and write ``c`` command.