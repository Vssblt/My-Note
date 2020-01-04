# vim 笔记


### ctags常用命令  
  - ctags [options] [files]  
  用于生成tags文件，可以使用-R选项递归文件夹，也可以使用find加管道来限制文件。  
  
  - ctrl + ]  
  定位当前光标所在标识符的声明与定义，可在不同文件间切换。  
  
  - ctrl + w + ]  
  同上，但会新建窗口显示  
  
  - ctrl + o  
  回退  

  - ctrl + t  
  回退  

  - $ vim -t [tag name]  
  查找tag并打开该文件。注意：vim需要加载tags才行，可以在vimrc里设置set tags  

  - :tag [tag name]  
  查找tag  

  - :ts  
  tags list，显示当前查找tag的所有列表  

  - :tn  
  tags next，查找下一个tag  

  - :tp  
  tags preview，查找上一个tag  


### vim分屏  
  vim有buffer，window，tab的概念，可使用window和tab对屏幕进行分割和切换。  
  常用命令：  
  - vim -O[num] 或 vim -o[num]  
  -O为垂直分割，-o为水平分割  

  - :new [file name]  
  打开文件，不填file name则为空文件  

  - :vsp  
  垂直分割  

  - :sp  
  水平分割  

  - ctrl + w + [up/down/left/right/h/j/k/l]  
  编辑焦点移动  

  - :only  
  仅保留当前窗口  

  - :res[\+\-][num]  
  调节窗口大小  


### vim tab  
  - :tabe [file name]  
  新建tab并加载文件，不加文件名默认创建空文件  

  - :tabnew [file name]  
  同上  

  - :tab sp  
  打开当前缓冲区文件  

  - :tabf [file name]  
  搜索文件并在新tab打开，可打开多个文件，最多10个  

  - :tabs  
  列出所有tab  

  - :tabc  
  关闭当前tab  

  - :tabo  
  关闭所有tab  

  - :tabn  
  下一个tab  

  - :tabp  
  上一个tab  

  - gT  
  上一个tab  

  - gt  
  下一个tab  
  
  - :tabonly  
  只保留当前tab  

  - :tabr/tabfirst  
  切换到第一个tab  

  - :tabl/tablast  
  切换到最后一个tab  

  - :tabm [num]  
  调整tab次序  

  - :set showtabline=[0/1/2]  
  标签栏显示模式  

  - :tabdo  
  同时在多个tab里进行操作  


### vim多文件切换  
  - :ls  
  显示当前已加载的文件，显示“%”为当前文件，“#”为上个文件  

  - :b[num]  
  切换到某个文件  

  - :bn  
  切换到下个文件  

  - :bp  
  切换到上个文件  
