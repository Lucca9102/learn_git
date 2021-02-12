*为了方便回顾，有些指令在多个部分出现*

# 指令总结:
## 系统指令
`$` <kbd>`mkdir dir`</kbd>: 创建空目录  
`$` <kbd>`cd dir`</kbd>: 转到目录  
`$` <kbd>`pwd`</kbd>: 显示当前目录  
`$` <kbd>`ls`</kbd>: 查看当前目录下的文件和文件夹  
  - `-ah`: 查看包括隐藏文件在内的所有文件和文件夹  

`$` <kbd>`cat [file]`</kbd>: 查看文件内容  
`$` <kbd>`rm [file]`</kbd>: 删除文件

---
## 建立仓库和提交
`$` <kbd>`git init`</kbd>: 把这个目录编程Git可以管理的仓库  
`$` <kbd>`git add`</kbd>: 把文件添加到仓库  
`$` <kbd>`git commit`</kbd>：提交修改(创建文件快照)  
  - `-m  "[descriptive message]"`: 把文件提交到仓库
  - `-am "[descriptive message]"`: 把所有已修改的文件提交到仓库(不包括新添加的文件)
  - 连续两个包含`-m`选项的字符串，第一个会被作为提交的总结(summary)信息，第二个则被当作描述(description)。可以参考GitHub Desktop软件中的提交。

`$` <kbd>`git status`</kbd>: 查看仓库的当前状态  
`$` <kbd>`git diff`</kbd>: 查看所有文件修改前后的不同(默认是最近提交或暂存的版本)  
  - `version`</kbd>: 查看<i>`version`</i>版本与当前状态的差别(`version`可以是版本号也可以是`HEAD`表示的编号)  
  - `--staged`: 查看文件与暂存区的不同  
  - `-- [file]`: 查看对应文件与目标版本之间的区别(需要放在指令末尾)  

`$` <kbd>`git log`</kbd>: 查看提交记录  
  - `--pretty=oneline`: 将每次提交记录缩略到一行显示，包括版本号和提交信息
  - `--graph`: 查看分支的合并情况，会显示一个字符组成的简单图形  
  - `--abbrev-commit`: 缩写版本号，只显示前面几个字符

`$` <kbd>`git reflog`</kbd>: 查看指令历史(包括`commit`、`reset`等等)  

---
## 撤销更改
`$` <kbd>`git checkout`</kbd>: 检出
  - `-- [file]`: 将文件恢复到最近一次`add`或`commit`的状态
  - `[branch-name]`: 切换分支
    - `-b [branch-name]`: 创建并切换分支
  - `<tagname>`: 检出分支，即查看某个标签所指的文件版本  
`$` <kbd>`git reset`</kbd>: 回退版本(默认将暂存区的文件unstage)  
  - `--soft`: 只移动`HEAD`指针，不改变暂存区和工作区
  - `--mixed`: 默认值，移动`HEAD`指针，unstage暂存区文件，不改变工作区
  - `--hard`: 移动`HEAD`指针，退回暂存区文件，将工作区恢复到选定版本（完全回滚）  
  - `version`: 版本，默认为`HEAD`
  - `[file]`: 文件，默认为工作区所有文件

---
## 删除文件
`$` <kbd>`git rm [file]`</kbd>: 在版本库和文件资源管理器中同时删除文件(在Win10系统下文件不会进入回收站)  

---
## 远程仓库
`$` <kbd>`ssh-keygen`</kbd>: 设置SSH Key  
  - `-t [type]`: 要生成密钥的类型(学习时使用了rsa)
  - `-C "content"`: 用来识别密钥的注释  

`$` <kbd>`git remote`</kbd>: 查看远程仓库信息  
  - `-v`: 查看详细信息  
`$` <kbd>`git remote add <shortname> <url>`</kbd>: 添加名为`<shortname>`，地址为`<url`>的远程仓库(因为笔记来源不同，所以表述可能有所不同，如上面的`<shortname>`和下面的`[alias]`其实是同样的)
  - eg: `$ git remote add origin git@github.com:lucca9102/Learning-Git` 
 
`$` <kbd>`git push <remote>`</kbd>: 把本地的推送到远程仓库  
  - `-u`: (首次推送时，放在push后)把本地分支与远程分支关联起来，并推送本地分支到远程仓库(有这个作用，知道这个就够用了，但是具体作用建议查表)  
  - `<branch>`: 推送分支
  - `--tags`: 推送本地所有标签
  - `:refs/tags/<tagname>`: 删除远程标签  
  - `--delete`: 删除远程的什么东西
    - `<branch>`: 删除分支  
    - `<tagname>`: 删除标签

`$` <kbd>`git clone`</kbd>: 克隆远程仓库  
  - `$` <kbd>`git clone git@github.com:yourname/yourrepo.git`</kbd>: 使用SSH协议传输，默认，更快  
  - `$` <kbd>`git clone https://github.com/yourname/yourrepo.git`</kbd>: 使用HTTPS协议传输，慢，且每次都要口令  

---
## 分支管理
`$` <kbd>`git checkout`</kbd>: 检出
  - `-- [file]`: 将文件恢复到最近一次`add`或`commit`的状态
  - `[branch-name]`: 切换分支
    - `-b [branch-name]`: 创建并切换分支
  - `<tagname>`: 检出分支，即查看某个标签所指的文件版本
`$` <kbd>`git switch [branch-name]`</kbd>: 切换分支  
  - `-c`: 创建并切换到新的分支  
`$` <kbd>`git branch`</kbd>: 查看所有分支  
  - `[branch-name]`: 建立分支
  - `-d [branch-name]`: 删除分支
  - `-D [branch-name]`: 强行删除分支  
  - `-vv`: 查看详细分支信息，包括和远程分支的领先、落后情况等（这个命令并不会联网，只是使用最后一次抓取时的状态）
  - `-r`: 查看远程分支
  - `--merged [branch-name]`: 查看 不包含 **没有**合并到选中分支（默认为当前分支）的内容 的分支  
  - 和`--no-merged [branch-name]`: 查看 包含 **没有**合并到选中分支（默认为当前分支）的内容 的分支  
`$` <kbd>`git merge [branch]`</kbd>: 合并分支  
`$` <kbd>`git log`</kbd>: 查看提交记录  
  - `--pretty=oneline`: 将每次提交记录缩略到一行显示，包括版本号和提交信息
  - `--graph`: 查看分支的合并情况，会显示一个字符组成的简单图形  
  - `--abbrev-commit`: 缩写版本号，只显示前面几个字符
  - `--oneline`: `--pretty=oneline`和`--abbrev-commit`合用的简写
  - `-(num)`: 显示`num`条记录，例如`$ git log -3`

`$` <kbd>`git merge`</kbd>: 合并分支  
  - `--no-ff`: 合并时不要使用`Fast-Forward`模式   
  - `-m [msg]`: 如果建立了新的提交，则使用后面的字符串做提交信息

`$` <kbd>`git stash`</kbd>: 暂存已修改的内容  
  - `apply`: 取出暂存的内容  
    - `stash{$num}`: 取出特定编号的stash  
  - `drop`: 删除暂存的内容  
    - `stash{$num}`  
  - `pop`: 取出暂存内容并删除stash  
    - `stash{$num}`  
  - `clear`: 清除所有stash

`$` <kbd>`git cherry-pick [commit]`</kbd>: 复制某次提交到当前分支  

`$` <kbd>`git push <remote>`</kbd>: 把本地的推送到远程仓库  
  - `-u`: (首次推送时，放在push后)把本地分支与远程分支关联起来，并推送本地分支到远程仓库(有这个作用，知道这个就够用了，但是具体作用建议查表)  
  - `<branch>`: 推送分支
  - `--tags`: 推送本地所有标签
  - `:refs/tags/<tagname>`: 删除远程标签  
  - `--delete`: 删除远程的什么东西
    - `<branch>`: 删除分支  
    - `<tagname>`: 删除标签

`$` <kbd>`git fetch <remote>`</kbd>: 抓取远程库的数据并下载到本地  
  - `--all`: 抓取所有远程仓库
`$` <kbd>`git pull`</kbd>: 抓取数据到本地并合并，相当于`fetch`+`merge`  

---
## 打标签
`$` <kbd>`git tag`</kbd>: 查看所有标签
  - `-l`或`--list`: 查找符合条件的标签
    如果后面不接东西，则可以省略，返回所有标签；  
    如果提供了一个匹配标签名的通配模式，那么`-l`或`--list`就是强制使用的

  - `-a <tagname>`: 提供标签名，使用即创建附注标签
  - `-m <description>`: 添加标签的描述信息，附注标签必需
  - `-d <tagname>`: 删除标签

`$` <kbd>`git show <tagname>`</kbd>: 查看tag信息