# git笔记


### 非常基础的常用命令  
这些命令都是非常基础的，掌握这些命令即可完成大部分工作。

  - git clone [url]  
  从服务器克隆文件  

  - git pull  
  从服务器拉取文件，更新到本地库  

  - git add [file name]  
  添加文件，加“-A”参数可自动添加所有修改过的文件  

  - git rm [file name]  
  删除文件，但是一定要注意这会同时删除本地文件，如果想要保留本地文件，需要加"--cached"  

  - git commit  
  提交，加“-m”参数可在后面直接跟一行修改信息  

  - git push  
  将文件推到远端服务器  

  - git checkout [file name] [branch hash]  
  还原文件，不加分支hash会还原到当前分支，hash可通过git log查看，谨慎操作，搞不好的话，已经修改的文件就会被你搞没了  

  - git checkout [branch name]  
  检出，切换到某一分支  

  - git checkout -b [new branch name]  
  创建新的分支并切换到该分支  

  - git checkout -b [new branch name] [branch name]  
  创建新分支并切换到目标分支，例如 git checkout -b newlocalbranch origin/remoteBranch  

  - git branch [new branch name]  
  创建新分支  

  - git branch  
  查看本地分支，加参数“-r”可查看远程分支，加参数“-a”查看所有

  - git log  
  查看历史版本  

  - git log [file name]  
  查看某一文件的历史版本  

  - git log -[num]  
  查看[num]个历史版本  

  - git diff [file name]  
  查看当前文件和当前分支下的该文件的区别，就是看你修改了什么  

  - git diff [file name] [branch name]  
  查看当前文件和目标分支下该文件的区别  

  - git merge [branch name]  
  合并目标分支到当前分支  
