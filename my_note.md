# c program

     1.echo use printing value
    
     2.make执行成功的前提是当前文件夹中有makefile文件

# visit others machine in the Internet

 1.install ssh software 安装该软件的机器视为服务器，访问者为客户端,访问者不用安装也能访问
 
     sudo apt-get install openssh-server    //软件装好后会自动将访问口打开

 2.visit the server machine

     SSH akaedu@192.168.1.15  //ssh 访问的用户名@访问的IP地址

     退出访问：ctrl-d or exit
 
 3.cp file in server 不用访问主机在本机上直接操作

     scp akaedu@192.168.1.15:~/hihi . //复制akaedu的~下的hihi到本机。.代表本机

 4.sudo service ssh stop  访问口关闭

 5.sudo service ssh start 访问口开启

# vim

    Command = operator + number + motion
                d(elete)  1,2
                y(ank)             gg+G

     要粘贴必须进入插入模式

## open another bash in vim
   
     1.先保存文件即:w

     2.open bash :sh

     3.close bash = ctrl d

     4.退出vim  :q
 
     这种情况下可步关闭vim的情况下编译源程序，方便源程序的修改 

##.vimrc

    home下的创建本机的.vimrc（隐藏文件）文件，该文件是vim的配置文件

    set atuoindent 设置缩进set tabstop=4 设置tab键的长度set expandtab设置tab展开成空格set shiftwidth=4 可视行时shift-v+>展开成空格的个数

    ctrl-t与ctrl-d在插入模式下不对齐

    set dictionary=/usr/share/dirc/words 使用ubuntu自带辞典，使用时插入下ctrl-x-k

     i_ctrl-x-f 补齐路径

     map  用来将指令映射成简单操作或称为快捷键例如：map ,ss :set sepll<cr> ,单词检错。map <tab> :bn 将bn映射未tab   

     imap jj <esc>    将Esc键映射为jj，即用来从插入模式返回至，命令行模式

##words checking

      :set spell    //单词错误检查(非.c文件)，.c文件只检查注释

## V 进入可视行模式后，可用类似windows下的删除粘贴等操作最文件进行删除粘贴等

  1.先用鼠标选中要操作的第一行，然后进入可视行模式，用j移动选中要操作的区域，用dd,y,p等命令操作   

  2.整体缩进几行代码：首先用可视行模式选中这几行，然后>(<相反方向缩进)

##vim snipmate plugin install        snipmate用来用于补全函数for等(tab补全)

      unzip snipMate.zip -d ~/.vim     //解压缩.zip文件到～/.vim中

      vim中的插件安装的实质是将插件复制到.vim中

## ctrl-n is used to aanvulling(补全)command,不仅是当前文件的内容还有包含的头文件的内容

##ctags software  查找函数的定义位置

     install it before uses it.

     ctags file.c     //若应用大工程文件时，ctags main.c file.c file.h 

     之后生成tags文件，tags中存储函数的位置

     在file.c中ctrl+]可从函数调用处跳至函数定义处，ctrl+t回到跳转前的位置

##tar

    tar.gz:tar zcvf dir.tar.gz dir

           tar zxvf dir.tar.gz

    tar.bz:tar jcvf dir.tar.b2z dir

           tar jxvf dir.tar.b2z

##rar file 解压缩   man unrar

    sudo apt-get install unrar
    
    unrar e XXXX.rar

# multiple files 在vim的命令行模式下使用用于vim同时操作的文件(.c)

      :ls #see buffers
    
      :bn #go to next buffer

      :pn #go to previous buffer

      :bd #delete a buffer

# markdown

    http://happypeter.github.com/LGCB/book/toy_markdown.html

### html study

http://www.w3schools.com/

# git

## install

    sudo apt-get install git-core 
    sudo apt-get install tig

## uninstall

    sudo apt-get purge 软件         
    sudo apt-get remove --purge 软件

## install xxx作用类似于tig，查找工程中的字符串并给出具体位置，e可跳转至具体位置

    git clone https://github.com/happypeter/hen.git

    sudo apt-get install libncurses5 libncurses5-dev  添加xxx所需库

    make            // /hen/search/curse

    sudo make install

    eg. xxx times    //查找当前文件中的字符串times, e 可跳至具体位置处
  
##clone others respository

    git clone + 链接(end with .tg)

    git pull    //进入克隆的文件夹内，执行后可更新克隆的仓库

## git basics

1. first create a dir

        mkdir ggg

2. now you MUST cd to this dir

        cd ggg

3. initializing this git dir

        git init

    now you can see a `.git` in this dir

        ls -a

4. now create a file

        vim hello.c

5. let git knows about this file

        git add hello.c

6. create the first version

        git commit -a -m "my first version"   //-a跟踪所有修改-m修改信息，说明性内容，说明为什么修改等

       if want to write too many line messages,the editor must be vim,so in the file of .gitconfig must set:[core] editor = vim. next,when you make commit you should use the command "git commit -a",you can input the message.

       git commit -a -v   //参数-v可在做版本是看到修改的具体内容

7. 上传新版本到仓库
   
        git remote add origin git@github.com:wanggege/my_note.git //给链接起别名

        git push -u origin master        //master是仓库的以部分

8.小结

        每次修改完都要重复执行6和7的第二步,每个文件或工程必须有自己私有的.git仓库，负责github历史就会混乱。

##git branch

 1.git checkout master               //跳转至master分支

  git checkout 版本号               //跳转至commit号对应的历史版本状态

 2.git checkout 版本号 -b branchname  //给对应的版本号起名，并跳转该处

 3.git branch        //查看当前分支

 4.git status       //查看当前分支状态

 5.git branch -D branchname    //delete branch 

 6.git checkout -b tmp   //master备份，也可用2备份

#github

 1.login my github in github website   //https://github.com

 2.add SSH public keys
 
      cd /home/akaedu

      mv .ssh/ akaedu-ssh   

      ssh-keygen(一直enter)

      cd .ssh(复制.ssh中的内容，注意不要复制空格)

      在github网页中的SSH pubilc keys中add即可

 3.creat new repository

      Dashboard->Create A Repository

 4.重复git basics中的7步(若已经有git跟踪的文件可不用执行本步骤)

 5.rename repository

      git remote add origin + 仓库链接(end with .git)

 6.更新版本之后上传至仓库

      git push -u origin master    //master is a part of repository

 7.git config    git配置   //若是已经存在的仓库就不用执行这步

      cd 要上传的文件

      git config --global user.name "wanggege"
  
      git config --global user.email wanggege_bb@163.com

 8. git reset --hard HEAD    //未做版本时撤销上次修改
   
    git reset --hard HEAD^    //做好版本后未push时撤销操作回到以前版本

 9.~/.gitconfig is the configation of git

    alais is used to rename the command.eg,[alais] throw = reset --hard HEAD

    throwh = reset --hard HEAD^     

##about markdown

      markdown文本书写时一定要注意在内容行缩进和与标题之间的空行

#markdown using
 
1.download and install markdown

      sudo apt-get install markdown

 2.creat my .md directory

      vim my_note.md

 3.change .md to .html

      markdown my_note.md > my_note.html

 4.open .html directory

      firefox my_note.html&

##the reason why .swap file appearing
   
   1. open the same file twice sametime
  
   2. close the file unusual

## ref

http://progit.org/

video: search "linus git" at youku.com

# linux basics

Linux is OS(operating system)
OS as linus see it:

OS is nothing but the kernel.

Linux is nothing but the kernel.

ubuntu is Linux + 1000 app.

OS as MS see it:

OS is kernel + desktop env.
# tips

   Clear screen : Ctrl-l

   Copy and Paste: select -> middle button

## language

https://github.com/happypeter/job-akae/wiki

## translation

http://dict.youdao.com/

# shell ( shell is a commandline interpreter)

bash is a kind of shell. 

## where are you(locate command)

     which filename

     locate name   //find file by name

     sudo updatedb  //更新locate数据库

     find XXX|grep filename  //find file in directory by name file name

     ps aux |grep firefox 查找进程firefox的具体信息，ps跟aux一起使用查找当前进程

     kill 进程号   // 杀死进程    kill -9 进程号    //强行杀死进程

##~.bashrc is the configation of bash.alias is used to rename command an so on.it can be used like this:

    alias aaa='sudo apt-get install'

## filesystem tree

    ls

    cd 
    # ~ means your home dir
    cd .. # go to the parent of current dir

    pwd

    man pwd # q to quit

    mkdir dir

    cp copy file,cp -r directory  //递归复制目录

### path

    绝对路径: start with /
    相对路径: start with .

## shell prompt

    peter@cow:~/tg-note$
    user@machinename:currentWorkingDirectory(folder)$

# software installation

    sudo apt-get install tree


# tar 

http://www.happypeter.org/posts/10

# ref

http://happypeter.github.com/LGCB/

http://billie66.github.com/TLCL/book/


## some of my favorite sites

http://www.linfo.org/

http://www.wikipedia.org/

http://news.ycombinator.com/news
