**用法：**

1. diff [选项]... FILES

比较单个文件或者目录内容，如果指定比较的是文件，则只有当输入为文本文件时才有效，以逐行的方式，比较文本文件的异同处，如果指定比较的是目录的时候，diff命令会比较两个目录下名字相同的文本文件，列出不同的二进制文件、公共子目录和只在一个目录出现的文件；

必选参数对长短选项同时适用；

        --normal                  输出正常的差异（默认）

    -q, --brief                   仅显示有无差异，不显示详细的信息

    -s, --report-identical-files  若没有发现任何差异，仍然显示信息

    -c, -C NUM, --context[=NUM]   显示全部内容，并标出不同之处

    -u, -U NUM, --unified[=NUM]   以合并的方式来显示文件内容的不同

    -e, --ed                      此参数的输出格式可用于ed的scripts文件

    -n, --rcs                     将比较结果以RCS的格式来显示

    -y, --side-by-side            以并列的方式显示文件的异同之处

    -W, --width=NUM               在使用-y参数时，指定栏宽（默认130）
        --left-column             在使用-y参数时，若两个文件某一行内容相同，则仅在左侧的栏位显示该行内容
        --suppress-common-lines   在使用-y参数时，仅显示不同之处

    -p, --show-c-function         若比较的文件为C语言的程序文件时，显示差异所在的函数名称

    -F, --show-function-line=RE   在上下文和统一格式中，对于每一大块的不同，显示出匹配RE的的一些前面的行
        --label LABEL             使用LABEL而不是文件名，可以重复

    -t, --expand-tabs             输出时将tab字符展开

    -T, --initial-tab             在文本行（无论是常规的或者格式化的前后文关系）前除数tab代替空格
        --tabsize=NUM             tab字符的长度为NUM，默认是8
        --suppress-blank-empty    输出空白行时压缩空格字符或者tab字符

    -l, --paginate                将结果交由pr程序来分页

    -r, --recursive               比较子目录中的文件
        --no-dereference          对符号链接文件不比较

    -N, --new-file                  在目录比较中，如果那个文件只在其中的一个目录中找到，那么它在另一个目录中被视为一个空文件
        --unidirectional-new-file   将缺失文件视为空文件
        --ignore-file-name-case     对比文件名时忽略大小写
        --no-ignore-file-name-case  比较文件名时考虑大小写

    -x, --exclude=PAT               不比较选项中所指定的文件或目录

    -X, --exclude-from=FILE         将文件或目录类型保存为文本文件，然后在=<文件>中指定此文本文件

    -S, --starting-file=FILE        在比较目录时，从指定的文件开始比较
        --from-file=FILE1           对FILE1进行所有的操作，FILE1可以为目录
        --to-file=FILE2             对FILE2进行所有的操作，FILE2可以为目录

    -i, --ignore-case               不检查大小写的不同

    -E, --ignore-tab-expansion      不检查tab字符扩展带来的不同

    -Z, --ignore-trailing-space     不检查行末尾的空格字符带来的不同

    -b, --ignore-space-change       不检查空格字符的不同

    -w, --ignore-all-space          忽略全部的空格字符

    -B, --ignore-blank-lines        不检查空白行

    -I, --ignore-matching-lines=RE  忽略由插入、删除行（由RE参数提供参考）带来的不同

    -a, --text                      diff预设只会逐行比较文本文件
        --strip-trailing-cr         去除行尾的换行

    -D, --ifdef=NAME                此参数的输出格式可用于前置处理器聚集
        --GTYPE-group-format=GFMT   将GTYPE与GFMT合并
        --line-format=LFMT          以LFMT格式处理所有输入行
        --LTYPE-line-format=LFMT    以LFMT处理LTYPE输入行

    -d, --minimal                   使用不同的演算法，以小的单位来做比较
        --horizon-lines=NUM         保持前缀后后缀NUM行
        --speed-large-files         假定大文件中许多小变化

**示例：**

example 1，比较两个文件，

    zhb@zhb-VM:~/Desktop/work/test$ diff temp1/1.txt temp2/1.txt
    3c3
    < Desktop
    ---
    > Mobile
    5a6
    > Ubuntu
    7d7
    < Windows Phone

3c3说明temp1/1.txt与temp2/1.txt第3行不同，5a6说明temp1/1.txt比temp2/1.txt少了"Ubuntu"，7d7说明temp1/1.txt与temp2/1.txt第7行多了"Window Phone"；

diff的normal显示格式有三种提示，

    a - add

    c - change

    d - delete

example 2，并排格式输出，

    zhb@zhb-VM:~/Desktop/work/test$ diff temp1/1.txt temp2/1.txt -y -W 50
    zhb@zhb-VM:~/Desktop/work/test$ diff temp1/1.txt temp2/1.txt -y -W 100
    I use Ubuntu as my work enviroment.     I use Ubuntu as my work enviroment.
    Life is short, use Python.              Life is short, use Python.
    Desktop                               |	Mobile
    Mac OSX                                 Mac OSX
    Windows                                 Windows
                                         >	Ubuntu
    IOS                                     IOS
    Windows Phone                        <
    Android                                 Android

输出格式说明，

    "|"表示前后2个文件内容有不同

    "<"表示后面文件比前面文件少了1行内容

    ">"表示后面文件比前面文件多了1行内容


example 3，上下文输出格式，

    zhb@zhb-VM:~/Desktop/work/test$ diff temp1/1.txt temp2/1.txt -c
    *** temp1/1.txt	2016-08-31 21:19:01.427960075 +0800
    --- temp2/1.txt	2016-08-31 21:19:10.395960119 +0800
    ***************
    *** 1,8 ****
      I use Ubuntu as my work enviroment.
      Life is short, use Python.
    ! Desktop
      Mac OSX
      Windows
      IOS
    - Windows Phone
      Android
    --- 1,8 ----
      I use Ubuntu as my work enviroment.
      Life is short, use Python.
    ! Mobile
      Mac OSX
      Windows
    + Ubuntu
      IOS
      Android

格式说明，

    "+"表示比较的文件的后者比前者多1行

    "-"表示比较的文件的后者比前者少1行

    "!"表示比较的文件有不同的行

example 4,统一格式输出，

    zhb@zhb-VM:~/Desktop/work/test$ diff temp1/1.txt temp2/1.txt -u
    --- temp1/1.txt	2016-08-31 21:19:01.427960075 +0800
    +++ temp2/1.txt	2016-08-31 21:19:10.395960119 +0800
    @@ -1,8 +1,8 @@
     I use Ubuntu as my work enviroment.
     Life is short, use Python.
    -Desktop
    +Mobile
     Mac OSX
     Windows
    +Ubuntu
     IOS
    -Windows Phone
     Android

格式说明，

1.第一部分，也就是文件的基本信息，"---"表示变动前的文件，"+++"表示变动后的文件；

    --- temp1/1.txt	2016-08-31 21:19:01.427960075 +0800

    +++ temp2/1.txt	2016-08-31 21:19:10.395960119 +0800

2.第二部分，变动的位置用两个@表示作为起首和结束，

    @@ -1,8 +1,8 @@

前面的"-1,8"分成三个部分，减号表示第一个文件（即temp1/1.txt），"1"表示第1行，"8"表示连续8行，何在一起，就表示下面是第一个文件从第1行开始的连续8行；同样的，"+1,10"表示变动后，第二个文件从第1行开始的连续10行；

example 5,比较文件夹的不同，

    zhb@zhb-VM:~/Desktop/work/test$ diff temp1 temp2
    diff temp1/1.txt temp2/1.txt
    3c3
    < Desktop
    ---
    > Mobile
    5a6
    > Ubuntu
    7d7
    < Windows Phone
    diff temp1/2.txt temp2/2.txt
    3c3
    < Storm
    ---
    >

example 6,比较两个文件不同，并生产补丁，

    zhb@zhb-VM:~/Desktop/work/test$ diff -ruN temp1/1.txt temp2/1.txt  > patch.log
    zhb@zhb-VM:~/Desktop/work/test$ cat patch.log
    --- temp1/1.txt	2016-08-31 21:19:01.427960075 +0800
    +++ temp2/1.txt	2016-08-31 21:19:10.395960119 +0800
    @@ -1,8 +1,8 @@
     I use Ubuntu as my work enviroment.
     Life is short, use Python.
    -Desktop
    +Mobile
     Mac OSX
     Windows
    +Ubuntu
     IOS
    -Windows Phone
     Android

**Reference:**

[linux命令大全之diff命令详解(比较文件内容)](http://www.jb51.net/LINUXjishu/151930.html)
