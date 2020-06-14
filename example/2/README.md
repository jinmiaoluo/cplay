如何用  gdb debug C 程序

1. 编译时添加 -g 选项

  ```bash
  gcc -g main.c
  ```

2. 调用 gdb

  ```bash
  gdb a.out
  ```

3. 在 gdb 的 shell 内设置 breakpoint

  ```gdb
  break 10
  ```

4. 在 gdb 的 shell 内执行程序

  ```gdb
  run
  ```

5. 查看当前行

  ```gdb
  frame
  ```

6. 在 max 函数设置 breakpoint

  ```gdb
  break max
  ```

7. 在特定文件的特定行号设置 breakpoint

  ```gdb
  break main.c:8
  ```

8. 按行浏览的时候进入一个子函数流演示

  ```gdb
  break 12
  run
  step
  ```
