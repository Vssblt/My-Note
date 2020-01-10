# vim 脚本


这里有我的常用脚本设置

### /etc/vimrc  
  - 很多时候vim需要打开多个文件交叉编辑，尤其是编写代码，所以当我们打开多个文件时自动对屏幕进行分割然后加载不同的文件会更加方便，下面就是相关的代码，将代码加至vimrc结尾即可。

    这段脚本将实现自动垂直分割屏幕并加载第一个和第二个文件到buffer
    
    >if (buflisted(2))
    >	let fname = "vs " . bufname(2)  
    >	exe fname  
    > endif  

### ~/.vim/synatx/c.vim
  - 这个文件默认是不存在的，需要从“/usr/share/vim/vim81/syntax”目录下复制，复制后可将C/C++代码进行高亮显示，但原版脚本高亮显示不尽人意，所以我给脚本增加了更多的高亮规则，将此段代码加至该文件末尾即可生效。

    > hi cCustomSymbol gui=NONE cterm=bold ctermfg=yellow 
    > hi cCustomCalcu gui=NONE cterm=bold ctermfg=yellow  
    > hi cCustomClass gui=NONE cterm=bold  ctermfg=78  
    > hi cCustomFunc  gui=NONE cterm=bold  ctermfg=9  
    > hi cCustomComment gui=NONE cterm=bold  ctermfg=154  
    > hi cCustomComment2 gui=NONE cterm=bold  ctermfg=154  
    > hi cCustomComment3 gui=NONE cterm=bold  ctermfg=154  

    需要确保你的terminal支持256位色彩，否则高亮将不会生效，这在大多数linux gui下是被支持的，cygwin下需要额外的设置，如果你的terminal不支持，可以更改代码中的数字为其他颜色。
