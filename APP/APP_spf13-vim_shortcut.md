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

## 保存为UTF-8编码
```
set fenc=utf-8
```

## 正确的VIM编码设置方法
```
set encoding=utf-8
set fileencodings=ucs-bom,utf-8,cp936,gb18030,latin1
set fileencoding=utf-8
```

## 替换^M字符 \r
```
set ff=unix
%s#\r##g
```

## 替换^@字符 \0x00
```
%s#[\x00]##g
```

## 代码折叠级数:
```
<Leader>F0-F9
zo 打开折叠
zc 重新折叠
zr 全部展开
zm 全部折叠
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
:! cmd %
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
n@{a-z} 运行寄存器中的指令n次
@{a-z}  运行寄存器中的指令
@@        重复运行指令
```
## 合并行
```
J
```

## 命令计数
```
n+cmd
```

## 行间移动
```
^ 行首第一非空
0 行首
$ 行末
```

## 括号跳转
```
%
```

## 行移动
```
nG     移动到n行
gg     到首行
G      到末行
0-100% 内容的百分比处
```

## 搜索
```
.  *  [  ]  ^  % /  \  ?  ~  $ 要加转义，转义字符 \
/ 向后搜索
? 向前搜索
n 下一处
n 前一处
* 0-n次
\+ 1-n次
\= 0-1次
\{a,b} a-b次
\{a,}  a-n次
\{,b}  n-b次
\{a}   a次
\|     或

```

## 打印
```
:hardcopy
:source $VIMRUNTIME/syntax/2html.vim
```

## 可视块模式
```
<C+V> 进入可视块模式
I     竖向插入，ESC后显示全部
```

## 改变单词大小写
```
gU{w,b} 改大写，向前走一个单词
gu{w,b} 改小写，向后走一个单词
```

## 正则分组
```
\(\)
```

## 虚拟编辑模式
```
:set virtualedit=all
:set virtualedit=
```
