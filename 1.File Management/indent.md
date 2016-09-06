## 1.用法

1. indent file [-o outfile ] [ options ]
2. indent file1 file2 ... fileN [ options ]

用于调整C原始代码文件的格式，indent可辨识C的原始代码文件，并加以格式化，以方便阅读；

**Options:**

    -bad或--blank-lines-after-declarations 　         在声明区段或加上空白行

    -bap或--blank-lines-after-procedures 　           在程序或加上空白行

    -bbb或--blank-lines-after-block-comments 　       在注释区段后加上空白行

    -bc或--blank-lines-after-commas 　                在声明区段中，若出现逗号即换行

    -bl或--braces-after-if-line 　                    if(或是else,for等等)与后面执行区段的"{"不同行，且"}"自成一行

    -bli<缩排格数>或--brace-indent<缩排格数> 　          设置{ }缩排的格数

    -br或--braces-on-if-line 　                       if(或是else,for等等)与后面执行跛段的"{"不同行，且"}"自成一行

    -bs或--blank-before-sizeof 　                     在sizeof之后空一格

    -c<栏数>或--comment-indentation<栏数> 　           将注释置于程序码右侧指定的栏位

    -cd<栏数>或--declaration-comment-column<栏数> 　   将注释置于声明右侧指定的栏位

    -cdb或--comment-delimiters-on-blank-lines 　      注释符号自成一行

    -ce或--cuddle-else 　                             将else置于"}"(if执行区段的结尾)之后

    -ci<缩排格数>或--continuation-indentation<缩排格数> 叙述过长而换行时，指定换行后缩排的格数

    -cli<缩排格数>或--case-indentation-<缩排格数> 　     使用case时，switch缩排的格数

    -cp<栏数>或-else-endif-column<栏数> 　              将注释置于else与elseif叙述右侧定的栏位

    -cs或--space-after-cast 　                        在cast之后空一格

    -d<缩排格数>或-line-comments-indentation<缩排格数> 　针对不是放在程序码右侧的注释，设置其缩排格数。

    -di<栏数>或--declaration-indentation<栏数> 　       将声明区段的变量置于指定的栏位

    -fc1或--format-first-column-comments 　           针对放在每行最前端的注释，设置其格式

    -fca或--format-all-comments 　                    设置所有注释的格式

    -gnu或--gnu-style 　                              指定使用GNU的格式，此为预设值

    -i<格数>或--indent-level<格数> 　                  设置缩排的格数

    -ip<格数>或--parameter-indentation<格数> 　        设置参数的缩排格数

    -kr或--k-and-r-style 　                           指定使用Kernighan&Ritchie的格式

    -lp或--continue-at-parentheses 　                 叙述过长而换行，且叙述中包含了括弧时，将括弧中的每行起始栏位内容垂直对其排列

    -nbad或--no-blank-lines-after-declarations 　     在声明区段后不要加上空白行

    -nbap或--no-blank-lines-after-procedures 　       在程序后不要加上空白行

    -nbbb或--no-blank-lines-after-block-comments 　   在注释区段后不要加上空白行

    -nbc或--no-blank-lines-after-commas 　            在声明区段中，即使出现逗号，仍旧不要换行

    -ncdb或--no-comment-delimiters-on-blank-lines 　  注释符号不要自成一行

    -nce或--dont-cuddle-else 　                       不要将else置于"}"之后

    -ncs或--no-space-after-casts 　                   不要在cast之后空一格

    -nfc1或--dont-format-first-column-comments 　     不要格式化放在每行最前端的注释

    -nfca或--dont-format-comments 　                  不要格式化任何的注释

    -nip或--no-parameter-indentation 　               参数不要缩排

    -nlp或--dont-line-up-parentheses 　               叙述过长而换行，且叙述中包含了括弧时，不用将括弧中的每行起始栏位垂直对其排列

    -npcs或--no-space-after-function-call-names 　    在调用的函数名称之后，不要加上空格

    -npro或--ignore-profile 　                        不要读取indent的配置文件.indent.pro

    -npsl或--dont-break-procedure-type 　             程序类型与程序名称放在同一行

    -nsc或--dont-star-comments 　                     注解左侧不要加上星号(*)

    -nsob或--leave-optional-semicolon 　              不用处理多余的空白行

    -nss或--dont-space-special-semicolon 　           若for或while区段仅有一行时，在分号前不加上空格

    -nv或--no-verbosity 　                            不显示详细的信息

    -orig或--original 　                              使用Berkeley的格式

    -pcs或--space-after-procedure-calls 　            在调用的函数名称与"{"之间加上空格

    -psl或--procnames-start-lines 　                  程序类型置于程序名称的前一行

    -sc或--start-left-side-of-comments 　             在每行注释左侧加上星号(*)

    -sob或--swallow-optional-blank-lines 　           删除多余的空白行

    -ss或--space-special-semicolon 　                 若for或swile区段今有一行时，在分号前加上空格

    -st或--standard-output 　                         将结果显示在标准输出设备

    -T 　                                             数据类型名称缩排

    -ts<格数>或--tab-size<格数> 　                     设置tab的长度

    -v或--verbose 　                                  执行时显示详细的信息

## 2.示例

**example 1:** 格式化单个文件，

    zhb@zhb-VM:~/Desktop/work/test$ sed -n l test.c
    #include "stdio.h"$
    $
    int main()$
    {$
        printf("hello world\\n");$
    \tprintf("Hello Ubuntu\\n");$
        return 0;$
    }$

输出，

    zhb@zhb-VM:~/Desktop/work/test$ indent -npro -gnu -i4 -sob -l200 -ss -bl -bli 4 -npsl -bl4 -ts4 test.c
    zhb@zhb-VM:~/Desktop/work/test$ sed -n l test.c
    #include "stdio.h"$
    $
    int main ()$
    {$
    \tprintf ("hello world\\n");$
    \tprintf ("Hello Ubuntu\\n");$
    \treturn 0;$
    }$

**example 2:** 格式化多个文件，

    find . -name "*.[h,c]" -exec indent -npro -gnu -i4 -sob -l200 -ss -bl -bli 4 -npsl -bl4 '{}' \;

**example 3:** 用space代替tab，

    zhb@zhb-VM:~/Desktop/work/test$ find -name "*.[hc]" | xargs perl -pi -e 's/\t/    /g'
    zhb@zhb-VM:~/Desktop/work/test$ sed -n l test.c
    #include "stdio.h"$
    $
    int main ()$
    {$
        printf ("hello world\\n");$
        printf ("Hello Ubuntu\\n");$
        return 0;$
    }$

**example 4:** 删除中间文件，

    zhb@zhb-VM:~/Desktop/work/test$ ll
    总用量 48
    drwxrwxr-x  6 zhb zhb 4096  9月  6 22:12 ./
    drwxrwxr-x 22 zhb zhb 4096  8月 24 22:01 ../
    -rw-rw-r--  1 zhb zhb    0  9月  3 20:47 1.TXT
    -rw-rw-r--  1 zhb zhb    3  9月  3 23:31 23.txt
    -rw-rw-r--  1 zhb zhb    4  9月  3 23:31 abc.txt
    -rw-rw-r--  1 zhb zhb    7  9月  3 23:34 all.txt
    drwxrwxr-x  2 zhb zhb 4096  9月  4 10:37 old/
    -rw-rw-r--  1 zhb zhb  257  8月 31 21:44 patch.log
    drwxrwxr-x  2 zhb zhb 4096  9月  3 22:15 temp1/
    drwxrwxr-x  2 zhb zhb 4096  9月  3 22:15 temp2/
    drwxrwxr-x  2 zhb zhb 4096  9月  3 22:15 temp3/
    -rw-rw-r--  1 zhb zhb  111  9月  6 22:12 test.c
    -rw-rw-r--  1 zhb zhb  108  9月  6 22:11 test.c~
    zhb@zhb-VM:~/Desktop/work/test$ find . -name "*.h~" -exec rm '{}' \; -o -name "*.c~" -exec rm '{}' \;
    zhb@zhb-VM:~/Desktop/work/test$ ll
    总用量 44
    drwxrwxr-x  6 zhb zhb 4096  9月  6 22:13 ./
    drwxrwxr-x 22 zhb zhb 4096  8月 24 22:01 ../
    -rw-rw-r--  1 zhb zhb    0  9月  3 20:47 1.TXT
    -rw-rw-r--  1 zhb zhb    3  9月  3 23:31 23.txt
    -rw-rw-r--  1 zhb zhb    4  9月  3 23:31 abc.txt
    -rw-rw-r--  1 zhb zhb    7  9月  3 23:34 all.txt
    drwxrwxr-x  2 zhb zhb 4096  9月  4 10:37 old/
    -rw-rw-r--  1 zhb zhb  257  8月 31 21:44 patch.log
    drwxrwxr-x  2 zhb zhb 4096  9月  3 22:15 temp1/
    drwxrwxr-x  2 zhb zhb 4096  9月  3 22:15 temp2/
    drwxrwxr-x  2 zhb zhb 4096  9月  3 22:15 temp3/
    -rw-rw-r--  1 zhb zhb  111  9月  6 22:12 test.c

## 3.Reference

[Linux indent命令](http://www.runoob.com/linux/linux-comm-indent.html)

[Linux indent命令](http://www.cnblogs.com/274914765qq/p/5052112.html)
