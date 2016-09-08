## 1.用法

1. less [参数] 文件

与more命令功能类似，可以随意浏览文件，但是more仅能向前移动，不能向后移动，less在查看之前不会加载整个文件；

**Options:**

    -a  ........  --search-skip-screen                      跳跃式搜索当前屏幕
    -A  ........  --SEARCH-SKIP-SCREEN                      从目标行开始搜索
    -b [N]  ....  --buffers=[N]                             设置缓冲区的大小
    -B  ........  --auto-buffers                            针对管道，不自动定位缓冲
    -c  ........  --clear-screen                            通过清理屏幕重新显示而不是回滚
    -d  ........  --dumb                                    基本的终端
    -D [xn.n]  .  --color=xn.n                              设置屏幕颜色（MS-DOS）
    -e  -E  ....  --quit-at-eof  --QUIT-AT-EOF              当文件显示结束后，自动离开
    -f  ........  --force                                   强制打开特殊文件，例如外围设备、目录和二进制文件
    -F  ........  --quit-if-one-screen                      如果整个文件适应第一屏幕，就退出
    -g  ........  --hilite-search                           只标记最后搜索的关键词
    -G  ........  --HILITE-SEARCH                           不标记任何搜索的关键词
    -h [N]  ....  --max-back-scroll=[N]                     向后回滚限制
    -i  ........  --ignore-case                             不包含大写的搜索时忽略大小写
    -I  ........  --IGNORE-CASE                             所有的搜索中忽略大小写
    -j [N]  ....  --jump-target=[N]                         目标行在屏幕的位置
    -J  ........  --status-column                           在屏幕左边显示状态栏
    -k [file]  .  --lesskey-file=[file]                     使用lesskey文件
    -K            --quit-on-intr                            退出less，与Ctrl-C对应
    -L  ........  --no-lessopen                             忽略LESSOPEN环境变量
    -m  -M  ....  --long-prompt  --LONG-PROMPT              设置查询格式
    -n  -N  ....  --line-numbers  --LINE-NUMBERS            不显示行号
    -o [file]  .  --log-file=[file]                         标准输入时，将less输出的内容保存到日志文件中
    -O [file]  .  --LOG-FILE=[file]                         无条件地将less输出的内容重写到日志文件
    -p [pattern]  --pattern=[pattern]                       在命令行中，从指定模式开始
    -P [prompt]   --prompt=[prompt]                         定义一个新的查询
    -q  -Q  ....  --quiet  --QUIET  --silent --SILENT       退出less命令
    -r  -R  ....  --raw-control-chars  --RAW-CONTROL-CHARS  输出原始的控制字符
    -s  ........  --squeeze-blank-lines                     将连续多个空行压缩成一行显示
    -S  ........  --chop-long-lines                         在单行显示较长的内容，而不换行显示
    -t [tag]  ..  --tag=[tag]                               查找tag
    -T [tagsfile] --tag-file=[tagsfile]                     使用另一个tag文件
    -u  -U  ....  --underline-special  --UNDERLINE-SPECIAL  改变会退格键的处理方式
    -w  ........  --hilite-unread                           在向前的屏幕中标记最新的一行
    -W  ........  --HILITE-UNREAD                           向前的动作后标记最新的一行
    -x [N[,...]]  --tabs=[N[,...]]                          将tab字符显示为指定个数的空格字符
    -X  ........  --no-init                                 不使用终端初始/结束字符串
    -y [N]  ....  --max-forw-scroll=[N]                     前向回滚限制
    -z [N]  ....  --window=[N]                              设置窗口的尺寸
    -" [c[c]]  .  --quotes=[c[c]]                           设置shell的引用字符
    -~  ........  --tilde                                   不显示末尾的波浪符号
    -# [N]  ....  --shift=[N]                               水平回滚数量（0为屏幕宽度的一半）
        ........  --no-keypad                               不向终端发送键盘初始/结束字符串
        ........  --follow-name                             如果输入文件重命名，F命令修改文件

## 2.示例

**example 1** 查看文件内容，

    zhb@zhb-H81-M1:~/Desktop/work/test$ less 1.txt
    Ubuntu
    Spark
    Hadoop

**example 2** ps查看进程信息并通过less分页显示，

    zhb@zhb-H81-M1:~/Desktop/work/test$ ps -ef | less
    UID        PID  PPID  C STIME TTY          TIME CMD
    root         1     0  0 08:33 ?        00:00:00 /sbin/init
    root         2     0  0 08:33 ?        00:00:00 [kthreadd]
    root         3     2  0 08:33 ?        00:00:00 [ksoftirqd/0]
    root         4     2  0 08:33 ?        00:00:00 [kworker/0:0]
    root         5     2  0 08:33 ?        00:00:00 [kworker/0:0H]
    root         7     2  0 08:33 ?        00:00:09 [rcu_sched]
    root         8     2  0 08:33 ?        00:00:00 [rcu_bh]
    root         9     2  0 08:33 ?        00:00:09 [rcuos/0]
    root        10     2  0 08:33 ?        00:00:00 [rcuob/0]
    root        11     2  0 08:33 ?        00:00:00 [migration/0]
    root        12     2  0 08:33 ?        00:00:00 [watchdog/0]
    root        13     2  0 08:33 ?        00:00:00 [watchdog/1]
    root        14     2  0 08:33 ?        00:00:00 [migration/1]
    root        15     2  0 08:33 ?        00:00:00 [ksoftirqd/1]
    root        16     2  0 08:33 ?        00:00:00 [kworker/1:0]
    root        17     2  0 08:33 ?        00:00:00 [kworker/1:0H]
    root        18     2  0 08:33 ?        00:00:00 [rcuos/1]
    root        19     2  0 08:33 ?        00:00:00 [rcuob/1]
    root        20     2  0 08:33 ?        00:00:00 [watchdog/2]
    root        21     2  0 08:33 ?        00:00:00 [migration/2]
    root        22     2  0 08:33 ?        00:00:00 [ksoftirqd/2]
    root        24     2  0 08:33 ?        00:00:00 [kworker/2:0H]
    root        25     2  0 08:33 ?        00:00:00 [rcuos/2]
    root        26     2  0 08:33 ?        00:00:00 [rcuob/2]
    root        27     2  0 08:33 ?        00:00:00 [watchdog/3]
    root        28     2  0 08:33 ?        00:00:00 [migration/3]
    root        29     2  0 08:33 ?        00:00:00 [ksoftirqd/3]
    root        31     2  0 08:33 ?        00:00:00 [kworker/3:0H]
    root        32     2  0 08:33 ?        00:00:00 [rcuos/3]
    root        33     2  0 08:33 ?        00:00:00 [rcuob/3]
    root        34     2  0 08:33 ?        00:00:00 [khelper]
    root        35     2  0 08:33 ?        00:00:00 [kdevtmpfs]

**example 3** 查看命令历史使用记录并通过less分页显示，

    zhb@zhb-H81-M1:~/Desktop/work/test$ history | less
        1  df -H
        2  ifconfig
        3  sudo gedit /etc/samba/smb.conf
        4  sudo vim /etc/samba/smb.conf
        5  sudo vi /etc/samba/smb.conf
        6  sudo apt-get install vim
        7  sudo vim /etc/samba/smb.conf
        8  sudo useradd zhb
        9  sudo smbpasswd -a zhb
       10  sudo service smbd restart
       11  sudo vim /etc/samba/smb.conf
       12  sudo service smbd restart
       13  cd /
       14  ll
       15  cd home/
       16  ll
       17  chown zhb:zhb share
       18  sudo chown zhb:zhb share
       19  ll
       20  ifconfig
       21  sudo vim /etc/samba/smb.conf
       22  sudo /etc/init.d/samba restart
       23  smbclient -L //localhost/myshare
       24  sudo vim /etc/samba/smb.conf
       25  sudo service smbd restart
       26  ping samba_ip
       27  ping 192.168.27.28
       28  telnet 192.168.27.28 445 telnet 192.168.27.28 139
       29  ll
       30  cd /home/
       31  ll
       32  sudo rm -rf share/
       33  cd zhb/

**example 4** 浏览多个文件，

    less 1.txt 2.txt

输入 ":n"后，切换到2.txt文件；

输入 ":p"后，切换到1.txt文件；

## 3.Reference

[Linux less命令](http://www.runoob.com/linux/linux-comm-less.html)

[Linux less命令](https://wizardforcel.gitbooks.io/w3school-linux/content/34.html)
