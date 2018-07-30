```
Centos6.4 64位

起因
安装glibc-2.14时候，破坏了libc.so.6文件导致Centos下常用的命令都无法使用

解决方方法
使用命令1
LD_PRELOAD=/lib64/libc-2.12.so ln -s /lib64/libc-2.12.so /lib64/libc.so.6

报错：
libc.so.6 file exists

原因
上面命令是解决libc.so.6文件被误删的情况,此处是libc.so.6文件被破坏

解决方式
在每条命令前加上 LD_PRELOAD=/lib64/libc-2.12.so 前缀，不能使用的命令可以重新使用。例如 LD_PRELOAD=/lib64/libc-2.12.so ls，ls命令可以重新使用。则删除lib64下被破坏libc.so.c文件，再使用LD_PRELOAD=/lib64/libc-2.12.so ln -s /lib64/libc-2.12.so /lib64/libc.so.6，问题解决。

```
