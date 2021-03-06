定制 shell 提示符
####################################

PS（Prompt Sign）是指命令提示符，在 Linux 环境下 $PS1 是终端提示符，我们可以用预设的一些特殊符号来改变 $PS1 变量。首先，先看一下 $PS1 到变量，本例以 Ubuntu 18 为准：

.. highlight:: none

::

    [Linux]$ echo $PS1
    \[\e]0;\u@\h:\w\a\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\
    [\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$


PS1 变量中各项提示符的含义：

* \\d： 日期
* \\H： 完整的主机名称
* \\h： 仅取主机的第一个名字
* \\t： 显示时间为 24 小时格式，如：HH：MM：SS
* \\T： 显示时间为 12 小时格式
* \\A： 显示时间为 24 小时格式：HH：MM
* \\u： 当前用户的账号名称 
* \\v： BASH 的版本信息
* \\w： 完整的工作路径名
* \\W： 最后一个路径名
* \\#： 下达的第几个命令
* \\$： 提示字符，root 用户为 # ，普通用户为 $

同时可以通过 PS1 变量设置提示符的颜色，在 PS1 中设置字符序列颜色的格式为： ``\[\e[F;Bm\]`` 其中“F”为字体颜色，编号30~37；“B”为背景色，编号40~47。取消设置： ``\[\e[0m\]``

每种字体颜色对应的代码:

*  0=重置
* 30=黑色
* 31=红色
* 32=绿色
* 33=黄色
* 34=蓝色
* 35=洋红
* 36=青色
* 37=白色

**背景颜色对应的代码：**

*  0=重置
* 40=黑色
* 41=红色
* 42=绿色
* 43=黄色
* 44=蓝色
* 45=洋红
* 46=青色
* 47=白色
* 01=高亮显示（常用）
* 04=underline
* 07=反白显示
* 08=不可见

在修改提示符时，可以先临时修改，以查看效果。等满意之后在写入配置文件 ~/.bashrc 中，使效果永久生效。

.. hint::

    PS1 在赋值的时因为值中包含空格所以需要用单引号 ``'`` 把值包起来，同时需要注意，变量与值以等号连结，而且等号两边不能直接接空格

::

    gavin@gavin-ubuntu:~$ PS1='\[\H\]\$ '
    gavin-ubuntu$ PS1='\[\H@\u\]\$ '
    gavin-ubuntu@gavin$ PS1='\[\w\]\$ '
    ~$ cd Documents/
    ~/Documents$ PS1='[\u@\h \w \A #\#]\$ '
    [gavin@gavin-ubuntu ~/Documents 21:17 #6]$ PS1='\u@\W\$ '

    # 个人默认的修改，带颜色版本
    PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\W\[\033[00m\]\$ '
