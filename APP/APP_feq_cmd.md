# 常用命令速记

## 打包及压缩
```
tar cvf tar_file files    #打包
tar xvf tar_file          #解包
tar xvf tar_file -C dir   #解包到指定目录
tar tvf tar_file          #显示被打包的文件

-p  保存文件的原有权限及属性，适用于备份重要文件
-P  保存文件的绝对路径

# gzip
tar cvfz tar_gz_file files
tar xvfz tar_gz_file
tar tvfz tar_gz_file

# bzip2
tar cvfj tar_bz2_file files
tar xvfj tar_bz2_file
tar tvfj tar_bz2_file
```

## 链接文件
```
ln -sf source target
s  符号链接
f  若目标文件存在，则先删除后创建
```

## 其它常用命令
```
# gerp
grep [option] pattern files
-v 反选
-c 统计条目
-i 忽略大小写
-r 递归目录

# find
find [pathname] [conditions]
find /etc -name "*mail*"      #文件名中包含mail的
find / -type f -size +100M    #文件大小超过100M的
find . -mtime +60             #文件修改时间距今超过60天的
find . -mtime -2              #在过去两天内修改过的
find / -type f -name *.tar.gz -size +100M -exec ls -l {} \;
#找到tar.gz包，且大小超过100M的，并显示它们的详细信息
find /home -type f -mtime +60 | xargs tar -cvfj /tmp/`date '+%d%m%Y'_archive.tar`
#使用xargs将找到的文件打包备份

-atime  文件的最近访问时间
-ctime  文件的最近更改时间-文件状态
-mtime  文件的最近更改时间-文件内容
-depth  目录深度
-exec   执行相应命令
-follow 跟随符号链接
-fstype 指定文件系统类型
-group  指定用户组
-gid    指定用户组号
-inum   inode号
-links  文件拥有的链接数量
-name   文件名模式
-newer  比指定文件更新
-nogroup 非系统用户组文件
-nouser 非系统用户文件
-perm   指定文件具有的权限
-size   文件大小
-type   文件类型 f d l b c p s
-user   指定用户
-uid    指定用户ID

# date
date +"%Y-%m-%d %H:%M:%S"
2009-01-01 08:21:41

# cron
crontab -e
* * * * * /path_to_command arg1 arg2 ...
1 Minute      0-59
2 Hours       0-23
3 Day         0-31
4 Month       0-12
5 Day of week 0-7

可以使用* , - /
* 任意时间，不做限制
, 并列时间
- 指定时间区间，如5-10号每月
/ 步长，如*/3每隔三天

预定义的宏时间
@reboot       启动时执行一次
@yearly       一年执行一次，0 0 1 1 *
@annually     与@yearly相同
@monthly      每月执行一次，0 0 1 * *
@weekly       每周执行一次，0 0 * * 0
@daily        每天执行一次，0 0 * * *
@midnight     与daily相同
@hourly       每小时执行一次，0 * * * *

定义位置
/etc/crontab
/etc/cron.d
/etc/cron.hourly
/etc/cron.daily
/etc/cron.weekly
/etc/cron.monthly
/var/spool/cron/crontabs

/etc/cron.allow
/etc/cron.deny



```
