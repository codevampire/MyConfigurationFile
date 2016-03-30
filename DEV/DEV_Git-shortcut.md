# Git常用命令

## Git的状态
工作目录 暂存区 仓库
从仓库到工作目录通过检出，从工作目录到暂存区通过暂存，从暂存区到仓库通过检入。

## 设定用户名、邮箱地址以及默认编辑器
```
$ git config --global user.name "Your Name"
$ git config --global user.email youemail@xxx.com
$ git config --global core.editor vim 
```

## 查看当前配置情况
```
$ git config --list
```

## 创建一个仓库
```
$ git init
```

## 克隆一个仓库
```
$ git clone https://github.com/codevampire/xxx.git
$ git clone https://github.com/codevampire/xxx.git myxxx
$ git clone -b branch_name https://github.com/codevampire/xxx.git
$ git clone git://github.com/codevampire/xxx.git
$ git clone user@server:path/to/repo.git
```

## 记录到仓库的数据变更
数据存在未跟踪状态、未修改状态、修改状态与暂存状态。
未跟踪的文件通过add命令进行暂存，已修改的文件通过暂存到暂存状态，暂存状态的文件通过commit提交到未修改状态，未修改状态的文件通过remove到未跟踪状态。
```
$ git status
```

## 忽略文件
```
*.a              非.a文件
!lib.a           但lib.a例外
/TODO            只忽略顶层根目录下的TODO目录
build/           忽略build目录下的文件
doc/*.txt        只忽略doc这层目录下的.txt文件
doc/**/*.txt     递归忽略doc目录下的.txt文件
*                任意多次
?                一个字符
[0-9]            数字组
```

## 提交更改
```
$ git commit -m 'comment'
```

## add、rm、mv
```
$ git add file
$ git rm  file
$ git mv  old_file new_file
```

## 查看历史
```
$ git log
```

## 追加提交
```
$ git commit --amend    提交后发现还有东西需要提交或加注释，则改完后再执行该语句，会追加到之前的提交上。
```

## 移出暂存区
```
$ git reset HEAD file
```

## 取消修改
```
$ git checkout -- file
```

## 查看远程仓库
```
$ git remote -v
```

## pull与push
```
$ git pull origin master
$ git push origin master
```

## 创建分支
```
$ git branch branch_name
$ git branch new_branch from_branch
$ git checkout -b branch_name          创建分支并切换分支
```
创建分支命令并不负责切换分支，Git内部维护一个HEAD指针，需要手工挪动HEAD指针到需要的分支上。

## 查看现有分支
```
$ git branch
$ git branch -v
$ git branch -a
$ git branch --merged
$ git branch --no-merged
$ git log --decorate --graph --all
```

## 检出分支
```
$ git checkout branch_name
$ git checkout master            切换回主分支
```

## 合并分支
```
$ git merge branch_name          一个分支合并另一个名为branch_name的分支
```
前向合并，最简单的合并，在一条线的前方分支合并这条线的后方分支。
基本合并，非同路线上的分支进行合并，采用三方合并，合并时会报冲突，必须解决冲突，之后才能继续。

## 删除分支
```
$ git branch -d branch_anem      删除分支
```
