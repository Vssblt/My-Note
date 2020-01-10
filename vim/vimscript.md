# vim 脚本


这里有我的常用脚本设置

### /etc/vimrc  
  - 很多时候vim需要打开多个文件交叉编辑，尤其是编写代码，所以当我们打开多个文件时自动对屏幕进行分割然后加载不同的文件会更加方便，下面就是相关的代码，将代码加至vimrc结尾即可。

    这段脚本将实现自动垂直分割屏幕并加载第一个和第二个文件到buffer
    
    `if (buflisted(2))  
    `	let fname = "vs " . bufname(2)  
    `	exe fname  
    `endif  

