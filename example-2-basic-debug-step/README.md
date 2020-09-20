# 如何用  gdb debug C 程序

#### 编译时添加 -g 选项

```bash
gcc -g main.c
```

#### 调用 gdb

```bash
gdb a.out
```

#### 在 gdb 的 shell 内设置 breakpoint

```gdb
break 10
```

#### 在 gdb 的 shell 开始调试

```gdb
run
```

#### 查看当前行

```gdb
frame
```

#### 在 max 函数设置 breakpoint

```gdb
break max
```

#### 在特定文件的特定行号设置 breakpoint

```gdb
break main.c:8
```

#### 按行浏览的时候进入一个子函数流程演示

```gdb
break 12
run
step
```

#### 在 gdb shell 中显示 c 代码和对应的汇编代码

```gdb
disassemble /rm
# /r means raw
# /m means mix
```

#### 将断点打到汇编代码的函数定义处(而不是C语言的函数内部)

```gdb
break *main
```

#### 执行汇编的下一条指令
```gdb
stepi (abbr. si)
```

#### 显示源码和汇编代码

```gdb
# 显示汇编
layout asm
# 显示源码和汇编
layout split
```

#### 参考
- [官方文档](https://sourceware.org/gdb/current/onlinedocs/gdb/)
- [100个gdb小技巧](https://github.com/hellogcc/100-gdb-tips/blob/master/src/index.md)
