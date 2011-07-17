# vim

    Command = operator + number + motion
                d(elete)  1,2
                y(ank)             gg+G

     要粘贴必须进入插入模式

# markdown

    http://happypeter.github.com/LGCB/book/toy_markdown.html

### html study

http://www.w3schools.com/

# git
## install

    sudo apt-get install git-core 
    sudo apt-get install tig

    git pull
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


#github

 1.login my github in github website   //https://github.com

 

##about markdown

   markdown文本书写时一定要注意在内容行缩进和与标题之间的空行

#markdown using
##download and install markdown

   1.sudo apt-get install markdown

##creat my .md directory

   2.vim my_note.md

##change .md to .html

   3.markdown my_note.md > my_note.html

##open .html directory

   4.firefox my_note.html&


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

## filesystem tree

    ls

    cd 
    # ~ means your home dir
    cd .. # go to the parent of current dir

    pwd

    man pwd # q to quit

    mkdir dir

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
