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
