# linux 笔记


**我为什么喜欢linux？**


因为linux的易用性取决于一个人的水平，而不是系统本身。


## 关于目录切换
**cd命令真的好用吗？**


  我个人持否定态度，`cd`只是提供了基础的切换目录的功能，`cd`命令在用户多目录切换的情况下并不友好。尽管如此，多年来cd还是我切换目录最常用的工具。如果你想有更高效和易用的切换体验，则更应该尝试使用`pushd`、`popd`和`dirs`命令，这组命令可以以栈的形式管理你的目录，这使得目录切换更加方便。


  **1. `dirs pushd popd`**

  这组命令将目录存储堆栈化，`dirs`显示堆栈内容，`pushd`和`popd`分别用于将目录压入和弹出堆栈。整个目录栈存储了用户需要存储的目录内容，栈顶永远为当前目录，因此向栈顶压栈一定会改变当前的所在目录。


  **2. dirs**

  dirs命令用于显示堆栈内容，[-v] 参数可将堆栈按行排列并显示行号。[+n] 显示当前第n层目录。[-c] 清空当前堆栈。
  例：
```shell
[root@centos bin]# dirs -v
 0  /bin
 1  /var/www/html
 2  /var/www/html
 3  ~
```


  **3. pushd**

  不加参数时，pushd将置换栈内最顶层的两个目录，由于栈顶目录永远为当前目录，因此执行后将切换目录至置换后的目录，其结果类似于`# cd -`。
  `pushd [dir]`传入目录时，该目录将会从栈顶压入，并改变当前目录。
  `pushd [+n]`传入标号将会使堆栈以栈循环的方式将目标目录循环至栈顶，此操作同样会改变当前目录。
  `push [-n]`此参数将目录压入栈顶元素下面的位置，此操作不会改变当前目录。

  例：
```shell
[root@centos bin]# dirs -v
 0  /bin
 1  /var/www/html
 2  /var/www/html
 3  ~
[root@centos bin]# pushd +2
/var/www/html ~ /bin /var/www/html
[root@centos html]# dirs -v
 0  /var/www/html
 1  ~
 2  /bin
 3  /var/www/html
[root@centos html]# pushd +3
/var/www/html /var/www/html ~ /bin
[root@centos html]# dirs -v
 0  /var/www/html
 1  /var/www/html
 2  ~
 3  /bin
 ```


  4. popd
  
  `popd`不加参数时默认弹出栈顶元素。
  `popd [+n]`将编号n的元素删除。
  `popd [-n]`将栈顶元素下面的元素删除。

例：
```shell
[root@centos html]# dirs -v
 0  /var/www/html
 1  /var/www/html
 2  ~
 3  /bin
[root@centos html]# popd
/var/www/html ~ /bin
[root@centos html]# dirs -v
 0  /var/www/html
 1  ~
 2  /bin
[root@centos html]# popd -n
/var/www/html /bin
[root@centos html]# dirs -v
 0  /var/www/html
 1  /bin
[root@centos html]# popd +1
/var/www/html
[root@centos html]# dirs -v
 0  /var/www/html
```
