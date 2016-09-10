## 1.用法

1. lsattr [ -RVadv ] [ files...  ]

显示文件属性，用chattr执行改变文件或目录的属性，可执行lsattr指令查询其属性。

**OPTIONS:**

    -R     递归处理，将指定目录下的所有文件及子目录一并处理

    -a     显示所有文件和目录，包括以"."为名称开头字符的额外内建，现行目录"."与上层目录"."

    -d     显示目录名称而非其内容

    -v    显示文件或目录版本

## 2.示例

**example 1** 用chattr命令放置系统中某个关键文件被修改，

    zhb@zhb-VM:~/Desktop/work/test$ sudo chattr +i test.c
    zhb@zhb-VM:~/Desktop/work/test$ vim test.c
    得到提示，
    -- 插入 -- W10: 警告: 正在修改一个只读文件

    zhb@zhb-VM:~/Desktop/work/test$ sudo chattr +i test.c
    zhb@zhb-VM:~/Desktop/work/test$ lsattr test.c
    ----i--------e-- test.c
    # 要想修改此文件，就把i属性去掉
    zhb@zhb-VM:~/Desktop/work/test$ sudo chattr -i test.c
    zhb@zhb-VM:~/Desktop/work/test$ lsattr test.c
    -------------e-- test.c

**example 2** 让某个文件只能往里面追加数据，但不能删除，适用于各种日志文件，

    chattr +a /patch.log

## 3.Reference

[Linux lsattr命令](http://www.runoob.com/linux/linux-comm-lsattr.html)
