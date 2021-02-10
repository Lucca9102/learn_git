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
`$` <kbd>`git checkout -- [file]`</kbd>: 将文件恢复到最近一次`add`或`commit`的状态  
`$` <kbd>`git reset`</kbd>: 回退版本(默认将暂存区的文件unstage)  
  - `--soft`: 只移动`HEAD`指针，不改变暂存区和工作区
  - `--mixed`: 默认值，移动`HEAD`指针，unstage暂存区文件，不改变工作区
  - `--hard`: 移动`HEAD`指针，退回暂存区文件，将工作区恢复到选定版本（完全回滚）  
  - `version`: 版本，默认为`HEAD`
  - `[file]`: 文件，默认为工作区所有文件

---
## 删除文件
`$` <kbd>`git rm [file]`</kbd>: 在版本库和文件资源管理器中同时删除文件(不会进入回收站)  

---
## 远程仓库
`$` <kbd>`ssh-keygen`</kbd>: 设置SSH Key  
  - `-t [type]`: 要生成密钥的类型
  - `-C "content"`: 用来识别密钥的注释
`$` <kbd>`git remote add origin git@github.com:yourname/yourrepo`</kbd>: 将仓库关联到远程仓库(以GitHub为例)  
`$` <kbd>`git push [alias] [branch]`</kbd>: 把`[branch]`分支上的提交推送到远程仓库`[alias]`  
  - `-u`: (首次推送时)把本地分支与远程分支关联起来，并推送本地分支到远程仓库(有这个作用，知道这个就够用了，但是具体作用建议查表)  

`$` <kbd>`git clone`</kbd>: 克隆远程仓库  
  - `$` <kbd>`git clone git@github.com:yourname/yourrepo.git`</kbd>: 使用SSH协议传输，默认，更快  
  - `$` <kbd>`git push https://github.com/yourname/yourrepo.git`</kbd>: 使用HTTPS协议传输  

---
## 分支管理
`$` <kbd>`git checkout [branch-name]`</kbd>: 切换分支  
`$` <kbd>`git checkout -b [branch-name]`</kbd>: 创建并切换到新的分支  
`$` <kbd>`git switch [branch-name]`</kbd>: 切换分支  
`$` <kbd>`git switch -c [branch-name]`</kbd>: 创建并切换到新的分支  
`$` <kbd>`git branch`</kbd>: 查看所有分支  
`$` <kbd>`git branch -d [branch-name]`</kbd>: 删除分支  
`$` <kbd>`git merge [branch]`</kbd>: 合并分支  
`$` <kbd>`git log`</kbd>: 查看提交记录  
  - `--pretty=oneline`: 将每次提交记录缩略到一行显示，包括版本号和提交信息
  - `--graph`: 查看分支的合并情况，会显示一个字符组成的简单图形  
  - `--abbrev-commit`: 缩写版本号，只显示前面几个字符

`$` <kbd>`git merge`</kbd>: 合并分支  
  - `--no-ff`: 合并时不要使用`Fast-Forward`模式   
  - `-m [msg]`: 如果建立了新的提交，则使用后面的字符串做提交信息