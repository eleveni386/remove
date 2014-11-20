remove
======

安全的linux rm 命令

众所周知 linux 下 大杀器之一 rm 是多么恐怖的东西存在

众多系统管理员 对此命令是又爱 又恨,  基于本人也是一枚系统管理员, 写下这个小 工具
方便自己 随心所欲的使用大杀器

麻麻再也不用担心 我使用rm了

##特性

    1.  删除日志记录
    2. 安全目录
    3. 垃圾箱机制
    
 
##参数

    usage: rm [-h] [-r] [-f] [--log] [-a SAFE_DIR] [file [file ...]]

    用于替换系统的rm命令
    自带回收站
    exp:
        -a '^/$' -a '^/home/?$' # 增加/ 和 /home 目录不可删除
        --log # 显示删除日志
    

    positional arguments:
        file                  file...

    optional arguments:
         -h, --help            show this help message and exit
        r, --recursive       remove directories and their contents recursively
        -f, --force           ignore nonexistent files and arguments, never prompt
         --log                 show delete log
        -a SAFE_DIR, --add_safe_dirs SAFE_DIR
                             add safe dirs regex
                             
##默认安全目录

[Safe_dirs]

safe_dirs = ['^/$', '^/home/?$', '^/usr/?$', '^/var/?$']

可通过 `-a `参数 添加 新的 安全目录 (**每次添加一个目录**)

或 直接 在 `~/.Recycle/.Recycle.conf `中添加

##垃圾箱位置

`~/.Recycle/`

该目录下 存在两个隐藏文件

`.delete`, `.Recycle.conf`

delete 是删除日志
Recycle.conf 是安全目录配置文件

