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
