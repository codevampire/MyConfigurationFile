SPF13-VIM快捷键列表

全新安装：
curl https://j.mp/spf13-vim3 -L -o - | sh

更新：
cd $HOME/to/spf13-vim/
git pull
vim +BundleInstall! +BundleClean +q

<Leader>:
,

Buffers and Tabs:
:badd <filename>
:b#   Switch to new tab
:bd   Buffer delete
:bn   Buffer next
:bp   Buffer prev

Highlight:
:nohl

Paste Toggle:
<F12>

Folding Options:
<Leader>F0-F9

UndoTree:
<Leader>u

NERDTree:
<Leader>e
<C-E> toogle

ctrlp:
<c-p>

Surround:
删除配对 ds + 配对 ds"
更改配对 cs + 旧配对 + 新配对 cs])
更改配对到标签 cs + 旧配对 + 新标签 cs"<p>

NERDCommenter:
<Leader>c<space>

neocomplete:
<C-k>

Tabularize:
<Leader>a=
<Leader>a:
<Leader>a::
<Leader>a,
<Leader>a<bar>

Tagbar:
<Leader>tt 开启面板
<C-]> 跳转

自动补全:
<Tab>


