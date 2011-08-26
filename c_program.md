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
