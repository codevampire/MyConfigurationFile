# Makefile文件及GCC编译器使用说明

## Makefile文件说明
```
-k 当make发现错误时仍然继续
-n 输出make将要执行的操作而不实际执行操作
-f makefile 指定make使用的Makefile文件

all 目标，可以用来创建多个目标，是一个伪目标
#  开头为注释
MACRONAME=value 在Makefile中定义宏
$(MACRONAME) 在Makefile中使用宏
${MACRONAME} 在Makefile中使用宏
在make命令行上的宏定义会覆盖Makefile文件中的宏定义

常见的宏:
CC、CFLAGS、INCLUDE
$? 当前目标的依赖人间列表中比当前目标文件新的文件
$@ 当前目标的名字
$< 当前依赖文件的名字
$* 不包括后缀名的当前依赖文件的名字

- 出现在命令之前，make将忽略命令的报错继续执行
@ 出现在命令之前，命令的显示将不出现在标准输出

all 目标为默认目标，如果不指定则执行all目标，新定义的目标如remove、clean、install等如果没有依赖则认为

```
