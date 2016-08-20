**用法：**

1. chmod [选项]... 模式[,模式]... 文件...

2. chmod [选项]... 八进制模式 文件...

3. chmod [选项]... --reference=参考文件 文件...

修改每个文件为指定模式，如果如果有--reference"选项，将每个文件的模式修改为参考文件RFILE的模式；

    -c, --changes          与-v类似，仅仅发生改变时输出调试信息

    -f, --silent, --quiet  不显示错误信息

    -v, --verbose          运行时显示详细的处理信息
        --no-preserve-root 正常对待根目录 '/'
        --preserve-root    在根目录上不执行递归操作
        --reference=RFILE  使用RFILE的模式而非指定的模式

    -R, --recursive        处理指定目录以及其子目录下的所有文件

**示例：**

    chgrp 0777 1.txt        #将 1.txt 的模式更改为"777"

    chgrp -R 0777 /u        #将 /u 及其子目录下所有文件的属性更改为"777"
