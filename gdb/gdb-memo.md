# gdb 笔记


### 非常基础的命令  
  掌握这些命令就可以进行基础的调试。P.S.编译的时候记得加调试"-g"


  - $gdb [file name]  
  运行gdb并打开文件  

  - $gdb -tui [file name]  
  运行带有terminal ui的gdb。注意：若程序有输出，会破坏tui的显示，可使用重定向将程序输出到其他pts  

  - focus/layout  
  同上  

  - tty [files]  
  将程序输出重定向，例如：tty /dev/pts/1，如果存在pts-1，程序输出将显示在pts-1，可使用 $ w 查看当前登录用户  

  - file  
  使用gdb打开文件  

  - l [identifier/line number]  
  显示某标识符或行号附近的代码  

  - l [file name]:[line number], [line number]  
  显示某文件某行到某行的代码  

  - r  
  运行程序  

  - b [line number]  
  打断点  

  - d [break number]  
  删除断点  

  - p [variable name] 或 p {[variable name], [variable name], ...}  
  显示当前一个或多个变量的值  

  - display [variable name] 或 display {[variable name], [variable name], ...}  
  显示当前一个或多个变量的值，会持续显示  

  - undisplay [variable number]  
  取消显示变量，参数为变量索引号  

  - watch [variable name] 或 watch {[variable name], [variable name], ...}  
  显示当前一个或多个变量的值，会在变量发生改变时显示  

  - ctrl + C  
  发送中断信号给程序，gdb会将程序暂停  

  - kill [filename]  
  终止当前程序  

  - c  
  继续执行程序  

  - n  
  执行下一行，步过  

  - s  
  执行下一条语句，步进  
  
  - f  
  查看当前堆栈  

  - set [variable name]  
  设置变量值  

  - rwatch [variable name]  
  如果变量被读取，则暂停程序  

  - awatch [variable name]  
  如果变量被写入，则暂停程序  

  - disable [break number]  
  禁用断点  

  - enable [break number]  
  启用断点  

  - return  
  强制从当前函数返回  

  - q  
  退出程序


### 稍微进阶一点的  
  可以使你的调试更加顺畅


  - stepi  
  执行下一句汇编，步进  

  - nexti  
  执行下一句汇编，步过  

  - ignore [break number] [times]  
  设置一个断点忽略册数  

  - xbreak  
  在当前函数退出点上设置一个断点  

  - txbreak  
  在当前函数退出点上设置一个一次性断点

  - backtrace/bt  
  查看堆栈，可在函数崩溃时调试使用  

  - whatis  
  显示当前变量的值和类型  

  - ptype  
  显示变量类型  

  - make  
  重新make  

  - shell  
  运行shell，执行exit可回到gdb  

  - finish  
  继续执行直到当前函数返回  


  如果你有兴趣或需求，可以修改gdb脚本，在~/.gdbinit，来定制你的gdb
