## 1.用法

1. file [OPTION...] [FILE...]

用于探测给定文件的类型，file命令对文件的检查分为文件系统、魔法幻数和语言检查3个过程；

**Options:**

        --help                 信息帮助信息，然后退出

    -v, --version              输出版本信息，然后退出

    -m, --magic-file LIST      指定魔法数字文件

    -z, --uncompress           尝试在压缩文件中查找

    -b, --brief                列出辨识结果时，不显示文件名称

    -c, --checking-printout    详细显示指令执行过程，便于排错或分析程序执行的情形

    -e, --exclude TEST         从测试列表中排除TEST选项，有效的测试有，apptype, ascii, cdf, compress, elf, encoding,soft, tar, text, tokens

    -f, --files-from FILE      指定名称文件，其内容有一个或者多个文件名称时，让file依序辨识这些文件，格式为每列一个文件名称

    -F, --separator STRING     使用字符串替代':'作为分隔符

    -i, --mime                 输出MIME类型字符串
        --apple                输出Apple 创建者/类型
        --mime-type            输出MIME类型
        --mime-encoding        输出MIME编码

    -k, --keep-going           第一次匹配后不终止

    -l, --list                 显示魔法强度

    -L, --dereference          直接显示符号连接所指向的文件类型

    -h, --no-dereference       不显示符号连接所指向的文件类型

    -n, --no-buffer            不缓存输出

    -N, --no-pad               不填充输出

    -0, --print0               用ASCII NULL作为文件名结尾

    -p, --preserve-date        保存文件的获取时间

    -r, --raw                  不可打印字符不转换为 \ooo

    -R, --recursion            设置最大的递归层级

    -s, --special-files        将特殊的文件（块/字符设备）作为常规的设备

    -C, --compile              选择-m选项时，编译文件

    -d, --debug                输出调试信息

## 2.示例

**example 1:** 显示文件类型，

    zhb@zhb-H81-M1:~/Desktop/work$ file 1.txt
    1.txt: ASCII text

    zhb@zhb-H81-M1:~/Desktop/work$ file -b 1.txt#不显示文件名称
    ASCII text

    zhb@zhb-H81-M1:~/Desktop/work$ file -i 1.txt#显示MIME类别
    1.txt: text/plain; charset=us-ascii

    zhb@zhb-H81-M1:~/Desktop/work$ file -b -i 1.txt#不显示文件名称，显示MIME类别
    text/plain; charset=us-ascii

**example 2:** 显示符号连接的文件类型，

    zhb@zhb-H81-M1:~/Desktop/work/test$ ls -l 2.txt
    lrwxrwxrwx 1 zhb zhb 11  9月  2 17:05 2.txt -> temp1/2.txt

    zhb@zhb-H81-M1:~/Desktop/work/test$ file 2.txt
    2.txt: symbolic link to 'temp1/2.txt'

    zhb@zhb-H81-M1:~/Desktop/work/test$ file -L 2.txt#直接显示符号连接所指向的文件类型
    2.txt: ASCII text

    zhb@zhb-H81-M1:~/Desktop/work/test$ file -h 2.txt#不显示符号连接所指向的文件类型
    2.txt: symbolic link to 'temp1/2.txt'

## 3.Reference

[file命令](http://man.linuxde.net/file)
