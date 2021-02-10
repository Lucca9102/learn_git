# 指令总结:
## 系统指令
`$` <kbd>`mkdir dir`</kbd>: 创建空目录  
`$` <kbd>`cd dir`</kbd>: 转到目录  
`$` <kbd>`pwd`</kbd>: 显示当前目录  
`$` <kbd>`ls`</kbd>: 查看当前目录下的文件和文件夹  
  - `$` <kbd>`ls -ah`</kbd>: 查看包括隐藏文件在内的所有文件和文件夹  

`$` <kbd>`cat [file]`</kbd>: 查看文件内容  
`$` <kbd>`rm [file]`</kbd>: 删除文件

---
## 建立仓库和提交
`$` <kbd>`git init`</kbd>: 把这个目录编程Git可以管理的仓库  
`$` <kbd>`git add`</kbd>: 把文件添加到仓库  
`$` <kbd>`git commit`</kbd>：提交修改
  - `$` <kbd>`git commit -m "xxx"`</kbd>: 把文件提交到仓库
  - `$` <kbd>`git commit -am "xxx"`</kbd>: 把所有已修改的文件提交到仓库

`$` <kbd>`git status`</kbd>: 查看仓库的当前状态  
`$` <kbd>`git diff`</kbd>: 查看修改前后的不同  
  - `$` <kbd>`git diff version -- [file]`</kbd>: 查看<i>`version`</i>版本与当前状态的差别(`version`可以是版本号也可以是`HEAD`表示的编号)  

`$` <kbd>`git log`</kbd>: 查看历史提交记录
  - `$` <kbd>`git log --pretty=oneline`</kbd>: 将简略信息在一行内显示出来

`$` <kbd>`git reflog`</kbd>: 查看指令历史(包括`commit`、`reset`等等)  

---
## 撤销更改
`$` <kbd>`git checkout -- [file]`</kbd>: 将文件恢复到最近一次`add`或`commit`的状态  
`$` <kbd>`git reset`</kbd>: 回退版本
  - `$` <kbd>`git reset --hard version`</kbd>: 退回<i>`version`</i>版本并删除修改
  - `$` <kbd>`git reset HEAD [file]`</kbd>: 将暂存区的修改撤销(unstage)掉，重新放回工作区(不会删除当前的修改)

---
## 删除文件
| 指令 | 作用 |
| :- | :- |
| `$` <kbd>`git rm [file]`</kbd> | 在版本库和文件资源管理器中同时删除文件 |
---
## 远程仓库
| 指令 | 作用 |
| :- | :- |
| `$` <kbd>`ssh-keygen -t rsa -C "content"`</kbd> | 设置SSH Key |
| `$` <kbd>`git remote add origin git@github.com:yourname/yourrepo`</kbd> | 将仓库关联到远程仓库(以GitHub为例) |
| `$` <kbd>`git push [alias] [branch]`</kbd><br>例：`$` <kbd>`git push origin master` | 把`[branch]`分支上的提交推送到远程仓库`[alias]`<br>例：把`master`分支的提交推送到远程仓库`origin` |
| `$` <kbd>`git push -u [alias] [branch]`</kbd> | (首次推送时)把本地分支与远程分支关联起来，并推送本地分支到远程仓库 |
| `$` <kbd>`git clone git@github.com:yourname/yourrepo.git`</kbd> | 使用SSH协议传输的克隆远程仓库 |
| `$` <kbd>`git push https://github.com/yourname/yourrepo.git` | 使用HTTPS协议传输的克隆远程仓库 |

---
## 分支管理
| 指令 | 作用 |
| :- | :- |
| `$` <kbd>`git checkout -b [branch-name]`</kbd> | 创建并切换到新的分支 |
| `$` <kbd>`git checkout [branch-name]`</kbd> | 切换到分支 |
| `$` <kbd>`git switch -c [branch-name]`</kbd> | 创建并切换到新的分支 |
| `$` <kbd>`git switch [branch-name]`</kbd> | 切换到分支 |
| `$` <kbd>`git branch`</kbd> | 查看当前仓库中所有分支 |
| `$` <kbd>`git branch [branch-name]`</kbd> | 创建新的分支 |
| `$` <kbd>`git merge [branch]`</kbd> | 把选定的分支的提交合并到当前分支 |
| `$` <kbd>`git branch -d [branch-name]`</kbd> | 删除分支 |