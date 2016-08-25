**用法：**
1. cp [选项]... [-T] 源文件 目标文件
2. cp [选项]... 源文件... 目录
3. cp [选项]... -t 目录 源文件...

拷贝源文件（可能是多个）到目标路文件；

必选参数对长短选项同时适用。

    -a, --archive               等于-dR --preserve=all
        --attributes-only       仅复制属性而不复制数据
        --backup[=CONTROL       为每个已存在的目标文件创建备份

    -b                          类似--backup 但不接受参数
      --copy-contents           在递归处理是复制特殊文件内容

    -d                          等于--no-dereference --preserve=links

    -f, --force                 如果目标文件不能被打开，删除它，然后重试。如果使用了-n选项，-f选项就会被忽略

    -i, --interactive            覆盖文件之前先询问用户

    -H                           对源文件进行命令行符号链接

    -l, --link                   对源文件建立硬链接，而非复制文件

    -L, --dereference            对源文件进行符号链接

    -n, --no-clobber             不要覆盖已存在的文件(使前面的 -i 选项失效)

    -P, --no-dereference         不跟随源文件中的符号链接

    -p                           等于--preserve=模式,所有权,时间戳
        --preserve[=属性列表      保持指定的属性(默认：模式,所有权,时间戳)，如果可能保持附加属性：环境、链接、xattr 等
        --sno-preserve=属性列表   不保留指定的文件属性
        --parents                复制前在目标目录创建来源文件路径中的所有目录

    -R, -r, --recursive          递归复制目录及其子目录内的所有内容
        --reflink[=WHEN]         控制克隆/CoW 副本。请查看下面的内如
        --remove-destination     尝试打开目标文件前先删除已存在的目的地文件 (相对于 --force 选项)
        --sparse=WHEN            控制创建稀疏文件的方式
        --strip-trailing-slashes 删除参数中所有源文件/目录末端的斜杠

    -s, --symbolic-link          只创建符号链接而不复制文件

    -S, --suffix=后缀             自行指定备份文件的后缀

    -t,  --target-directory=目录	将所有参数指定的源文件/目录复制至目标目录

    -T, --no-target-directory    将目标目录视作普通文件

    -u, --update                 只在源文件比目标文件新，或目标文件不存在时才进行复制

    -v, --verbose                显示详细的进行步骤

    -x, --one-file-system	     不跨越文件系统进行操作

默认情况下，源文件的稀疏性仅仅通过简单的方法判断，对应的目标文件目标文件也
被为稀疏。这是因为默认情况下使用了--sparse=auto 参数。如果明确使用
--sparse=always 参数则不论源文件是否包含足够长的0 序列也将目标文件创文
建为稀疏件。
使用--sparse=never 参数禁止创建稀疏文件。

当指定了--reflink[=always] 参数时执行轻量化的复制，即只在数据块被修改的
情况下才复制。如果复制失败或者同时指定了--reflink=auto，则返回标准复制模式。

备份文件的后缀是'~'，除非设置--suffix 或者 SIMPLE_BACKUP_SUFFIX；版本控制方法可能会通过--backup选项或VERSION_CONTROL环境变量；

    none, off                  不进行备份(即使使用了--backup 选项)

    numbered, t                备份文件加上数字进行排序

    existing, nil              若有数字的备份文件已经存在则使用数字，否则使用普通方式备份

    simple, never              永远使用普通方式备份

有一个特别情况：如果同时指定--force 和--backup 选项，而源文件和目标文件
是同一个已存在的一般文件的话，cp 会将源文件备份。

**示例:**

example 1，不带任何参数下，运行cp；

    zhb@zhb-VM:~/Desktop/work/test$ ll temp1
    总用量 8
    drwxrwxr-x 2 zhb zhb 4096  8月 25 20:47 ./
    drwxrwxr-x 3 zhb zhb 4096  8月 25 20:47 ../
    zhb@zhb-VM:~/Desktop/work/test$ cp 1.txt temp1  #将1.txt拷贝到temp1目录下
    zhb@zhb-VM:~/Desktop/work/test$ ll temp1
    总用量 12
    drwxrwxr-x 2 zhb zhb 4096  8月 25 20:47 ./
    drwxrwxr-x 3 zhb zhb 4096  8月 25 20:47 ../
    -rwxrwxr-x 1 zhb zhb   35  8月 25 20:47 1.txt

example 2，同时拷贝多个文件；

    zhb@zhb-VM:~/Desktop/work/test$ cp 1.txt 2.txt temp1  #同时拷贝多个文件，只需要将多个文件用空格隔开
    zhb@zhb-VM:~/Desktop/work/test$ ll temp1
    总用量 16
    drwxrwxr-x 2 zhb zhb 4096  8月 25 20:49 ./
    drwxrwxr-x 3 zhb zhb 4096  8月 25 20:49 ../
    -rwxrwxr-x 1 zhb zhb   35  8月 25 20:49 1.txt*
    -rwxrwxr-x 1 zhb zhb   35  8月 25 20:49 2.txt

example 3，拷贝一个目录，需要添加-r或-R选项来实现，-r或-R选项表明递归操作，无论该目录是否为空目录，这个选项都是必要的；

    zhb@zhb-VM:~/Desktop/work/test$ ll
    总用量 24
    drwxrwxr-x  4 zhb zhb 4096  8月 25 20:51 ./
    drwxrwxr-x 22 zhb zhb 4096  8月 24 22:01 ../
    -rwxrwxr-x  1 zhb zhb   35  8月 25 20:47 1.txt*
    -rwxrwxr-x  1 zhb zhb   35  8月 25 20:42 2.txt*
    drwxrwxr-x  2 zhb zhb 4096  8月 25 20:49 temp1/
    drwxrwxr-x  2 zhb zhb 4096  8月 25 20:51 temp2/
    zhb@zhb-VM:~/Desktop/work/test$ cp -r temp2 temp1
    zhb@zhb-VM:~/Desktop/work/test$ ll temp1
    总用量 20
    drwxrwxr-x 3 zhb zhb 4096  8月 25 20:51 ./
    drwxrwxr-x 4 zhb zhb 4096  8月 25 20:51 ../
    -rwxrwxr-x 1 zhb zhb   35  8月 25 20:49 1.txt*
    -rwxrwxr-x 1 zhb zhb   35  8月 25 20:49 2.txt*
    drwxrwxr-x 2 zhb zhb 4096  8月 25 20:51 temp2/

example 4，创建文件的硬链接，而不是拷贝它们，拷贝文件意味着你必须使用一些存储空间来存储拷贝的文件，有时候出于某些原因，你可能想要创建“快捷方式”或者链接到文件，而不是拷贝它们，要做到这一点，我们可以使用-l选项；注意，硬链接不能用来创建目录；

    zhb@zhb-VM:~/Desktop/work/test$ ls -lvi *.txt
    1314345 -rwxrwxr-x 1 zhb zhb 35  8月 25 20:47 1.txt
    1314447 -rwxrwxr-x 1 zhb zhb 35  8月 25 20:42 2.txt
    zhb@zhb-VM:~/Desktop/work/test$ cp -l 1.txt temp2
    zhb@zhb-VM:~/Desktop/work/test$ ls -lvi temp2/*.txt
    1314345 -rwxrwxr-x 2 zhb zhb 35  8月 25 20:47 temp2/1.txt

example 5，创建文件的符号链接，也有一种链接叫做软链接或者符号链接，我们用-s选项来实现；创建符号链接只能在当前目录下进行；

    zhb@zhb-VM:~/Desktop/work/test$ cp -s temp2/3.txt 3.txt
    zhb@zhb-VM:~/Desktop/work/test$ ls -l *.txt
    -rwxrwxr-x 2 zhb zhb 35  8月 25 20:47 1.txt
    -rwxrwxr-x 1 zhb zhb 35  8月 25 20:42 2.txt
    lrwxrwxrwx 1 zhb zhb 11  8月 25 21:02 3.txt -> temp2/3.txt

example 6, 不随符号链接拷贝原文件，意思就是只拷贝符号链接文件，可以用-P选项来实现，当对符号链接使用cp命令，它会照原样拷贝它自身；

    zhb@zhb-VM:~/Desktop/work/test$ cp -P 3.txt temp1
    zhb@zhb-VM:~/Desktop/work/test$ ls -l 3.txt
    lrwxrwxrwx 1 zhb zhb 11  8月 25 21:02 3.txt -> temp2/3.txt
    zhb@zhb-VM:~/Desktop/work/test$ ls -l temp1/3.txt
    lrwxrwxrwx 1 zhb zhb 11  8月 25 21:13 temp1/3.txt -> temp2/3.txt

example 7，随符号链接拷贝原文件，-L选项，与-P选项相反；

    zhb@zhb-VM:~/Desktop/work/test$ ls -l 3.txt
    lrwxrwxrwx 1 zhb zhb 11  8月 25 21:02 3.txt -> temp2/3.txt
    zhb@zhb-VM:~/Desktop/work/test$ cp -L 3.txt temp1
    zhb@zhb-VM:~/Desktop/work/test$ ls -l temp1/3.txt
    -rw-rw-r-- 1 zhb zhb 0  8月 25 21:17 temp1/3.txt

example 8，文件归档，当我们去拷贝一个目录时，我们会用-r或-R选项，但是我们也可以用-a选项来归档文件，这样会创建文件和目录的准确套录，如果有的话，也可以包括符号链接，-a选项会保留原文件或目录的属性；

    zhb@zhb-VM:~/Desktop/work/test$ ls -l temp1
    总用量 12
    -rwxrwxr-x 1 zhb zhb   35  8月 25 20:49 1.txt
    -rwxrwxr-x 1 zhb zhb   35  8月 25 20:49 2.txt
    -rw-rw-r-- 1 zhb zhb    0  8月 25 21:17 3.txt
    drwxrwxr-x 2 zhb zhb 4096  8月 25 20:51 temp2
    zhb@zhb-VM:~/Desktop/work/test$ ls -l temp3/temp1
    总用量 12
    -rwxrwxr-x 1 zhb zhb   35  8月 25 20:49 1.txt
    -rwxrwxr-x 1 zhb zhb   35  8月 25 20:49 2.txt
    -rw-rw-r-- 1 zhb zhb    0  8月 25 21:17 3.txt
    drwxrwxr-x 2 zhb zhb 4096  8月 25 20:51 temp2

example 9，显示正在做什么，默认情况下，当拷贝作业成功时，我们仅仅会再次看到命令提示符，如果你想了解在拷贝文件时发生了什么，我们可以用-v选项；

    zhb@zhb-VM:~/Desktop/work/test$ cp -v *.txt temp3
    "1.txt" -> "temp3/1.txt"
    "2.txt" -> "temp3/2.txt"
    "3.txt" -> "temp3/3.txt"
    zhb@zhb-VM:~/Desktop/work/test$ ls -l temp3
    总用量 8
    -rwxrwxr-x 1 zhb zhb 35  8月 25 21:23 1.txt
    -rwxrwxr-x 1 zhb zhb 35  8月 25 21:23 2.txt
    -rw-rw-r-- 1 zhb zhb  0  8月 25 21:23 3.txt

example 10，当原文件较目标文件新时拷贝，我们用-u选项来实现；

    zhb@zhb-VM:~/Desktop/work/test$ ls -l temp3
    总用量 8
    -rwxrwxr-x 1 zhb zhb 35  8月 25 21:23 1.txt
    -rwxrwxr-x 1 zhb zhb 35  8月 25 21:23 2.txt
    -rw-rw-r-- 1 zhb zhb  0  8月 25 21:23 3.txt
    zhb@zhb-VM:~/Desktop/work/test$ ls -l
    总用量 24
    -rwxrwxr-x 2 zhb zhb   35  8月 25 21:25 1.txt
    -rwxrwxr-x 1 zhb zhb   35  8月 25 20:42 2.txt
    lrwxrwxrwx 1 zhb zhb   11  8月 25 21:02 3.txt -> temp2/3.txt
    drwxrwxr-x 3 zhb zhb 4096  8月 25 21:17 temp1
    drwxrwxr-x 2 zhb zhb 4096  8月 25 21:01 temp2
    drwxrwxr-x 2 zhb zhb 4096  8月 25 21:23 temp3
    zhb@zhb-VM:~/Desktop/work/test$ cp -vu *.txt temp3
    "1.txt" -> "temp3/1.txt"

example 11,使用交互模式，交互模式下会询问是否覆盖目标目录下的文件，使用-i选项，启用交互模式；

    zhb@zhb-VM:~/Desktop/work/test$ cp -i 1.txt temp3
    cp：是否覆盖"temp3/1.txt"？ y

example 12,创建备份文件，当目标目录已经含有同名文件，默认情况下cp命令会覆盖目标目录下的同名文件，使用--backup选项，cp命令会为每一个现有的目标文件做一个备份；

    zhb@zhb-VM:~/Desktop/work/test$ ls -l temp3
    总用量 8
    -rwxrwxr-x 1 zhb zhb 35  8月 25 21:28 1.txt
    -rwxrwxr-x 1 zhb zhb 35  8月 25 21:23 2.txt
    -rw-rw-r-- 1 zhb zhb  0  8月 25 21:23 3.txt
    zhb@zhb-VM:~/Desktop/work/test$ cp --backup=simple 1.txt temp3
    zhb@zhb-VM:~/Desktop/work/test$ ls -l temp3
    总用量 12
    -rwxrwxr-x 1 zhb zhb 35  8月 25 21:31 1.txt
    -rwxrwxr-x 1 zhb zhb 35  8月 25 21:28 1.txt~
    -rwxrwxr-x 1 zhb zhb 35  8月 25 21:23 2.txt
    -rw-rw-r-- 1 zhb zhb  0  8月 25 21:23 3.txt

example 13,只拷贝文件属性，cp命令也提供给我们--arrtibutes-only选项，顾名思义，这个选项只会拷贝文件及其属性，不会拷贝任何数据；

    zhb@zhb-VM:~/Desktop/work/test$ ll
    总用量 28
    drwxrwxr-x  5 zhb zhb 4096  8月 25 21:45 ./
    drwxrwxr-x 22 zhb zhb 4096  8月 24 22:01 ../
    -rwxrwxr-x  2 zhb zhb   35  8月 25 21:25 1.txt*
    -rwxrwxr-x  1 zhb zhb   35  8月 25 20:42 2.txt*
    lrwxrwxrwx  1 zhb zhb   11  8月 25 21:02 3.txt -> temp2/3.txt
    drwxrwxr-x  3 zhb zhb 4096  8月 25 21:17 temp1/
    drwxrwxr-x  2 zhb zhb 4096  8月 25 21:01 temp2/
    drwxrwxr-x  2 zhb zhb 4096  8月 25 21:46 temp3/
    zhb@zhb-VM:~/Desktop/work/test$ cp --attributes-only 1.txt -v temp3
    "1.txt" -> "temp3/1.txt"
    zhb@zhb-VM:~/Desktop/work/test$ ll temp3
    总用量 16
    drwxrwxr-x 2 zhb zhb 4096  8月 25 21:46 ./
    drwxrwxr-x 5 zhb zhb 4096  8月 25 21:45 ../
    -rwxrwxr-x 1 zhb zhb    0  8月 25 21:46 1.txt*
    -rwxrwxr-x 1 zhb zhb   35  8月 25 21:28 1.txt~*
    -rwxrwxr-x 1 zhb zhb   35  8月 25 21:23 2.txt*
    -rw-rw-r-- 1 zhb zhb    0  8月 25 21:23 3.txt

example 14,强制拷贝，使用-f选项会强制进行拷贝操作，如果目标文件不能打开，可以用-f尝试一下；

    zhb@zhb-VM:~/Desktop/work/test$ cp -f *.txt -v temp3
    "1.txt" -> "temp3/1.txt"
    "2.txt" -> "temp3/2.txt"
    "3.txt" -> "temp3/3.txt"

example 15,拷贝之前先删除目标，可以用--remove-destination选项实现，这个选项与-f选项形成对照，如果cp命令在目标目录下发现同名文件，cp命令会先删除目标文件，然后再拷贝一份新的；

    zhb@zhb-VM:~/Desktop/work/test$ cp --remove-destination *.txt -v temp3
    已删除"temp3/1.txt"
    "1.txt" -> "temp3/1.txt"
    已删除"temp3/2.txt"
    "2.txt" -> "temp3/2.txt"
    已删除"temp3/3.txt"
    "3.txt" -> "temp3/3.txt"
