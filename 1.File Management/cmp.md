## 1.用法

1. cmp [选项]... 文件1 [文件2 [SKIP1 [SKIP2]]]

逐字节比较两个文件；

当相互比较的两个文件完全一样时，cmp指令不会显示任何信息；若发现有所差异，预设会标示出第一个不同之处的字符和列数编号；如果一个文件是'-'或者缺失，从标准输入中读取内容；

SKIP1和SKIP2是可以选择的，表示每个文件起始处忽略的字节数（默认是0）；

    -b, --print-bytes                 打印不同的字节

    -i, --ignore-initial=SKIP         忽略输入中前SKIP字节数据

    -i, --ignore-initial=SKIP1:SKIP2  忽略FILE1前SKIP1个字节数据和FILE2前SKIP2个字节数据

    -l, --verbose                     输出不同处的字节数和对应的值

    -n, --bytes=LIMIT                 最多对比LIMIT个字节

    -s, --quiet, --silent             不显示错误信息


SKIP 值可以加上以下的单位：
kB=1000、K=1024、MB=1000000、M=1048576、GB=1000000000、G=1073741824，
还有 T、P、E、Z、Y 如此类推。

如果输入相同，则退出状态为 0；1 表示输入不同；2 表示有错误产生；

## 2.示例

**example 1**

    cmp -b 1.txt 2.txt
    1.txt 2.txt 不同：第 2 行，第 27 字节为  56 .  55 -

**example 2**

    cmp -i 26 1.txt 2.txt
    1.txt 2.txt 不同：第 1 字节，第 1 行
    cmp -i 27 1.txt 2.txt
    //无输出

**example 3**

    cmp -i 26:26 1.txt 2.txt
    1.txt 2.txt 不同：第 1 字节，第 1 行

**example 4**

    cmp -l 1.txt 2.txt
    27  56  55

**example 5**

    cmp -n 26  1.txt 2.txt
    //无
    cmp -n 28  1.txt 2.txt
    1.txt 2.txt 不同：第 27 字节，第 2 行

**example 6**

    cmp -s  1.txt 2.txt
    //无
