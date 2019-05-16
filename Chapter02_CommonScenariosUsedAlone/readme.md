|No.|常用场景|命令|
|:--|:--|:--|
|1|怎么删除不需要的分支|`git brach -d branch_name`|
|2|怎么修改最新commit和message|`git commit --amend`|
|3|怎么修改老旧commit和message|`git rebase -i commit_father_id`|
|4|怎么把连续的多个commit整理成1个|`git rebase -i commit_father_id`|
|5|怎么把间隔的几个commit整理成1个|`git rebase -i commit_father_id`|
|6|怎么比较暂存区和HEAD所含文件的差异|`git diff --cached`|
|7|怎么比较工作区和暂存区所含文件的差异|`git diff`|
|8|如何让暂存区恢复和HEAD的一样|`git reset HEAD`|
|9|如何让工作区的文件恢复为和暂存区一样|`git checkout`|
|10|怎么消除暂存区部分文件的修改|`git reset HEAD -- file1 file2`|
|11|消除最近的几次提交|`git reset --hard commit_id`|
|12|看看不同提交的指定文件的差异|`git diff commit-id1 commit-id2 path-to-filename`|
|13|正确删除文件的方法|`git rm file`|
|14|开发中临时加塞了紧急任务怎么处理|`git stash`|
|15|如何指定不需要Git管理的文件|`touch .gitignore`|
|16|如何将Git仓库备份到本地|`git clone --bare file://[local_path] [backup_name]`|
