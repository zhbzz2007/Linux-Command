## 1.用法

1. mattrib [-a|+a] [-h|+h] [-r|+r] [-s|+s] [-/]   [-p]  [-X]  msdosfile  [
msdosfiles ... ]

matrrib用于修改MSDOS文件属性，使用'+'操作符设定MS-DOS文件属性标志位，使用'-'操作符除去MS-DOS文件属性标志位；

**Options:**

    a      -a/+a除去/设定备份属性

    r      -r/+r除去/设定只读属性

    s      -s/+s除去/设定系统属性

    h      -h/+h除去/设定隐藏属性

    Mattrib支持如下命令行标志位

    /      递归的处理所有子目录下的文件

    X      以较短的格式输出结果

    p      设定重播模式

## 2.示例

**example 1** 列出A槽MS-DOS格式磁盘上所有文件的属性，

    matrrib a:

**example 2** 除去A槽磁片上msdos.sys文件的隐藏、系统与只读属性，

    matrrib -h -s -r a:msdos.sys

**example 3** 除去A槽磁片上包含子目录下所有文件的只读属性，

    matrrib -r -/ a:*.*

## 3.Reference

[Linux mattrib命令](http://www.runoob.com/linux/linux-comm-mattrib.html)
