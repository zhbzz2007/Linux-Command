## 1.用法

1. Usage: locate [OPTION]... [PATTERN]...

使用者可以很快速的搜寻档案系统内是否有指定的档案。其方法是先建立一个包括系统内所有档案名称及路径的数据库，之后当寻找时，就只需查询这个数据块，而不必实际深入档案系统之中；

**Options:**

    -A, --all              只显示匹配所有模式的文件

    -b, --basename         只匹配路径中的基本名字

    -c, --count            只显示找到的文件的数目

    -d, --database DBPATH  指定数据库的路径

    -e, --existing         将排除在寻找的范围之外

    -L, --follow           检查文件存在时，对软链接进行操作

    -i, --ignore-case      匹配模式时，忽略目标的大小写

    -l, --limit, -n LIMIT  限制输出的数目

    -P, --nofollow, -H     检查文件存在时，不对软链接进行操作

    -0, --null             在输出中使用NUL分割文件

    -S, --statistics       不搜索，输出所有使用的数据库

    -q, --quiet            安静模式，不会显示任何错误讯息

    -r, --regexp REGEXP    使用基本的正则表达式作为寻找的条件
        --regex            扩展正则表达式的模式

    -w, --wholename        匹配整个路径名称

## 2.示例

**example 1** 查找和pwd相关的所有文件，

    zhb@zhb-VM:~/Desktop/work$ locate pwd
    /bin/pwd
    /etc/.pwd.lock
    /home/zhb/install/eclipse/plugins/org.python.pydev.jython_5.1.2.201606231256/Lib/pwd.py
    /home/zhb/torch/exe/luajit-rocks/luarocks/win32/tools/pwd.exe
    /lib/modules/4.2.0-27-generic/kernel/drivers/watchdog/hpwdt.ko
    /lib/modules/4.2.0-36-generic/kernel/drivers/watchdog/hpwdt.ko
    /lib/modules/4.2.0-38-generic/kernel/drivers/watchdog/hpwdt.ko
    /lib/modules/4.2.0-41-generic/kernel/drivers/watchdog/hpwdt.ko
    /lib/modules/4.2.0-42-generic/kernel/drivers/watchdog/hpwdt.ko
    /lib/modules/4.4.0-34-generic/kernel/drivers/watchdog/hpwdt.ko
    /lib/modules/4.4.0-36-generic/kernel/drivers/watchdog/hpwdt.ko
    /sbin/unix_chkpwd
    /usr/bin/pwdx
    /usr/include/pwd.h

**example 2** 搜索etc目录下所有以sh开头的文件，

    zhb@zhb-VM:~/Desktop/work$ locate /etc/sh
    /etc/shadow
    /etc/shadow-
    /etc/shells

**example 3** 搜索etc目录下，所有以m开头的文件，

    zhb@zhb-VM:~/Desktop/work$ locate /etc/m
    /etc/magic
    /etc/magic.mime
    /etc/mailcap
    /etc/mailcap.order
    /etc/manpath.config
    /etc/mime.types
    /etc/mke2fs.conf
    /etc/modprobe.d
    /etc/modules
    /etc/modules-load.d
    /etc/mpv
    /etc/mtab
    /etc/mtab.fuselock
    /etc/mtools.conf
    /etc/modprobe.d/alsa-base.conf
    /etc/modprobe.d/blacklist-ath_pci.conf
    /etc/modprobe.d/blacklist-firewire.conf
    /etc/modprobe.d/blacklist-framebuffer.conf
    /etc/modprobe.d/blacklist-modem.conf
    /etc/modprobe.d/blacklist-oss.conf
    /etc/modprobe.d/blacklist-rare-network.conf
    /etc/modprobe.d/blacklist-watchdog.conf
    /etc/modprobe.d/blacklist.conf
    /etc/modprobe.d/dkms.conf
    /etc/modprobe.d/fbdev-blacklist.conf
    /etc/modprobe.d/iwlwifi.conf
    /etc/modprobe.d/mlx4.conf
    /etc/modprobe.d/nvidia-352_hybrid.conf
    /etc/modprobe.d/nvidia-graphics-drivers.conf
    /etc/modprobe.d/vmwgfx-fbdev.conf
    /etc/modules-load.d/cups-filters.conf
    /etc/mpv/encoding-profiles.conf
    /home/zhb/install/eclipse/plugins/org.apache.ant_1.9.6.v201510161327/etc/maudit-frames.xsl
    /home/zhb/install/eclipse/plugins/org.apache.ant_1.9.6.v201510161327/etc/mmetrics-frames.xsl
    /home/zhb/torch/exe/luajit-rocks/lua-5.1/etc/min.c
    /home/zhb/torch/exe/luajit-rocks/lua-5.1-rc/etc/min.c
    /usr/local/cuda-7.5/libnsight/plugins/org.apache.ant_1.9.2.v201404171502/etc/maudit-frames.xsl
    /usr/local/cuda-7.5/libnsight/plugins/org.apache.ant_1.9.2.v201404171502/etc/mmetrics-frames.xsl
    /usr/local/cuda-7.5/libnvvp/plugins/org.apache.ant_1.9.2.v201404171502/etc/maudit-frames.xsl
    /usr/local/cuda-7.5/libnvvp/plugins/org.apache.ant_1.9.2.v201404171502/etc/mmetrics-frames.xsl
    /usr/src/linux-headers-4.4.0-34/zfs/etc/modules-load.d
    /usr/src/linux-headers-4.4.0-34/zfs/etc/modules-load.d/Makefile.in
    /usr/src/linux-headers-4.4.0-36/zfs/etc/modules-load.d
    /usr/src/linux-headers-4.4.0-36/zfs/etc/modules-load.d/Makefile.i

## 3.Reference

[每天一个linux命令（18）：locate 命令](http://www.cnblogs.com/peida/archive/2012/11/12/2765750.html)
