#type transform

     when int and unsigned is operating :int->usigned int
     tips:小向大，简单向复杂

#gdb gnu调试器

     编译时加-g
	 start:单步执行
	 n：执行下一步
	 run：执行到程序结束
	 break num：在num行设置断点
	 d breakpoints num：删除num行的断点
	 info b：查看断点
	 s：单步执行，有函数调用时会跳至调用的函数内部执行
	 l num：从num行开始打印源程序代码一次打印10行
	 c/continue：从一个断点执行到另一个断点处
	 print n:打印变量n的值
	 start 参数：在gdb中传递命令行参数

#a.c-->a.out的过程
##程序a.out执行时最先执行启动代码，启动代码会生成与该文件相关的堆栈等虚拟地址空间，之后才调用main函数开始执行

    gcc a.c -E -> a.i(a.i是预处理后的.c文件，预处理的作用：头文件展开，宏替换，去注释)
	gcc -s a.c ->a.s(汇编语言的文件)
	gcc a.s -o a.o(ELF文件,但不是可执行文件，是可重新定位目标二进制文件)
	gcc a.c ->a.out(链接之后加有启动代码的机器语言文件)

##objdump -dXxs a.o >temp

    查看反汇编文件信息，>输出重定向

#通用Makefile的书写

    基本格式->目标：依赖
	          (tab)命令

    特殊符号：$@ -> 代表目标
	          $^ -> 代表所有依赖
			  $< -> 代表第一个依赖，一般一个.o只依赖与一个.c文件

	定义变量:CC = gcc   
	         CFLAGS = -Wall -g            编译时的编译选项
			 LDFLAGS                      链接时的选项

	变量的引用:$(CC)
	           $(CFLAGS)

	Makefile的隐式规则：  %.o:%.c 自动将所有的.c转换成对应的.o两者之间有依赖关系

	Makefile的特殊函数：wildcard -> 提取当前文件下的所有.c文件
	           src = (wildcard *.c)
			            patsubst
			   obj = $(patsubst %.c,%.o,$(src)) 将src提取的.c转换成对应的.o

	注意：当前文件下不能有多余的与项目无关的.c文件

##通用Makefile例子

    src = $(wildcard *.c)            
	obj = $(patsubst %.c,%.o,$(src)) 
	CC = gcc
	CFLAGS = -Wall -g
	#LDFLAGS    

	main:$(obj)
	    $(CC) $^ -o $@
	%.o:%.c
		$(CC) $(CFLAGS) $< -c

	.PHONY:clean

	clean:
		rm -rf *.o
		rm -rf main
    
