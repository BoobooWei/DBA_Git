[toc]

# 如何让暂存区恢复和HEAD的一样

放弃已经add的内容

```shell
git reset HEAD
```

git reset 有三个参数
* --soft 这个只是把 HEAD 指向的 commit 恢复到你指定的 commit，暂存区 工作区不变
* --hard 这个是 把 HEAD， 暂存区， 工作区 都修改为 你指定的 commit 的时候的文件状态
* --mixed 这个是不加时候的默认参数，把 HEAD，暂存区 修改为 你指定的 commit 的时候的文件状态，工作区保持不变
