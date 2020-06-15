如何将 C 编译成汇编

```bash
gcc -S main.c -o main.s
```

如何将汇编编译为 object

```bash
gcc -c main.s -o main.o
```

如何链接 object 文件内的 symbols

```bash
gcc main.o -o hello
```

如何编译 intel 格式的汇编代码(默认是 AT&T 的格式)

```bash
gcc -S -masm=intel main.c -o intel-main.s
gcc -S -masm=intel demo2.c -o demo2.s
```

注意, 不同的格式, 指令的参数位置是不一样的. 这会导致理解错误, 比如 add 指令:
```
add src, dest             # GAS(GNU Assembler) Syntax
add dest, src             # Intel Syntax
```
