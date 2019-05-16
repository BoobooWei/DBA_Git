[toc]

# 怎么比较暂存区和HEAD所含文件的差异

```shell
MacBook-Pro-4:DBA_Git booboo$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
MacBook-Pro-4:DBA_Git booboo$ git diff --cached
MacBook-Pro-4:DBA_Git booboo$ git add *
MacBook-Pro-4:DBA_Git booboo$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   Chapter02_CommonScenariosUsedAlone/17_怎么把连续的多个commit整理成1个.md
	modified:   Chapter02_CommonScenariosUsedAlone/18_怎么把间隔的几个commit整理成1个.md
	modified:   Chapter02_CommonScenariosUsedAlone/readme.md

MacBook-Pro-4:DBA_Git booboo$ git diff --cached
diff --git a/Chapter02_CommonScenariosUsedAlone/17_怎么把连续的多个commit整理成1个.md b/Chapter02_CommonScenariosUsedAlone/17_怎么把连续的多个commit整理成1个.md
index e69de29..98e36eb 100644
--- a/Chapter02_CommonScenariosUsedAlone/17_怎么把连续的多个commit整理成1个.md
+++ b/Chapter02_CommonScenariosUsedAlone/17_怎么把连续的多个commit整理成1个.md
@@ -0,0 +1,7 @@
+[toc]
+
+# 怎么把连续的多个commit整理成1个
+
+```shell
+`git rebase -i commit_father_id`
+```
diff --git a/Chapter02_CommonScenariosUsedAlone/18_怎么把间隔的几个commit整理成1个.md b/Chapter02_CommonScenariosUsedAlone/18_怎么把间隔的几个commit整理成1个.md
index e69de29..56854c1 100644
--- a/Chapter02_CommonScenariosUsedAlone/18_怎么把间隔的几个commit整理成1个.md
+++ b/Chapter02_CommonScenariosUsedAlone/18_怎么把间隔的几个commit整理成1个.md
@@ -0,0 +1,7 @@
+[toc]
+
+# 怎么把间隔的几个commit整理成1个
+
+```shell
+git rebase -i commit_father_id
+```
diff --git a/Chapter02_CommonScenariosUsedAlone/readme.md b/Chapter02_CommonScenariosUsedAlone/readme.md
index e2d0f86..c907b2d 100644
--- a/Chapter02_CommonScenariosUsedAlone/readme.md
+++ b/Chapter02_CommonScenariosUsedAlone/readme.md
@@ -2,7 +2,7 @@
 |:--|:--|:--|
 |1|怎么删除不需要的分支|`git brach -d branch_name`|
 |2|怎么修改最新commit和message|`git commit --amend`|
-|3|怎么修改老旧commit和message|`git rebase -i commit_id  `|
+|3|怎么修改老旧commit和message|`git rebase -i commit_father_id`|
 |4|怎么把连续的多个commit整理成1个||
 |5|怎么把间隔的几个commit整理成1个||
 |6|怎么比较暂存区和HEAD所含文件的差异||
```
