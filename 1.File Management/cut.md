**用法：**
1. cut [选项]... [文件]...

将每个文件中所选择的部分打印到标准输出；

必选参数对长短选项同时适用；

    -b, --bytes=列表              只选中指定的这些字节

    -c, --characters=列表         只选中指定的这些字符

    -d, --delimiter=分界符        使用指定分界符代替制表符作为区域分界

    -f, --fields=列表             只选中指定的这些域；并打印所有不包含分界符的行，除非-s 选项被指定

    -n(忽略)
        --complement              补全选中的字节、字符或域

    -s, --only-delimited          不打印没有包含分界符的行
        --output-delimiter=字符串	使用指定的字符串作为输出分界符，默认采用输入的分界符

仅使用f -b, -c 或-f 中的一个，每一个列表都是专门为一个类别作出的，或者您可以用逗号隔开要同时显示的不同类别。您的输入顺序将作为读取顺序，每个仅能输入一次；

每种参数格式表示范围如下：

    N         从第1 个开始数的第N 个字节、字符或域

    N-        从第N 个开始到所在行结束的所有字符、字节或域

    N-M       从第N 个开始到第M 个之间(包括第M 个)的所有字符、字节或域

    -M        从第1 个开始到第M 个之间(包括第M 个)的所有字符、字节或域

当没有文件参数，或者文件不存在时，从标准输入读取；


**示例：**

文件内容，

    zhb@zhb-virtual-machine:~/Desktop/work/test$ cat 1.txt
    No Name Mark Percent
    01 tom 69 91
    02 jack 71 87
    03 alex 68 98

example 1,提取每一行的第2个字节，

    zhb@zhb-virtual-machine:~/Desktop/work/test$ cat 1.txt | cut -b 2
    o
    1
    2
    3


example 2,字节定位中，想提取第3,第4,第5和第9个字节，如果使用-b选项，执行此命令时，cut会先把-b后面所有的定位进行从小到大排序，然后再提取；

    zhb@zhb-virtual-machine:~/Desktop/work/test$ cat 1.txt | cut -b3-5,9
    NaM
    to9
    ja7
    al6

example 3,类似于3-5这样的技巧，-3表示从第1个字节到第3个字节，3-表示从第3个字节开始到行尾；

    zhb@zhb-virtual-machine:~/Desktop/work/test$ cat 1.txt | cut -b -3
    No
    01
    02
    03
    zhb@zhb-virtual-machine:~/Desktop/work/test$ cat 1.txt | cut -b 3-
     Name Mark Percent
     tom 69 91
     jack 71 87
     alex 68 98

example 4,-c以字符为单位进行输出，-b以字节单位进行输出，-n用于告诉cut不要将多字节字符拆开；

    zhb@zhb-virtual-machine:~/Desktop/work/test$ cat 2.txt | cut -c 1,2,3,4,5,6
    星期
    星期
    星期
    星期
    zhb@zhb-virtual-machine:~/Desktop/work/test$ cat 2.txt | cut -b 1,2,3,4,5,6
    星期
    星期
    星期
    星期

example 5,设置间隔符，再设置提取第几个域；

    zhb@zhb-virtual-machine:~/Desktop/work/test$ cat 1.txt | cut -d ' ' -f 4
    Percent
    91
    87
    98

example 6,遇到空格和制表符，怎么分辨？如果是制表符，会显示\t符号，如果是空格，就会原样显示；

    zhb@zhb-virtual-machine:~/Desktop/work/test$ cat  cut.txt
    a		1
    b    2
    zhb@zhb-virtual-machine:~/Desktop/work/test$ sed -n l  cut.txt
    a\t\t1$
    b    2$

example 6, -d中用什么符号来设定制表符或者空着，-d选项的默认间隔符就是制表符，当使用制表符的时候，完全可以省略-d选项，直接用-f来取域即可；

    zhb@zhb-virtual-machine:~/Desktop/work/test$ cat cut.txt | cut -f 1
    a
    b

example 7,ps和cut命令配合使用时，最后两行出现重复现象；因为ps|cut会自身创建一个进程，当ps时也会提取这个进程，然后通过管道输出到cut，当cut截取时，就多出一行，之所以会重复上衣航内容，是因为我们恰巧渠道了和上一行内容相同的字符而已，可能相同，也可能不相同；

    zhb@zhb-virtual-machine:~/Desktop/work/test$ ps
      PID TTY          TIME CMD
    12425 pts/1    00:00:00 bash
    16678 pts/1    00:00:00 ps
    zhb@zhb-virtual-machine:~/Desktop/work/test$ ps | cut -b3
    P
    4
    6
    6
