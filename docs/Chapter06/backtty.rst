在终端中把命令放到后台执行
##########################

在终端中执行命令时，在程序命令之后加上 ``&`` 字符，可以启动一个程序并将它放到后台运行。

可以用 ``jobs`` 命令查看后台执行程序的列表，用 ``fg %1`` 将程序拉到前台来（1 为后台的编号，默认为 1 所有 fg = fg %1），这样就可以用 Ctrl-c 来杀死程序。

.. highlight:: none

::

    [me@linuxbox ~]$ xlogo &
    [1] 28236
    [me@linuxbox ~]$ jobs
    [1]+ Running        xlogo &
    [me@linuxbox ~]$ fg %1
    xlogo

如果在输入命令时，忘记加上 ``&`` 字符，又或者在程序执行过程中才发现需要很长的时间执行完程序，那么这时怎么将程序放到后台去执行呢？

只需要两步：

1. Ctrl-z 停止当前进程，并移动到后台。
2. ``bg %1`` 在后台执行程序
