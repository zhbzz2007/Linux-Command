## 1.用法

将[文件]或标准输入组合输出到标准输出。

    -A, --show-all           等于-vET

    -b, --number-nonblank    对非空输出行编号

    -e                       等于-vE

    -E, --show-ends          在每行结束处显示"$"

    -n, --number             对输出的所有行编号

    -s, --squeeze-blank      不输出多行空行

    -t                       与-vT 等价

    -T, --show-tabs          将跳格字符显示为^I

    -u                       (被忽略)

    -v, --show-nonprinting   使用^ 和M- 引用，除了LFD和 TAB 之外

    --help		               显示此帮助信息并退出

    --version		             显示版本信息并退出

如果没有指定文件，或者文件为"-"，则从标准输入读取。

## 2.示例

    cat f - g  #先输出f 的内容，然后输出标准输入的内容，最后输出g 的内容。

    cat        #将标准输入的内容复制到标准输出。
