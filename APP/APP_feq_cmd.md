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
-group  指定用户组号
-inum   inode号
-links  文件拥有的链接数量
-name   文件名模式
-newer  比指定文件更新
-nogroup 非系统用户组文件
-nouser 非系统用户文件
-perm   指定文件具有的权限
-size   文件大小
-type   文件类型
-user   指定用户

# date
date +"%Y-%m-%d %H:%M:%S"
2009-01-01 08:21:41
```
