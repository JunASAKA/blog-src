---
linktitle: "个人用Vim设定"
title: ""
date: 2022-08-23T20:55:43+08:00
categories:
- 纪要
- 配置文件
- 工具类
tags:
- vim
- 配置文件
- 纪要
keywords:
- vim
- 配置文件
thumbnailImage: thumbnail/vim_config.png
thumbnailImagePosition: left
summary: "[Abstract] 个人用Vim设定，配C/C++、Verilog HDL语言。随时更新。"
comments: false
---

<!--more-->

![pic](pic.png)

<h3>安装Vim-plug</h3>

`$ curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim`

<h3>YouCompleteMe之C++相关</h3>

`./install.py --clang-completer`


<h3>.vimrc如下</h3>

----
<p>call plug#begin('~/.vim/plugged')
<br />
<br />Plug 'tomasr/molokai'	"monokai配色方案
<br />
<br />Plug 'preservim/nerdtree'	"文件树
<br />Plug 'mbbill/undotree'		"TO/DO List
<br />Plug 'vim-airline/vim-airline'		"Airline
<br />Plug 'vim-airline/vim-airline-themes'
<br />Plug 'luochen1990/rainbow'	"彩虹括号
<br />Plug 'Raimondi/delimitMate'	"符号配对
<br />Plug 'vim-scripts/taglist.vim'
<br />Plug 'Chiel92/vim-autoformat'
<br />Plug 'octol/vim-cpp-enhanced-highlight'	"CPP高亮
<br />
<br />Plug 'ycm-core/YouCompleteMe'
<br />
<br />call plug#end()
<br />
<br />colorscheme molokai
<br />
<br />map <C-n> :NERDTreeToggle<CR>
<br />map <F5> :UndotreeToggle<CR>
<br />noremap <F3> :Autoformat<CR>
<br />map <F4> :TlistToggle<cr>
<br />
<br />
<br />" For CPP Highlight
<br />let g:cpp_class_scope_highlight = 1
<br />let g:cpp_member_variable_highlight = 1
<br />let g:cpp_class_decl_highlight = 1
<br />let g:cpp_experimental_simple_template_highlight = 1
<br />let g:cpp_experimental_template_highlight = 1
<br />let g:cpp_concepts_highlight = 1
<br />
<br />" For Autoformat
<br />let g:autoformat_autoindent = 0
<br />let g:autoformat_retab = 0
<br />let g:autoformat_remove_trailing_spaces = 0
<br />let g:autoformat_verbosemode=1
<br />
<br />" For Taglist
<br />let Tlist_Use_Right_Window=1
<br />let Tlist_Inc_Winwidth=0
<br />let Tlist_File_Fold_Auto_Close=1
<br />let Tlist_Exit_Onluwindow=1
<br />
<br />" For Airlan
<br />set ambiwidth=double                    " 设置为双字宽显示，否则无法完整显示如:☆
<br />let g:airline_theme='bubblegum'		"Airline主题
<br />let g:airline_powerline_fonts = 1
<br />" 开启tabline
<br />let g:airline#extensions#tabline#enabled = 1      "tabline中当前buffer两端的分隔字符
<br />let g:airline#extensions#tabline#left_sep = ' '   "tabline中未激活buffer两端的分隔字符
<br />let g:airline#extensions#tabline#left_alt_sep = '|'      "tabline中buffer显示编号
<br />let g:airline#extensions#tabline#buffer_nr_show = 1
<br />" 映射切换buffer的键位
<br />nnoremap [b :bp<CR>
<br />nnoremap ]b :bn<CR>
<br />
<br />
<br />" For Ranbow
<br />
<br />let g:rainbow_conf = {
<br />\	'guifgs': ['#C186BF', '#268EDB','#F79318'],
<br />\	'ctermfgs': ['lightblue', 'lightyellow', 'lightcyan', 'lightmagenta'],
<br />\	'operators': '_,_',
<br />\	'parentheses': ['start=/(/ end=/)/ fold', 'start=/\[/ end=/\]/ fold', 'start=/{/ end=/}/ fold'],
<br />\	'separately': {
<br />\		'*': {},
<br />\		'tex': {
<br />\			'parentheses': ['start=/(/ end=/)/', 'start=/\[/ end=/\]/'],
<br />\		},
<br />\		'lisp': {
<br />\			'guifgs': ['royalblue3', 'darkorange3', 'seagreen3', 'firebrick', 'darkorchid3'],
<br />\		},
<br />\		'vim': {
<br />\			'parentheses': ['start=/(/ end=/)/', 'start=/\[/ end=/\]/', 'start=/{/ end=/}/ fold', 'start=/(/ end=/)/ containedin=vimFuncBody', 'start=/\[/ end=/\]/ <br />containedin=vimFuncBody', 'start=/{/ end=/}/ fold containedin=vimFuncBody'],
<br />\		},
<br />\		'html': {
<br />\			'parentheses': ['start=/\v\<((area|base|br|col|embed|hr|img|input|keygen|link|menuitem|meta|param|source|track|wbr)[ >])@!\z([-_:a-zA-Z0-9]+)(\s<br />+[-_:a-zA-Z0-9]+(\=("[^"]*"|'."'".'[^'."'".']*'."'".'|[^ '."'".'"><=`]*))?)*\>/ end=#</\z1># fold'],
<br />\		},
<br />\		'css': 0,
<br />\	}
<br />\}
<br />let g:rainbow_active = 1
<br />
<br />"YouCompleteMe相关
<br />set runtimepath+=~/.vim/bundle/YouCompleteMe
<br />let g:ycm_collect_identifiers_from_tags_files = 1           " 开启 YCM 基于标签引擎
<br />let g:ycm_collect_identifiers_from_comments_and_strings = 1 " 注释与字符串中的内容也用于补全
<br />let g:syntastic_ignore_files=[".*\.py$"]
<br />let g:ycm_seed_identifiers_with_syntax = 1                  " 语法关键字补全
<br />let g:ycm_complete_in_comments = 1
<br />let g:ycm_confirm_extra_conf = 0
<br />let g:ycm_key_list_previous_completion = ['<c-p>', '<Up>']
<br />let g:ycm_complete_in_comments = 1                          " 在注释输入中也能补全
<br />let g:ycm_complete_in_strings = 1                           " 在字符串输入中也能补全
<br />let g:ycm_collect_identifiers_from_comments_and_strings = 1 " 注释和字符串中的文字也会被收入补全
<br />let g:ycm_global_ycm_extra_conf='~/.vim/bundle/YouCompleteMe/third_party/ycmd/cpp/ycm/.ycm_extra_conf.py'
<br />let g:ycm_show_diagnostics_ui = 0                           " 禁用语法检查
<br />inoremap <expr> <CR> pumvisible() ? "\<C-y>" : "\<CR>" |            " 回车即选中当前项
<br />nnoremap <c-j> :YcmCompleter GoToDefinitionElseDeclaration<CR>|     " 跳转到定义处
<br />"let g:ycm_min_num_of_chars_for_completion=2                 " 从第2个键入字符就开始罗列匹配项
<br />
<br />
<br />
<br />"基本配置
<br />"
<br />set termguicolors
<br />set encoding=utf-8
<br />syntax on
<br />language en_GB.UTF-8
<br />set nocompatible	"关闭vi兼容模式
<br />filetype on
<br />filetype indent on
<br />filetype plugin on
<br />set mouse=a	"v模式下鼠标
<br />set listchars=tab:▸\ ,trail:▫	"标记Tab与空格
<br />set scrolloff=5		"留五行
<br />set backspace=indent,eol,start
<br />
<br />set foldmethod=indent	"代码折叠
<br />set foldlevel=99
<br />set laststatus=2	"留命令行
<br />set autoindent		"自动缩进
<br />set number		"行号
<br />set relativenumber	"相对行号
<br />set cursorline		"光标线
<br />set cursorcolumn
<br />set wrap		"自动换行
<br />set showcmd		"显示命令
<br />set wildmenu		"Tab补全命
<br />set hlsearch		"搜索相关
<br />exec "nohlsearch"
<br />set incsearch
<br />set ignorecase
<br />set smartcase
<br />
<br />autocmd BufNewFile *.cpp,*.c,*.h,*.hpp,*.sh,*.bash,*.zsh,*.md,*.tex,*.m exec ":call Setfilehead()"
<br />func Setfilehead()
<br />	call append(0,'/***************************************')
<br />	call append(1,'#')
<br />	call append(2,'#	Filename: '.expand("%"))
<br />	call append(3,'#')
<br />	call append(4,'#	Developer: _Herrscher_of_the_Muaku')
<br />	call append(5,'#	Description: ---')
<br />	call append(6,'#	CreatTime: '.strftime("%Y-%m-%d %H:%M:%S"))
<br />	call append(7,'#')
<br />	call append(8,'***************************************/')
<br />endfunc
<br />map <F10> :call Setfilehead()<CR>:10<CR>o
<br />
<br />autocmd BufNewFile *.v,*.vh exec ":call SetfileheadHDL()"
<br />func SetfileheadHDL()
<br />	call append(0,'/***************************************')
<br />	call append(1,'#')
<br />	call append(2,'#	Filename: '.expand("%"))
<br />	call append(3,'#')
<br />	call append(4,'#	Developer: _Herrscher_of_the_Mukau_')
<br />	call append(5,'#	Description: ---')
<br />	call append(6,'#	CreatTime: '.strftime("%Y-%m-%d %H:%M:%S"))
<br />	call append(7,'#')
<br />	call append(8,'***************************************/')
<br />	call append(9,'module '.expand("%:r")."(")
<br />	call append(10,'')
<br />	call append(11,');')
<br />	call append(12,'')
<br />	call append(13,'')
<br />	call append(14,'endmodule')
<br />endfunc
<br /></p>