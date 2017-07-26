# 帐号管理

## useradd
```
[root@www ~]# useradd [-u UID] [-g 初始群组] [-G 次要群组] [-mM] [-c 说明栏] [-d 家目录绝对路径] [-s shell] 使用者账号名
选项与参数：
-u  ：后面接的是 UID ，是一组数字。直接指定一个特定的 UID 给这个账号；
-g  ：后面接的那个组名就是我们上面提到的 initial group 啦～该群组的 GID 会被放置到 /etc/passwd 的第四个字段内。
-G  ：后面接的组名则是这个账号还可以加入的群组。这个选项与参数会修改 /etc/group 内的相关数据喔！
-M  ：强制！不要创建用户家目录！(系统账号默认值)
-m  ：强制！要创建用户家目录！(一般账号默认值)
-c  ：这个就是 /etc/passwd 的第五栏的说明内容啦～可以随便我们配置的啦～
-d  ：指定某个目录成为家目录，而不要使用默认值。务必使用绝对路径！
-r  ：创建一个系统的账号，这个账号的 UID 会有限制 (参考 /etc/login.defs)
-s  ：后面接一个 shell ，若没有指定则默认是 /bin/bash 的啦～
-e  ：后面接一个日期，格式为 YYYY-MM-DD 此项目可写入 shadow 第八字段，亦即账号失效日的配置项目啰；
-f  ：后面接 shadow 的第七字段项目，指定口令是否会失效。0为立刻失效，-1 为永远不失效(口令只会过期而强制于登陆时重新配置而已。)

范例一：完全参考默认值创建一个用户，名称为 vbird1
[root@www ~]# useradd vbird1
[root@www ~]# ll -d /home/vbird1
drwx------ 4 vbird1 vbird1 4096 Feb 25 09:38 /home/vbird1
# 默认会创建用户家目录，且权限为 700 ！这是重点！

[root@www ~]# grep vbird1 /etc/passwd /etc/shadow /etc/group
/etc/passwd:vbird1:x:504:505::/home/vbird1:/bin/bash
/etc/shadow:vbird1:!!:14300:0:99999:7:::
/etc/group:vbird1:x:505:    <==默认会创建一个与账号一模一样的群组名
```