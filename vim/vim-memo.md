# vim 笔记


因为有些命令总是忘，所以写个笔记记录下常用的命令，很多基础的命令比如:wq就不再记录了，笔记开源供大家学习。


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

  - :vsp/ctrl-w\_v  
  垂直分割  

  - :sp/ctrl-w\_n  
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

  - [num]gt/gt  
   跳转到某一个tab/下一个tab  

  - :tabo/tabonly  
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

  - :b[file index/file name]  
  切换到某个文件  

  - :bn  
  切换到下个文件  

  - :bp  
  切换到上个文件  


### vim定位相关命令  
  一般来讲键盘的屏幕定位能力相比鼠标来说要差一些，但多文件间定位要比鼠标强一些，这也就意味着你对vim定位指令的熟悉程度将直接影响你使用vim时的体验  
  - [[  
  跳到代码段开头，如果已在头部则向上跳转到上一个代码段头部，编程的时候用来跳转到函数头有奇效。  

  - ]]  
  跳转到下一个代码段的开头  

  - *  
  搜索光标所在的字符串  

  - ''  
  跳转到光标上次所在位置，注意是两个'，不是一个"  

  - w  
  跳到下一个单词  

  - h/j/k/l  
  分别相当于方向键left、down、up、right  

  - :[num]  
  跳转到[num]行号  

  vim提供了书签功能，这个功能可以极大的简化屏幕定位操作  

  - marks/marks [a-zA-Z]  
  查看所有书签/查看某一具体书签的详细信息，如果书签为大写则为全局书签。注意，显示的书签包含vim自行创建的书签其中包括："]"、"["、"""、"."等，你不需要对这些书签进行管理，但可以使用这些书签  

  - m[a-zA-Z]  
  设置书签，如果书签为大写则为全局书签  

  - `[a-zA-Z]  
  跳转到书签所在行，如果书签为大写则为全局书签  


### 编程相关  
  - :make  
  相当于直接执行了shell命令make  

  - :cw  
  vim非常强大的quickfix功能，显示make结果，用于调错  

  - :cn  
  quickfix窗口下，显示下一个错误  

  - :cp  
  quickfix窗口下，显示上一个错误  


### 代码补全
  （尚未完成，以后再加）  


### CSCOPE


### 


### 其他
  - :set mouse=a  
  激活鼠标操作（激活后就失去灵魂了，请谨慎操作）  

  - :h [vim command]  
  vim help  

  - :set viminfo='20,\"4096  
  vim read write buffer
