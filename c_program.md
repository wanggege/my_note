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

#静态库和共享库的制作
##静态库

    将a.c b.c c.c 制作成名为mylib的静态库

	1.gcc -c a.c b.c c.c

	2.ar rs libmylib.a a.o b.o c.o

	3.gcc main.c -L. -lmylib -Imylib -o main  //-L .表示在当前目录(即.)查找-lmylib告诉编译器要链接libmylib库，-I选项告诉编译器去哪里找头文件。注意，即使库文件就在当前目录，编译器默认也不会去找的，所以-L.选项不能少

    4.gcc main.c libmylib.a //制作静态库后使用

##共享库的制作

    1.gcc -fPIC a.c b.c c.c  //-fPIC是生成与位置无关文件，静态库具有与位置无关性

	2.gcc -shared -o libmylib.so a.o b.o c.o //生成共享库mylib

	3.gcc main.c -g -L . -lmylib -I. -o main//参数作用同上

	4.修改库路径

	     <1> export LD_LIBRARY_PATH=pwd    pwd指库所在的绝对路径
		 <2>sudo cp mylib.so /usr/lib   
		 <3>sudo vim /etc/ld.so.conf
		    添加库路径到该文件
			sudo ldconfig -v 更新库路径并查看更新

    参考资料
file:///home/akaedu/%E6%A1%8C%E9%9D%A2/html-chunk/ch20s04.html
