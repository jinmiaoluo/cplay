# 如何用  gdb debug C 程序

## 目录

<!-- vim-markdown-toc GFM -->

* [编译时添加 -g 选项](#编译时添加--g-选项)
* [调用 gdb](#调用-gdb)
* [在 gdb 的 shell 内设置 breakpoint](#在-gdb-的-shell-内设置-breakpoint)
* [在 gdb 的 shell 开始调试](#在-gdb-的-shell-开始调试)
* [查看当前行](#查看当前行)
* [在 max 函数设置 breakpoint](#在-max-函数设置-breakpoint)
* [在特定文件的特定行号设置 breakpoint](#在特定文件的特定行号设置-breakpoint)
* [按行浏览的时候进入一个子函数流程演示](#按行浏览的时候进入一个子函数流程演示)
* [在 gdb shell 中显示 c 代码和对应的汇编代码](#在-gdb-shell-中显示-c-代码和对应的汇编代码)
* [将断点打到汇编代码的函数定义处(而不是C语言的函数内部)](#将断点打到汇编代码的函数定义处而不是c语言的函数内部)
* [执行汇编的下一条指令](#执行汇编的下一条指令)
* [显示源码和汇编代码](#显示源码和汇编代码)
* [重新开始 debug](#重新开始-debug)
* [如何打印内存的值](#如何打印内存的值)
* [打印寄存器内的值](#打印寄存器内的值)
* [打印 jump 对应地址的指令](#打印-jump-对应地址的指令)
* [关闭和开启 TUI](#关闭和开启-tui)
* [命令行参数](#命令行参数)
* [参考](#参考)

<!-- vim-markdown-toc -->

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
# 会进入并依次执行 coroutine 的指令
stepi (abbr. si)
# 不会依次执行 coroutine 的指令. 会直接跳转到返回值处理相关的指令处
nexti (abbr. ni)
```

#### 显示源码和汇编代码

```gdb
# 显示汇编
layout asm
# 显示源码和汇编
layout split
```

#### 重新开始 debug

```gdb
start (abbr: r)
```

#### 如何打印内存的值

```gdb
# 16 进制形式表示数字, 按照字节为基本的单位
x/16xb

# 16 进制形式表示数字, 按照字(4个字节大小. 32 bits)为基本的单位
x/16xw

# 16 进制形式表示数字, 按照大字(8个字节大小. 64 bits)为基本的单位
x/16xg

# 比如要打印 0x88(%rsp) 的值
x/16wb 0x88+$rsp

# 更多的信息见
h x
```

#### 打印寄存器内的值

```gdb
# 有三种方案, 分别是:
p $rcx

info registers rcx

layout regs
```

#### 打印 jump 对应地址的指令

```gdb
# 打印 0x49a6e0 对应的指令
x/i 0x49a6e0
display /i  0x49a6e0

# 打印 0x49a6e0 开始后面3条指令
x/3i 0x49a6e0
display /3i 0x49a6e0
```

#### 关闭和开启 TUI

```gdb
tui disable
tui enable
```

#### 命令行参数

```gdb
set args "your arguments"
run
```

#### 参考
- [官方文档](https://sourceware.org/gdb/current/onlinedocs/gdb/)
- [100个gdb小技巧](https://github.com/hellogcc/100-gdb-tips/blob/master/src/index.md)
