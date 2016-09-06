## 1.用法

1. usage: git [--version] [--help] [-C <path>] [-c name=value]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p|--paginate|--no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]

文字模式下的文件管理员，git是用于管理文件的程序；

**Options：**

    add        添加文件或者目录到Git索引中

    bisect     二分查找介绍bug的修改

    branch     列出，创建或者删除分支

    checkout   切换分支或者路径到工作目录，还原代码

    clone      克隆一个代码仓库到新的目录中

    commit     提交工作区中的的修改

    diff       显示修改间的差异或者修改与工作目录之间的差异等等

    fetch      从其他代码仓库中下载文件和引用

    grep       显示匹配指定模式的行

    init       创建一个空的代码库或者对已经存在的代码库重新初始化

    log        查看历史日志

    merge      合并分支

    mv         删除或者重命名文件，目录或者符号连接

    pull       从其他的版本库（远程或者本地）将代码更新到本地

    push       将本地commit的代码更新到远程版本库中

    rebase     切换分支点

    reset      将当前的工作目录完全回滚到指定的版本号

    rm         从工作区和索引中删除文件

    show       查看修改文件变更情况

    status     显示工作区状态

    tag        创建、显示、删除或者验证一个tag

## 2.示例

**example 1：** 克隆远程代码库，

    zhb@zhb-H81-M1:~/Desktop/work$ git clone https://git.coding.net/zhbzz2007/TestForGit.git
    Cloning into 'TestForGit'...
    remote: Counting objects: 9, done.
    remote: Compressing objects: 100% (4/4), done.
    remote: Total 9 (delta 1), reused 9 (delta 1)
    Unpacking objects: 100% (9/9), done.
    Checking connectivity... done.

**example 2：** 查看当前工作区的状态，

    zhb@zhb-H81-M1:~/Desktop/work/TestForGit$ git status
    On branch master
    Your branch is up-to-date with 'origin/master'.

    Untracked files:
      (use "git add <file>..." to include in what will be committed)

            test.txt

    nothing added to commit but untracked files present (use "git add" to track)

**example 3：** 将当前工作区的修改添加至Git索引，并提交工作区的修改，

    zhb@zhb-H81-M1:~/Desktop/work/TestForGit$ git add test.txt
    zhb@zhb-H81-M1:~/Desktop/work/TestForGit$ git commit -m"add test.txt"           [master 21559e3] add test.txt
     1 file changed, 1 insertion(+)
     create mode 100644 test.txt

**example 4：** 将本地commit的代码更新到远程版本库中，

    zhb@zhb-H81-M1:~/Desktop/work/TestForGit$ git push origin  master
    Counting objects: 4, done.
    Delta compression using up to 4 threads.
    Compressing objects: 100% (2/2), done.
    Writing objects: 100% (3/3), 277 bytes | 0 bytes/s, done.
    Total 3 (delta 0), reused 0 (delta 0)
    To https://git.coding.net/zhbzz2007/TestForGit.git
       9c16f7e..21559e3  master -> master

**example 5：** 从其他的版本库（远程或者本地）将代码更新到本地，

    zhb@zhb-H81-M1:~/Desktop/work/TestForGit$ git pull
    Already up-to-date.

**example 6：** 查看提交历史日志，

    zhb@zhb-H81-M1:~/Desktop/work/TestForGit$ git log
    commit 21559e366ece352f9aef4b7bd7e9031502f4b0d7
    Author: zhbzz2007 <zhb.zz.2007@163.com>
    Date:   Mon Sep 5 19:24:14 2016 +0800

        add test.txt

    commit 9c16f7eb761d5681b6f430c172c3487a67add767
    Author: Haibo Zhou <zhb.zz.2007@163.com>
    Date:   Fri May 27 09:35:11 2016 +0800

        提交git安装及操作截图

    commit d9d10572b0a066771d7a154481946c4cab6b9a58
    Author: Haibo Zhou <zhb.zz.2007@163.com>
    Date:   Fri May 27 09:25:14 2016 +0800

        提交git使用步骤

    commit 3a2239beb59c5bc5e3dc7ec652b5a3d911a034da
    Author: zhbzz2007 <zhb.zz.2007@163.com>
    Date:   Fri May 27 09:07:34 2016 +0800

        Initial commit

**example 7：** 查看提交内容，

    zhb@zhb-H81-M1:~/Desktop/work/TestForGit$ git show
    commit 21559e366ece352f9aef4b7bd7e9031502f4b0d7
    Author: zhbzz2007 <zhb.zz.2007@163.com>
    Date:   Mon Sep 5 19:24:14 2016 +0800

        add test.txt

    diff --git a/test.txt b/test.txt
    new file mode 100644
    index 0000000..190a180
    --- /dev/null
    +++ b/test.txt
    @@ -0,0 +1 @@
    +123

**example 8：** 查看当前分支，

    zhb@zhb-H81-M1:~/Desktop/work/TestForGit$ git branch
    * master

**example 9：** 查看匹配某一模式的行，

    zhb@zhb-H81-M1:~/Desktop/work/TestForGit$ git grep "123"
    test.txt:123

## 3.Reference

[廖雪峰Git教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
