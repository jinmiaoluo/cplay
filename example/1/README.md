如何将 C 编译成汇编

```bash
gcc -S main.c -o main.S
```

如何将汇编编译为 object

```bash
gcc -c main.S -o main.o
```

如何链接 object 文件内的 symbols

```bash
gcc main.o -o hello
```
