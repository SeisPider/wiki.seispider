+++
date = "2017-08-05T16:24:01+08:00"
title = "适用于 Python 的 Vim 配置"
+++
首先，安装 [YouCompleteMe](https://github.com/Valloric/YouCompleteMe) 要求 Vim 
版本号在7.4.1578，然而 yum 源中的 Vim 版本为7.3.160。因此自行编译Vim。

# Vim8 的编译

- 克隆仓库获取最新 Vim 版本,本地版本在src中。
```
git clone https://github.com/vim/vim.git 
```

- [参考网页](http://maoxiaomeng.com/2016/10/12/vim%E7%BC%96%E8%AF%91%E6%96%B0%E7%89%88%E6%9C%AC/)编译更新 Vim 版本

# 配置 Vim 基本属性

```
"去掉vi的一致性"
set nocompatible
"显示行号"
set number
set relativenumber
" 隐藏滚动条"    
set guioptions-=r 
set guioptions-=L
set guioptions-=b
"隐藏顶部标签栏"
set showtabline=0
"设置字体"
set guifont=Monaco:h13         
syntax on    "开启语法高亮"
set nowrap    "设置不折行"
set fileformat=unix    "设置以unix的格式保存文件"
set cindent        "设置C样式的缩进格式"
set tabstop=4    "设置table长度"
set shiftwidth=4        "同上"
set showmatch    "显示匹配的括号"
set scrolloff=5        "距离顶部和底部5行"
set laststatus=2    "命令行为两行"
set fenc=utf-8      "文件编码"
set backspace=2
set mouse=a        "启用鼠标"
set selection=exclusive
set selectmode=mouse,key
set matchtime=5
set ignorecase        "忽略大小写"
set incsearch
set hlsearch        "高亮搜索项"
set noexpandtab        "不允许扩展table"
set whichwrap+=<,>,h,l
set autoread
set cursorline        "突出显示当前行"
set cursorcolumn        "突出显示当前列"
set colorcolumn=80   
```


# 配置 Vim 插件
- 在 .vimrc 文件中配置 Vundle 安装插件

```
filetype off
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
Plugin 'VundleVim/Vundle.vim'

"git interface
Plugin 'tpope/vim-fugitive'

"filesystem
Plugin 'scrooloose/nerdtree'
Plugin 'jistr/vim-nerdtree-tabs'
Plugin 'kien/ctrlp.vim' 
"html
"  isnowfy only compatible with python not python3
Plugin 'isnowfy/python-vim-instant-markdown'
Plugin 'jtratner/vim-flavored-markdown'
Plugin 'suan/vim-instant-markdown'
Plugin 'nelstrom/vim-markdown-preview'
"python sytax checker
Plugin 'nvie/vim-flake8'
Plugin 'vim-scripts/Pydiction'
Plugin 'vim-scripts/indentpython.vim'
Plugin 'scrooloose/syntastic'

"auto-completion stuff
"Plugin 'klen/python-mode'
Plugin 'Valloric/YouCompleteMe'
Plugin 'klen/rope-vim'
"Plugin 'davidhalter/jedi-vim'
Plugin 'ervandew/supertab'
""code folding
Plugin 'tmhedberg/SimpylFold'

"Colors!!!
Plugin 'altercation/vim-colors-solarized'
Plugin 'jnurmine/Zenburn'
Plugin 'Lokaltog/vim-powerline'
call vundle#end()
filetype plugin indent on
```

- 进入 Vim 中并执行命令 `:VundleInstall` 或直接在命令行键入`vim +PluginInstall +qall`
  以安装插件

# YouCompleteMe 配置
  仅利用 Vundle 安装 YCM 并不能生效，需要对 YCM 进行编译配置。
- 编译 [YCM](https://github.com/Valloric/YouCompleteMe)

```
cd ~/.vim/bundle/YouCompleteMe
./install.py
```

- 将模板配置文件中提取出来并进行设置，[参考](http://zuyunfei.com/2013/05/16/killer-plugin-of-vim-youcompleteme/)
```
cp ~/.vim/bundle/YouCompleteMe/cpp/ycm/.ycm_extra_conf.py ~/.vim/.ycm_extra_conf.py
```

并在 .vimrc 中添加语句
```	
let g:ycm_global_ycm_extra_conf = '~/.vim/.ycm_extra_conf.py'
```

# 设置颜色主题
- 从[Github](https://github.com/altercation/vim-colors-solarized)或`src/vim-colors-solarized` 中获取颜色配置文件
- 在 .vimrc 中添加配置
