## 1.用法：

1. ln [选项]... [-T] 目标 链接名	(第一种格式)
2. ln [选项]... 目标		(第二种格式)
3. ln [选项]... 目标... 目录	(第三种格式)
4. ln [选项]... -t 目录 目标...	(第四种格式)

为某一个文件在另一个位置建立一个同步的链接；

第一种格式，创建一个到TARGET的链接，名称为LINK_NAME；

第二种格式，在当前目录下创建一个到TARGET的链接；

第三种和第四种格式，在DIRECTORY中创建到每个TARGET的链接；

默认是创建硬链接，软链接需要使用--symbolic选项；默认每个目标（新链接的名称）不应该存在；当创建硬链接时，每个TARGET必须存在；

符号链接可以对任意文本文件保持，如果后者已经解决，一个相关的链接会在它相关的父目录中被解释；

**Options:**

        --backup[=CONTROL]	          为每个已存在的目标文件创建备份文件

    -b                                类似--backup，但不接受任何参数

    -d, -F, --directory               创建指向目录的硬链接(只适用于超级用户)

    -f, --force                       强行删除任何已存在的目标文件

    -i, --interactive                 在删除与destinations同名的文件时先进行询问

    -L, --logical                     解除软链接TARGETs

    -n, --no-dereference              在进行软链接时，将LINK_NAME视为一般的文件

    -P, --physical                    直接进行硬链接

    -r, --relative                    相对链接局部，建立软链接

    -s, --symbolic                    进行软链接

    -S, --suffix=SUFFIX               将备份的文件加上SUFFIX后缀

    -t, --target-directory=DIRECTORY  指定创建链接所在的目录

    -T, --no-target-directory         将LINK_NAME视为一般的文件

    -v, --verbose                     输出每个链接文件的文件名

备份后缀是'~'，除非使用--suffix或者SIMPLE_BACKUP_SUFFIX，可以改变后缀；

版本控制方式通过--backup选项或者通过VERSION_CONTROL环境变量，下面是相应的值，

    none, off       不进行备份(即使使用了--backup 选项)
    numbered, t     备份文件加上数字进行排序
    existing, nil   若有数字的备份文件已经存在则使用数字，否则使用普通方式备份
    simple, never   永远使用普通方式备份

使用-s选项将会忽略-L和-P选项；当TARGET是软链接时，最后的选项指定控制行为默认是-P；

## 2.示例

**example 1:** 为temp1/patch.log创建软链接，如果temp1/patch.log丢失，则patch_link也会失效，

    zhb@zhb-VM:~/Desktop/work/test$ ln -s temp1/patch.log patch_link
    zhb@zhb-VM:~/Desktop/work/test$ ll
    总用量 16
    drwxrwxr-x  3 zhb zhb 4096  9月  7 21:38 ./
    drwxrwxr-x 22 zhb zhb 4096  8月 24 22:01 ../
    lrwxrwxrwx  1 zhb zhb   15  9月  7 21:38 patch_link -> temp1/patch.log
    drwxrwxr-x  2 zhb zhb 4096  9月  7 21:38 temp1/
    -rw-rw-r--  1 zhb zhb  111  9月  6 22:12 test.c

**example 2:** 为temp1/patch.log创建硬链接，patch_hard_link与temp1/patch.log的各类属性都相同，

    zhb@zhb-VM:~/Desktop/work/test$ ln temp1/patch.log patch_hard_link
    zhb@zhb-VM:~/Desktop/work/test$ ll
    总用量 20
    drwxrwxr-x  3 zhb zhb 4096  9月  7 21:40 ./
    drwxrwxr-x 22 zhb zhb 4096  8月 24 22:01 ../
    -rw-rw-r--  2 zhb zhb  257  9月  7 21:38 patch_hard_link
    lrwxrwxrwx  1 zhb zhb   15  9月  7 21:38 patch_link -> temp1/patch.log
    drwxrwxr-x  2 zhb zhb 4096  9月  7 21:38 temp1/
    -rw-rw-r--  1 zhb zhb  111  9月  6 22:12 test.c
    zhb@zhb-VM:~/Desktop/work/test$ ll temp1/
    总用量 12
    drwxrwxr-x 2 zhb zhb 4096  9月  7 21:38 ./
    drwxrwxr-x 3 zhb zhb 4096  9月  7 21:40 ../
    -rw-rw-r-- 2 zhb zhb  257  9月  7 21:38 patch.log

## 3.Reference

[linux上ln命令详细说明](http://www.cnblogs.com/joeblackzqq/archive/2011/03/20/1989625.html)

[Linux ln命令](https://wizardforcel.gitbooks.io/w3school-linux/content/33.html)
