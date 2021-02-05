# 命令：  
- <kbd>`mkdir <i>dir</i>`</kbd>: 创建空目录  
- <kbd>`cd <i>dir</i>`</kbd>: 转到目录  
- <kbd>`pwd`</kbd>: 显示当前目录(***<font color=red>P</font>rint <font color=red>W</font>orking <font color=red>D</font>irectory***)  
- <kbd>`git init`</kbd>: 把这个目录编程Git可以管理的仓库
- <kbd>`git add`</kbd>: 把文件添加到仓库
- <kbd>`git commit`</kbd>
  - <kbd>`-m "xxx"`</kbd>: 把文件提交到仓库
- <kbd>`git status`</kbd>: 查看仓库的当前状态
- <kbd>`git diff`</kbd>: 查看修改前后的不同
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
- <kbd>`git reset --hard`</kbd>: 回退版本
  - <kbd>`HEAD`</kbd>: 表示当前版本，类似的，<kbd>`HEAD^`</kbd>表示上一个版本，<kbd>`HEAD^^`</kbd>表示上上一个版本。上100个版本可以写成<kbd>`HEAD~100`</kbd>。
  - <kbd>*`commit id`*</kbd>: 回退到该版本号对应的版本
- <kbd>`git reflog`</kbd>: 查看命令历史