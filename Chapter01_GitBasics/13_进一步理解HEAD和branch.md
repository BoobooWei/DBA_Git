# 进一步理解HEAD和branch

* HEAD 最终一定是指向 `commit`;
* `git diff HEAD HEAD^1^1`将当前分支和爷爷对比。

## 练习题

创建两个不同的 Git 仓库，在⾥⾯添加相同内容的⽂件，然后把 它们都加⼊到暂存区中，再看看两个仓库中同内容的⽂件对应的 blob 的 hash 值是否相同？多试⼏次看看结论是否⼀样？

一样。

```shell
MacBook-Pro-4:booboo booboo$ cd test_git/
MacBook-Pro-4:test_git booboo$ git init 01
Initialized empty Git repository in /Users/booboo/Desktop/booboo/test_git/01/.git/
MacBook-Pro-4:test_git booboo$ git init 02
Initialized empty Git repository in /Users/booboo/Desktop/booboo/test_git/02/.git/
MacBook-Pro-4:test_git booboo$ cd 01
MacBook-Pro-4:01 booboo$ echo 01 > 01.md
MacBook-Pro-4:01 booboo$ git add -A
MacBook-Pro-4:01 booboo$ git commit -m '01'
[master (root-commit) 55ed5b6] 01
 1 file changed, 1 insertion(+)
 create mode 100644 01.md
MacBook-Pro-4:01 booboo$ cd ..
MacBook-Pro-4:test_git booboo$ cd 02
MacBook-Pro-4:02 booboo$ echo 02 > 02.md
MacBook-Pro-4:02 booboo$ rm -rf 02.md 
MacBook-Pro-4:02 booboo$ ls
MacBook-Pro-4:02 booboo$ echo 01 > 01.md
MacBook-Pro-4:02 booboo$ git add -A
MacBook-Pro-4:02 booboo$ git commit -m '01'
[master (root-commit) 822cf01] 01
 1 file changed, 1 insertion(+)
 create mode 100644 01.md
MacBook-Pro-4:02 booboo$ cd ..
MacBook-Pro-4:test_git booboo$ ls
01	02
MacBook-Pro-4:test_git booboo$ cd 01
MacBook-Pro-4:01 booboo$ git log --oneline -n2
55ed5b6 (HEAD -> master) 01
MacBook-Pro-4:01 booboo$ git cat-file -p 55ed5b6
tree e490984a8d69d6c74ac8749fbcfd9e0571fa3453
author weiyaping <weiyaping@jiagouyun.com> 1554990843 +0800
committer weiyaping <weiyaping@jiagouyun.com> 1554990843 +0800

01
MacBook-Pro-4:01 booboo$ git cat-file -p e4909
100644 blob 8a0f05e166aa61225bf6649cb345f87416b5f509	01.md
MacBook-Pro-4:01 booboo$ git cat-file -p 8a0f
01
MacBook-Pro-4:01 booboo$ cd ../02
MacBook-Pro-4:02 booboo$ git log --oneline -n2
822cf01 (HEAD -> master) 01
MacBook-Pro-4:02 booboo$ git cat-file -p 822cf01
tree e490984a8d69d6c74ac8749fbcfd9e0571fa3453
author weiyaping <weiyaping@jiagouyun.com> 1554990882 +0800
committer weiyaping <weiyaping@jiagouyun.com> 1554990882 +0800

01
MacBook-Pro-4:02 booboo$ git cat-file -p e4909
100644 blob 8a0f05e166aa61225bf6649cb345f87416b5f509	01.md
MacBook-Pro-4:02 booboo$ git cat-file -p 8a0f
01
```

