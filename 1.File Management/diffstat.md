## 1.用法

1. diffstat [options] [files]

用来显示diff命令输出信息的柱状图，用以显示diff命令比较两个文件的不同信息，用户也可以直接使用|将diff命令所输出的结果直接送给diffstat命令进行统计结果的显示，使用该命令时，若比较的文件或者子目录不在当前目录下，则应该使用其完整路径，如果在命令行中没有给出文件名，则从标准输入中读取；


**Options:**

    -b      忽略与"Binary files XXX and YYY differ"匹配的行

    -c      在每一行前加上'#'

    -C      增加SGR颜色用于高亮柱状图

    -d      调试 -- 输出很多信息

    -D PATH 指定补丁文件的位置，用于未改变的统计

    -e FILE 将标准错误信息重定向到FILE

    -f NUM  格式化（0=concise，1=normal，2=filled，4=values）

    -h      输出这条消息

    -k      不合并文件名

    -K      决定"only"类型的文件名

    -l      列出文件名

    -m      在修改行中将添加/删除数据合并到块中

    -n NUM  指定文件名长度，指定的长度必须大于或者等于所有文件中最长的文件名

    -N NUM  指定文件名的最大长度

    -o FILE 将标准输出重定向到FILE

    -p NUM  与-n参数相同，但此处的<文件名长度>包括了文件的路径

    -q      对于空的差异，压缩"0 files changed"消息

    -r NUM  指定柱状图的凑整（0=none，1=simple，2=adjusted）

    -R      假设新旧文件交换时路径已经创建

    -s      只显示总结的行

    -S PATH 指定原始文件的位置，用于未改变的统计

    -t      输出一个表格而不是柱状图，逗号分割，

    -u      对输出列表不排序

    -v      如果输出被重定向到文件，显示进程

    -V      输出版本信息

    -w NUM  要输出时栏位的长度


## 2.示例

**example 1:**

    zhb@zhb-virtual-machine:~/Desktop/work/test$ diff temp1  temp2  | diffstat
     1.txt |    4 ++--
     2.txt |    4 ++--
     2 files changed, 4 insertions(+), 4 deletions(-)


## 3.Reference

[diffstat命令](http://man.linuxde.net/diffstat)
