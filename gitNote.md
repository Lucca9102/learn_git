# 命令:
- <kbd>`mkdir dir`</kbd>: 创建空目录  
- <kbd>`cd dir`</kbd>: 转到目录  
- <kbd>`pwd`</kbd>: 显示当前目录(***<font color=red>P</font>rint <font color=red>W</font>orking <font color=red>D</font>irectory***)  
- <kbd>`cat filename`</kbd>: 查看文件*filename*的内容
- <kbd>`git init`</kbd>: 把这个目录编程Git可以管理的仓库
- <kbd>`git add`</kbd>: 把文件添加到仓库
- <kbd>`git commit`</kbd>
  - <kbd>`-m "xxx"`</kbd>: 把文件提交到仓库
- <kbd>`git status`</kbd>: 查看仓库的当前状态
- <kbd>`git diff`</kbd>: 查看修改前后的不同  
  - <kbd>`version -- filename`</kbd>: 查看<i>`version`</i>版本与当前状态的差别。(`version`可以是版本号也可以是`HEAD`表示的编号)
- <kbd>`git log`</kbd>: 查看历史提交记录
  - 例如：
    > ```
    > commit 478fe7926edef5a859684aef8cea42b9a62af2f7 (HEAD -> master)
    > Author: Lucca9102 <luccachina@163.com>
    > Date:   Fri Feb 5 21:46:31 2021 +0800
    > 
    >     The first checkpoint
    > 
    > commit 5585b10e28bcf75936ea56d235f7170dc43359fc
    > Author: Lucca9102 <luccachina@163.com>
    > Date:   Fri Feb 5 21:26:07 2021 +0800
    > ```
    其中<b><i>478fe7...</i></b>是<kbd>**`commit id`**</kbd>(版本号)
  - <kbd>`--pretty=oneline`</kbd>: 将简略信息在一行内显示出来
    - 例如：
        > 478fe7926edef5a859684aef8cea42b9a62af2f7 (HEAD -> master) The first checkpoint  
        > 5585b10e28bcf75936ea56d235f7170dc43359fc Start taking note.
- <kbd>`git reflog`</kbd>: 查看命令历史(包括`commit`、`reset`等等)  

## 撤销更改
- <kbd>`git checkout -- filename`</kbd>: 将*filename*恢复到最近一次`add`或`commit`的状态。
  - <font color=red>注意</font>: 恢复的部分只包括<u>已保存</u>，<u>未提交</u>，<u>未放入暂存区</u>的修改。另外，命令中的<b>`--`</b>是必要的，否则会变成另一个命令。
- <kbd>`git reset`</kbd>: 回退版本
  - <kbd>`--hard HEAD`</kbd>: 退回当前(最后一次提交的)版本并删除修改。
    - 这里的<kbd>`HEAD`</kbd>表示当前版本，类似的，<kbd>`HEAD^`</kbd>表示上一个版本，<kbd>`HEAD^^`</kbd>表示上上一个版本。上100个版本可以写成<kbd>`HEAD~100`</kbd>。
  - <kbd>`HEAD <file>`</kbd>: 将暂存区的修改撤销(unstage)掉，重新放回工作区。不会删除当前的修改。
  - <kbd>*`commit id`*</kbd>: 回退到该版本号对应的版本

---
---
# 概念：
- 工作区：在电脑中能够看到的目录，如当前的Git文件夹
- 版本库：工作区中有一个隐藏目录<kbd>`.git`</kbd>，这个文件夹就是Git的版本库。版本库中最重要的东西就是称为<i>**stage**</i>(或叫<i>**index**</i>)的暂存区，还有Git自动创建的第一个分支<kbd>`master`</kbd>，以及指向<kbd>`master`</kbd>的指针<kbd>`HEAD`</kbd>
使用`git add`时，会将文件修改添加到暂存区；
使用`git commit`时，则会把暂存区的内容提交到当前分支。
- Git管理的是修改，而不是文件。即使新增一行也算修改。提交文件前必须先添加到暂存区，再提交到版本库。如果没有`add`，则修改不会被提交
![stage](images\stage.png)