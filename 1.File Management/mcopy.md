## 1.用法

1. mcopy [-bspanvmQT] [-D clash_option] sourcefile targetfile
2. mcopy [-bspanvmQT] [-D clash_option] sourcefile [ sourcefiles... ] targetdirectory
3. mcopy [-tnvm] MSDOSsourcefile

mcopy命令用于在MS-DOS和Unix系统中互相复制文件；

mcopy复制指定名称的文件，或者复制多个文件到指定的目录，源文件和目标文件可以既是MS-DOS或者Unix文件；

指定MS-DOS文件的驱动字符，例如'a:'，决定了转换的方向。如果没有驱动字符指定，则默认是当前目录开始的Unix文件；如果源驱动字符没有附加的文件名，那么将拷贝该驱动上的所有文件；

如果指定了MS-DOS源文件，如("mcopy a:foo.exe")，默认目标是当前目录；

'-'文件名表示标准输入或者输出，命令行中的位置决定它为输入还是输出；

**Options:**

    t      转换为文本文件

    b      批处理模式，这是为大量的文件复制进行最佳化的选项，但是当在复制文件过程中产生crash时，会有安全性的问题产生

    s      递归的复制，包含目录所含文件与其下所有子目录中的文件

    p      将源文件的属性设置为目标文件的属性

    Q      当复制多个文件产生错误时，尽快结束程序

    a      转换为ASCII文本文件

    T      通过字符集进行ASCII文本文件转换

    n      覆盖其他文件时，不需要进行确认而直接覆盖

    m      将源文件的修改时间设置为目标文件的修改时间

    v      显示复制的文件的名称

## 2.示例

**example 1** 将A盘根目录下的autoiexec.bat 拷贝到当前工作目录下，

    mcopy a:autoexec.bat .

**example 2** 当复制的内容包括子目录和文件时，必须使用参数"-/"递归操作，

    mcopy -/ A:\*

## 3.Reference

[Linux mcopy命令](http://www.runoob.com/linux/linux-comm-mcopy.html)
