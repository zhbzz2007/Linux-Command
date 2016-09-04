## 1.用法:

1. find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

find命令用于在指定目录下查找文件，任何位于参数之前的字符串都将被视为欲查找的目录名，如果使用该命令时，不设置任何参数，则find命令将在当前目录下查找子目录与文件，并且将查找到的子目录和文件全部进行显示；

**Options:**

    -amin<分钟>                   查找在指定时间曾被存取过的文件或目录，单位以分钟计算

    -anewer<参考文件或目录>         查找其存取时间较指定文件或目录的存取时间更接近现在的文件或目录；

    -atime<24小时数>               查找在指定时间曾被存取过的文件或目录，单位以24小时计算

    -cmin<分钟>                    查找在指定时间之时被更改过的文件或目录

    -cnewer<参考文件或目录>          查找其更改时间较指定文件或目录的更改时间更接近现在的文件或目录

    -ctime<24小时数>               查找在指定时间之时被更改的文件或目录，单位以24小时计算

    -daystart                     从本日开始计算时间

    -depth                        从指定目录下最深层的子目录开始查找

    -expty                        寻找文件大小为0 Byte的文件，或目录下没有任何子目录或文件的空目录

    -exec<执行指令>                 假设find指令的回传值为True，就执行该指令

    -false                         将find指令的回传值皆设为False

    -fls<列表文件>                  此参数的效果和指定“-ls”参数类似，但会把结果保存为指定的列表文件； -follow：排除符号连接

    -fprint<列表文件>               此参数的效果和指定“-print”参数类似，但会把结果保存成指定的列表文件

    -fprint0<列表文件>              此参数的效果和指定“-print0”参数类似，但会把结果保存成指定的列表文件

    -fprintf<列表文件><输出格式>      此参数的效果和指定“-printf”参数类似，但会把结果保存成指定的列表文件

    -fstype<文件系统类型>            只寻找该文件系统类型下的文件或目录

    -gid<群组识别码>                 查找符合指定之群组识别码的文件或目录

    -group<群组名称>                查找符合指定之群组名称的文件或目录

    -ilname<范本样式>               此参数的效果和指定“-lname”参数类似，但忽略字符大小写的差别

    -iname<范本样式>                此参数的效果和指定“-name”参数类似，但忽略字符大小写的差别

    -inum                          查找符合指定的inode编号的文件或目录

    -ipath<范本样式>                此参数的效果和指定“-path”参数类似，但忽略字符大小写的差别

    -iregex<范本样式>               此参数的效果和指定“-regexe”参数类似，但忽略字符大小写的差别

    -links<连接数目>                查找符合指定的硬连接数目的文件或目录

    -iname<范本样式>                指定字符串作为寻找符号连接的范本样式

    -ls                            假设find指令的回传值为Ture，就将文件或目录名称列出到标准输出

    -maxdepth<目录层级>             设置最大目录层级

    -mindepth<目录层级>             设置最小目录层级

    -mmin<分钟>                     查找在指定时间曾被更改过的文件或目录，单位以分钟计算

    -mount                         此参数的效果和指定“-xdev”相同

    -mtime<24小时数>                查找在指定时间曾被更改过的文件或目录，单位以24小时计算

    -name<范本样式>                 指定字符串作为寻找文件或目录的范本样式

    -newer<参考文件或目录>           查找其更改时间较指定文件或目录的更改时间更接近现在的文件或目录

    -nogroup                       找出不属于本地主机群组识别码的文件或目录

    -noleaf                        不去考虑目录至少需拥有两个硬连接存在

    -nouser                        找出不属于本地主机用户识别码的文件或目录

    -ok<执行指令>                   此参数的效果和指定“-exec”类似，但在执行指令之前会先询问用户，若回答“y”或“Y”，则放弃执行命令

    -path<范本样式>                 指定字符串作为寻找目录的范本样式

    -perm<权限数值>                 查找符合指定的权限数值的文件或目录

    -print                         假设find指令的回传值为Ture，就将文件或目录名称列出到标准输出。格式为每列一个名称，每个名称前皆有“./”字符串

    -print0                        假设find指令的回传值为Ture，就将文件或目录名称列出到标准输出。格式为全部的名称皆在同一行

    -printf<输出格式>               假设find指令的回传值为Ture，就将文件或目录名称列出到标准输出。格式可以自行指定

    -prune                         不寻找字符串作为寻找文件或目录的范本样式

    -regex<范本样式>                指定字符串作为寻找文件或目录的范本样式

    -size<文件大小>                 查找符合指定的文件大小的文件

    -true                          将find指令的回传值皆设为True

    -typ<文件类型>                  只寻找符合指定的文件类型的文件

    -uid<用户识别码>                查找符合指定的用户识别码的文件或目录

    -used<日数>                    查找文件或目录被更改之后在指定时间曾被存取过的文件或目录，单位以日计算

    -user<拥有者名称>               查找符和指定的拥有者名称的文件或目录

    -xdev                         将范围局限在先行的文件系统中

    -xtype<文件类型>                此参数的效果和指定“-type”参数类似，差别在于它针对符号连接检查

默认路径为当前目录；默认表达式为 -print
表达式可能由下列成份组成：操作符、选项、测试表达式以及动作：

    操作符 (优先级递减；未做任何指定时默认使用 -and):
         ( EXPR )   ! EXPR   -not EXPR   EXPR1 -a EXPR2   EXPR1 -and EXPR2
         EXPR1 -o EXPR2   EXPR1 -or EXPR2   EXPR1 , EXPR2

    位置选项 (总是真): -daystart -follow -regextype

    普通选项 (总是真，在其它表达式前指定):
          -depth --help -maxdepth LEVELS -mindepth LEVELS -mount -noleaf
          --version -xdev -ignore_readdir_race -noignore_readdir_race

    测试(N可以是 +N 或-N 或 N):-amin N -anewer FILE -atime N -cmin  
          -cnewer 文件 -ctime N -empty -false -fstype 类型 -gid N -group 名称
          -ilname 匹配模式 -iname 匹配模式 -inum N -ipath 匹配模式 -iregex 匹配模式
          -links N -lname 匹配模式 -mmin N -mtime N -name 匹配模式 -newer 文件
          -nouser -nogroup -path 匹配模式 -perm [+-]访问模式 -regex 匹配模式
          -readable -writable -executable
          -wholename PATTERN -size N[bcwkMG] -true -type [bcdpflsD] -uid N
          -used N -user NAME -xtype [bcdpfls]

    动作: -delete -print0 -printf FORMAT -fprintf FILE FORMAT -print
          -fprint0 FILE -fprint FILE -ls -fls FILE -prune -quit
          -exec COMMAND ; -exec COMMAND {} + -ok COMMAND ;
          -execdir COMMAND ; -execdir COMMAND {} + -okdir COMMAND ;


## 2.示例

**example 1:** 根据文件或者正则表达式进行匹配；

列出当前目录及字母所有文件和文件夹，

    zhb@zhb-VM:~/Desktop/work/test$ find .
    .
    ./1.TXT
    ./temp1
    ./temp1/1.txt
    ./temp1/2.txt
    ./Abc.txt
    ./temp2
    ./temp2/1.txt
    ./temp2/2.txt
    ./patch.log
    ./abc.txt

在当前目录下查找以.txt结尾的文件名，

    zhb@zhb-VM:~/Desktop/work/test$ find . -name "*.txt"
    ./temp1/1.txt
    ./temp1/2.txt
    ./Abc.txt
    ./temp2/1.txt
    ./temp2/2.txt
    ./abc.txt

在当前目录下查找以.txt结尾的文件名，忽略大小写，

    zhb@zhb-VM:~/Desktop/work/test$ find . -iname "*.txt"
    ./1.TXT
    ./temp1/1.txt
    ./temp1/2.txt
    ./Abc.txt
    ./temp2/1.txt
    ./temp2/2.txt
    ./abc.txt

当前目录及子目录下查找所有以.txt和.log结尾的文件，

    zhb@zhb-VM:~/Desktop/work/test$ find . -name "*.txt" -o -name "*.log"
    ./temp1/1.txt
    ./temp1/2.txt
    ./Abc.txt
    ./temp2/1.txt
    ./temp2/2.txt
    ./patch.log
    ./abc.txt

匹配文件路径或者文件，

    zhb@zhb-VM:~/Desktop/work/test$ find . -path "*temp1*"
    ./temp1
    ./temp1/1.txt
    ./temp1/2.txt

基于正则表达式匹配文件路径，

    zhb@zhb-VM:~/Desktop/work/test$ find . -regex ".*\(\.txt\|\.log\)$"
    ./temp1/1.txt
    ./temp1/2.txt
    ./Abc.txt
    ./temp2/1.txt
    ./temp2/2.txt
    ./patch.log
    ./abc.txt

基于正则表达式匹配文件路径，忽略大小写，

    zhb@zhb-VM:~/Desktop/work/test$ find . -iregex ".*\(\.txt\|\.log\)$"
    ./1.TXT
    ./temp1/1.txt
    ./temp1/2.txt
    ./Abc.txt
    ./temp2/1.txt
    ./temp2/2.txt
    ./patch.log
    ./abc.txt

**example 2:** 否定参数，找出当前目录下不是以.txt结尾的文件或者目录，

    zhb@zhb-VM:~/Desktop/work/test$ find . ! -name "*.txt"
    .
    ./1.TXT
    ./temp1
    ./temp2
    ./patch.log

**example 3:** 根据文件类型进行搜索，

    zhb@zhb-VM:~/Desktop/work/test$ find . -type l
    ./2.txt

类型参数列表，

    f 普通文件
    l 符号连接
    d 目录
    c 字符设备
    b 块设备
    s 套接字
    p FIFO

**example 4:** 基于目录深度搜索，向下最大深度限制为3,

    zhb@zhb-VM:~/Desktop/work/test$ find . -maxdepth 3 -type f
    ./1.TXT
    ./temp1/1.txt
    ./temp1/2.txt
    ./Abc.txt
    ./temp2/1.txt
    ./temp2/2.txt
    ./patch.log
    ./abc.txt

搜索出深度距离当前目录至少两个子目录的所有文件，

    zhb@zhb-VM:~/Desktop/work/test$ find . -mindepth 2 -type f
    ./temp1/1.txt
    ./temp1/2.txt
    ./temp2/1.txt
    ./temp2/2.txt

**example 5:** 根据文件时间戳进行搜索，

    find . -type f 时间戳

UNIX/Linux文件系统每个文件都有3个时间戳，

    访问时间  -atime/天，amin/分钟   用户最近一次访问时间
    修改时间  -mtime/天，-mmin/分钟  文件最后一次修改时间
    变化时间  -ctime/天，-cmin/分钟  文件数据元（例如权限等）最后一次修改时间

搜索最近2天内被访问过的所有文件，

    zhb@zhb-VM:~/Desktop/work/test$ find . -type f -atime -2
    ./1.TXT
    ./temp1/1.txt
    ./temp1/2.txt
    ./Abc.txt
    ./patch.log
    ./abc.txt

搜索恰好在3天前被访问过的所有文件，

zhb@zhb-VM:~/Desktop/work/test$ find . -type f -atime 3
./temp2/1.txt
./temp2/2.txt

搜索超过2天内被访问过的所有文件，

    zhb@zhb-VM:~/Desktop/work/test$ find . -type f -atime +2
    ./temp2/1.txt
    ./temp2/2.txt

搜索访问时间超过10分钟的所有文件，

    zhb@zhb-VM:~/Desktop/work/test$ find . -type f -amin +2
    ./1.TXT
    ./temp1/1.txt
    ./temp1/2.txt
    ./Abc.txt
    ./temp2/1.txt
    ./temp2/2.txt
    ./patch.log
    ./abc.txt

找出比1.TXT修改时间更长的所有文件，

    zhb@zhb-VM:~/Desktop/work/test$ find . -type f -newer 1.TXT
    ./Abc.txt
    ./abc.txt

**example 6:** 根据文件大小进行匹配，

    find . -type f -size 文件大小单元

文件大小单元，

    b  块（512字节）
    c  字节
    w  字（2字节）
    k  千字节
    M  兆字节
    G  吉字节

搜索大于10字节的文件，

    zhb@zhb-VM:~/Desktop/work/test$ find . -type f -size +10c
    ./temp1/1.txt
    ./temp1/2.txt
    ./temp2/1.txt
    ./temp2/2.txt
    ./patch.log

搜索等于10字节的文件，

    zhb@zhb-VM:~/Desktop/work/test$ find . -type f -size 113c
    ./temp1/1.txt

**example 7:** 删除匹配文件

删除当前目录下所有的.txt文件

    zhb@zhb-VM:~/Desktop/work/test$ find . -type f -name "*.txt" -delete
    zhb@zhb-VM:~/Desktop/work/test$ ll
    总用量 24
    drwxrwxr-x  5 zhb zhb 4096  9月  3 22:15 ./
    drwxrwxr-x 22 zhb zhb 4096  8月 24 22:01 ../
    -rw-rw-r--  1 zhb zhb    0  9月  3 20:47 1.TXT
    lrwxrwxrwx  1 zhb zhb   11  9月  3 21:50 2.txt -> temp1/2.txt
    -rw-rw-r--  1 zhb zhb  257  8月 31 21:44 patch.log
    drwxrwxr-x  2 zhb zhb 4096  9月  3 22:15 temp1/
    drwxrwxr-x  2 zhb zhb 4096  9月  3 22:15 temp2/
    drwxrwxr-x  2 zhb zhb 4096  9月  3 22:15 temp3/

**example 8:** 根据文件权限/所有权进行匹配，

当前目录下搜索出权限为777的文件，

    zhb@zhb-VM:~/Desktop/work/test$ find . -type f -perm 777
    ./Abc.txt
    ./abc.txt

找出当前目录下权限不是777的txt文件，

    zhb@zhb-VM:~/Desktop/work/test$ find . -type f  -name "*.txt" ! -perm 777
    ./23.txt

找出当前目录用户zhb拥有的所有文件，

    zhb@zhb-VM:~/Desktop/work/test$ find . -type f -user zhb
    ./1.TXT
    ./Abc.txt
    ./23.txt
    ./patch.log
    ./abc.txt

找出当前目录用户组zhb拥有的素有文件，

    zhb@zhb-VM:~/Desktop/work/test$ find . -type f -group zhb
    ./1.TXT
    ./Abc.txt
    ./23.txt
    ./patch.log
    ./abc.txt

**example 9:** 借助-exec选项与其它命令结合使用，

找出当前目录下所有的root的文件，并把所有权更改为用户zhb，本例中，{}用于与-exec选项结合使用来匹配所有文件，然后会被替换为相应的文件名;

    zhb@zhb-VM:~/Desktop/work/test$ find . -type f -user root -exec sudo chown zhb {} \;
    [sudo] password for zhb:
    zhb@zhb-VM:~/Desktop/work/test$ ll
    总用量 24
    drwxrwxr-x  5 zhb zhb 4096  9月  3 22:19 ./
    drwxrwxr-x 22 zhb zhb 4096  8月 24 22:01 ../
    -rw-rw-r--  1 zhb zhb    0  9月  3 20:47 1.TXT
    -rw-rw-r--  1 zhb zhb    0  9月  3 22:19 23.txt
    lrwxrwxrwx  1 zhb zhb   11  9月  3 21:50 2.txt -> temp1/2.txt
    -rwxrwxrwx  1 zhb zhb    0  9月  3 22:17 abc.txt*
    -rwxrwxrwx  1 zhb zhb    0  9月  3 22:17 Abc.txt*
    -rw-rw-r--  1 zhb zhb  257  8月 31 21:44 patch.log
    drwxrwxr-x  2 zhb zhb 4096  9月  3 22:15 temp1/
    drwxrwxr-x  2 zhb zhb 4096  9月  3 22:15 temp2/
    drwxrwxr-x  2 zhb zhb 4096  9月  3 22:15 temp3/

找出当前目录下所有的.txt文件并删除，本例中，-ok与-exec行为一样，不过它会给出提示，是否执行相应的操作；

    zhb@zhb-VM:~/Desktop/work/test$ find . -name "*.txt" -ok rm {} \;< rm ... ./Abc.txt > ? y
    < rm ... ./23.txt > ? y
    < rm ... ./2.txt > ? y
    < rm ... ./abc.txt > ? y
    zhb@zhb-VM:~/Desktop/work/test$ ll
    总用量 24
    drwxrwxr-x  5 zhb zhb 4096  9月  3 23:25 ./
    drwxrwxr-x 22 zhb zhb 4096  8月 24 22:01 ../
    -rw-rw-r--  1 zhb zhb    0  9月  3 20:47 1.TXT
    -rw-rw-r--  1 zhb zhb  257  8月 31 21:44 patch.log
    drwxrwxr-x  2 zhb zhb 4096  9月  3 22:15 temp1/
    drwxrwxr-x  2 zhb zhb 4096  9月  3 22:15 temp2/
    drwxrwxr-x  2 zhb zhb 4096  9月  3 22:15 temp3/

查找当前目录下所有.txt文件并把它们拼接起来写入到all.txt文件中，

    zhb@zhb-VM:~/Desktop/work/test$ cat 23.txt
    23
    zhb@zhb-VM:~/Desktop/work/test$ cat abc.txt
    abc
    zhb@zhb-VM:~/Desktop/work/test$ find . -type f -name "*.txt" -exec cat {} \;> all.txt
    cat: ./all.txt：输入文件是输出文件
    zhb@zhb-VM:~/Desktop/work/test$ cat all.txt
    23
    abc

将1天前的.log文件移动到old目录中，

    zhb@zhb-VM:~/Desktop/work/test$ find . -type f -mtime +1 -name "*.log" -exec cp {} old \;
    zhb@zhb-VM:~/Desktop/work/test$ ll old
    总用量 12
    drwxrwxr-x 2 zhb zhb 4096  9月  4 10:37 ./
    drwxrwxr-x 6 zhb zhb 4096  9月  4 10:36 ../
    -rw-rw-r-- 1 zhb zhb  257  9月  4 10:37 patch.log

找出当前目录下所有的.txt文件并以"File:文件名"的形式打印出来，

    zhb@zhb-VM:~/Desktop/work/test$ find . -type f  -name "*.txt" -exec printf "File:%s\n" {} \;
    File:./all.txt
    File:./23.txt
    File:./abc.txt

因为单行命令参数中-exec参数无法使用多个命令，一下方法可以实现在-exec之后接受多个命令

    -exec ./test.sh {} \;

**example 10:** 搜索但跳出指定的目录

查找当前目录或者子目录下所有.txt文件，但是跳过子目录temp2,

    zhb@zhb-VM:~/Desktop/work/test$ find . -path "./temp2" -prune -o -name "*.txt" -print
    ./Abc.txt
    ./23.txt
    ./2.txt
    ./abc.txt

**example 11:** 其它技巧收集

列出所有长度为0的文件，

    zhb@zhb-VM:~/Desktop/work/test$ find . -empty
    ./1.TXT
    ./temp1
    ./Abc.txt
    ./23.txt
    ./temp2
    ./temp3
    ./abc.txt

## 3.Reference

[find命令](http://man.linuxde.net/find)
