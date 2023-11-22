## 查询
[目录及概述 | 鸟哥的 Linux 私房菜：基础学习篇 第四版](https://wizardforcel.gitbooks.io/vbird-linux-basic-4e/content/1.html)
[超全整理！Linux shell及常用36类命令汇总 - 知乎](https://zhuanlan.zhihu.com/p/50448669)
[Linux 命令完全手册](https://www.freecodecamp.org/chinese/news/the-linux-commands-handbook/)

## 常见核心命令
### man
输入 `man <命令名>` 获取命令的说明

### ls
使用 `ls` 命令列出其中包含的全部文件
 `-al` 返回更多信息，包括- 文件权限（如果你的系统支持 ACL，这里也会有一个 ACL 标识）；链接到该文件的数量；该文件的所有者；该文件的用户组；文件大小（单位为字节）；文件最后的修改日期

### cd
用 `cd` 命令来打开文件夹。 `cd` 是 **c**hange **d**irectory（改变目录）的缩写。同样，你可以在后面加上文件夹的名字，或完整的路径，来访问某个特定的文件夹。
`cd ..` 代指上级目录。
`.`，指代的是**当前**所在的文件夹
根文件夹 `/`

### pwd
输入 `pwd` ，它会显示你现在的位置

### mkdir
使用 `mkdir` 命令创建新的文件夹或多个文件夹
添加 `-p` 参数，创建多个嵌套的文件夹

### rmdir
`rmdir` 命令用来删除文件夹
删除含有内容的文件夹，这里有一个更通用的命令：`rm` ，配合 `-rf` 参数即可同时删除文件夹和其中的文件

### mv
 `mv` 命令移动。只需要指定文件的当前路径和新路径

### cp
`cp` 命令可以用来复制文件，复制整个文件夹，可以添加 `-r` 参数来递归复制

### op
`open` 命令可以让你打开任意一个文件


## 文件管理
查看当前目录的大小 `du -sch . # `
查看某文件的大小 `du -sch file_name # `
查看该目录下所有文件/目录大小 `du -sch ./*
### find 命令[¶]( http://wiki.cheng-group.net/wiki/cluster_usage/pack_backup/#find "Permanent link")

对于大量具有相似命名的文件，可以利用 `find` 命令进行索引和删除。

例如对当前目录下（`./`），想要查找 `AuO` 任务产生的所有的 `cube` 文件（假设命名均为`AuO_*.cube`），可以采用如下命令进行展示：

`find ./ -name AuO_*.cube`

如果想要将这些文件直接删除，还可以加入 `-delete` 命令：
`find ./ -name AuO_*.cube -delete`

注意 `find` 命令后的选项为 `-` 而非 `--` 。