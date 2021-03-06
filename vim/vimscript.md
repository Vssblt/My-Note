# vim 脚本


这里有我的常用脚本设置  

这是我现在正在使用的轻量级vim脚本：[http://49.235.80.28/vim-script/](http://49.235.80.28/vim-script/)  
安装方法：只需下载[auto-download.sh](http://49.235.80.28/vim-script/auto-download.sh), 赋予执行权限之后运行脚本即可。  
注意：脚本主要针对一些vim配置、C/C++高亮、代码补全、自动加载tag和键盘映射进行优化，同时还附有一套主题风格，但是键盘映射是针对dvorak键盘布局进行设计的，因此并不适合qwerty键盘布局使用，可进行适当修改或直接删除此功能。后续我会持续更新和完善此脚本。  

### /etc/vimrc ~/.vimrc  
  - 很多时候vim需要打开多个文件交叉编辑，尤其是编写代码，所以当我们打开多个文件时自动对屏幕进行分割然后加载不同的文件会更加方便，下面就是相关的代码，将代码加至vimrc结尾即可。

    这段脚本将实现自动垂直分割屏幕并加载第一个和第二个文件到buffer
    
    >if (buflisted(2))  
    >	let fname = "vs " . bufname(2)  
    >	exe fname  
    > endif  


  - 以下选项将打开一些功能

    >set listchars=eol:$,tab:>-,trail:~,extends:>,precedes:<,nbsp:_  
    >set invlist  
    >set laststatus=2  
    >set showtabline=2
    >"set nowrap  
    >set cursorline  
    >set cursorcolumn  
    >set fileencodings=ucs-bom,utf-8,cp936,gb18030,big5,euc-jp,euc-kr,latin1  
    >set showtabline=2  
    >set hlsearch  
    >set incsearch  
    >set showmatch  
    >set ignorecase  
    >hi CursorLine gui=NONE cterm=bold ctermbg=238 "8 = dark gray, 15 = white, 235 = dark dark gray. ctermfg: front ground  
    >hi CursorColumn gui=NONE cterm=bold ctermbg=240  
    
    listchars选项可设置不可显示字符的显示规则  
    invlist选项可设置显示不可显字符，nolist可关闭  
    laststatus选项可设置为3种显示模式的其中之一，这里选择了状态2，即一直显示文件状态，选项打开后将持续显示当前文件的文件名和编辑行与列  
    showtabline选项为2时，vim将时刻显示当前的tab信息  
    nowrap选项可用于设置禁止强制换行，wrap可设置为强制换行  
    cursorline选项将打开光标所在行显示，该选项打开后可能会覆盖下划线的屏幕显示，但好处是，在你进行多个窗口切换时依旧可以看到此窗口的当前编辑行，帮助快速定位  
    cursorcolumn选项将打开光标所在列的显示。  
    fileencodings选项用于检测文件编码格式，vim会依次尝试使用下列文件编码格式解码文件，若成功解码则判断为该文件为此格式。所以应该将编码格式较为严格的放在前面，相对宽松的放在后面，用于防止误判。  
    showtabline选项值为2时常亮显示tab状态栏  
    hlsearch选项开启搜索高亮  
    incsearch选项开启搜索全文高亮  
    showmatch选项开启搜索实时匹配  
    ignorecase选项关闭搜索大小写敏感  

    以上选项均可使用:h listchars类似的方式查询帮助文档


  - 以下选项将打开代码补全

    >filetype plugin indent on  
    >set completeopt=longest,menu  
    >set tags=[当前tags文件]  

    打开后可在vim insert 模式下使用Ctrl+x使用补全选项，相关帮助文档可使用:h help new-omni-completion进行查询~~
    注意：代码补全需要ctags支持，使用时请先安装ctags并生成ctags文件


### ~/.vim/synatx/c.vim
  - 这个文件默认是不存在的，需要从“/usr/share/vim/vim81/syntax”目录下复制，复制后可将C/C++代码进行高亮显示，但原版脚本高亮显示不尽人意，所以我给脚本增加了更多的高亮规则，将此段代码加至该文件末尾即可生效。

    > " Highlight Class and Function names  
    > syn match    cCustomParen    "(" contains=cParen,cCppParen  
    > syn match    cCustomScope    "::"  
    > syn match    cCustomClass    "\w\\+\s*::" contains=cCustomScope  
    > syn match    cCustomFunc     "\w\\+\s*(" contains=cCustomParen  
    > syn match    cCustomSymbol   "[\\{\\}\\(\\)\\[\\]]"  
    > syn match    cCustomCalcu    "[&\+\\-\*\/\=\<\>]"  
    > syn match    cCustomComment  "\/\/[[:print:][:tab:]]*$" "contains=ctesttest  
    > syn match    cCustomComment2  "\/\*[[:print:][:tab:]]\{-}\*\/" "contains=ctesttest  
    > syn match    cCustomComment3  "\/\*\_[[:print:][:tab:]]\{-}\*\/" "contains=ctesttest  
    >  
    > hi cCustomSymbol gui=NONE cterm=bold ctermfg=yellow  
    > hi cCustomCalcu gui=NONE cterm=bold ctermfg=yellow  
    > hi cCustomClass gui=NONE cterm=bold  ctermfg=78  
    > hi cCustomFunc  gui=NONE cterm=bold  ctermfg=196     "9  
    > hi cCustomComment gui=NONE cterm=bold  ctermfg=73    "154  
    > hi cCustomComment2 gui=NONE cterm=bold  ctermfg=73     "154  
    > hi cCustomComment3 gui=NONE cterm=bold  ctermfg=73     "154  

    需要确保你的terminal支持256位色彩，否则高亮将不会生效，这在大多数linux gui下是被支持的，cygwin下需要额外的设置，如果你的terminal不支持，可以更改代码中的数字为其他颜色。
