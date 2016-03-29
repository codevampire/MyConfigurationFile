# SPF13-VIM快捷键

## 全新安装:
```
curl https://j.mp/spf13-vim3 -L -o - | sh
```

## 更新:
```
cd $HOME/to/spf13-vim/
git pull
vim +BundleInstall! +BundleClean +q
```

## Leader键绑定:
```
,
```

## 缓冲区与标签页管理:
```
:badd <filename>
:b#   Switch to new tab
:bd   Buffer delete
:bn   Buffer next
:bp   Buffer prev
```

## 关闭高亮:
```
:nohl
```

## 粘贴模式开关:
```
<F12>
```

## 代码折叠级数:
```
<Leader>F0-F9
```

## UndoTree 查看Unod与Redo历史:
```
:UndotreeToggle
<Leader>u
```

## NERDTree 文件浏览器:
```
<Leader>e
<C-E> NERDTree Toggle
```

## CtrlP 文件打开:
```
<C-p> CtrlP Toggle
```

## Surround:
```
删除配对 ds + 配对 ds"
更改配对 cs + 旧配对 + 新配对 cs])
更改配对到标签 cs + 旧配对 + 新标签 cs"<p>
```

### NERDCommenter 代码注释:
```
<Leader>c<space> Comment Toggle
```

## Neocomplete 自动补全:
```
<C-k> Complete Toggle
```

## Tabularize 代码对齐:
```
<Leader>a=
<Leader>a:
<Leader>a::
<Leader>a,
<Leader>a<bar>
```

## Tagbar 代码标签:
```
<Leader>tt 开启面板
<C-]> 跳转
<C-o> 回到上次
```

## 文件格式:
```
:set ff=unix/dos/?
```

## 语法高亮:
```
:syntax enable/clear/off
```

## 特殊字符:
```
<C-v> code
```

## 外部命令:
```
:! cmd
:r !cmd 读取运行结果
:w !cmd 将内容写入命令输入
```

## 屏幕切换:
```
<C-w> h/j/k/l
:close
:only
:qall
:wall
:wqall
```

## 大小写:
```
:set ic
:set noic
```

## 寄存器:
```
q{a-z}  在寄存器中记录指令
q{A-Z}  在寄存器中追加指令
q       结束
@{a-z}  运行寄存器中的指令
@@        重复运行指令
```

