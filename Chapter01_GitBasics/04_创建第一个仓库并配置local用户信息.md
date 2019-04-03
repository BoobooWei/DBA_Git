[TOC]

# 建 Git 仓库

## 场景1： 将已有的项目代码纳入 Git 管理

### Git 基本命令

```shell
$ cd dir
$ git init
```

### 练习

```shell
# 创建目录
$ mkdir git_learn_1

# 进入目录
$ cd git_learn_1/

# 查看目录下的所有文件
$ ls -al
total 40
drwxr-xr-x 1 rgwei 197121 0 3月  10 12:17 ./
drwxr-xr-x 1 rgwei 197121 0 3月  10 12:17 ../

# 初始化仓库
$ git init
Initialized empty Git repository in C:/Users/rgwei/AppData/Local/Temp/git_learn_1/.git/

# 看到初始化后的目录中多了一个隐藏目录.git
$ ls -al
total 44
drwxr-xr-x 1 rgwei 197121 0 3月  10 12:18 ./
drwxr-xr-x 1 rgwei 197121 0 3月  10 12:17 ../
drwxr-xr-x 1 rgwei 197121 0 3月  10 12:18 .git/

# 查看.git目录下的具体文件
$ ls -la .git
total 11
drwxr-xr-x 1 rgwei 197121   0 3月  10 12:18 ./
drwxr-xr-x 1 rgwei 197121   0 3月  10 12:18 ../
-rw-r--r-- 1 rgwei 197121 130 3月  10 12:18 config
-rw-r--r-- 1 rgwei 197121  73 3月  10 12:18 description
-rw-r--r-- 1 rgwei 197121  23 3月  10 12:18 HEAD
drwxr-xr-x 1 rgwei 197121   0 3月  10 12:18 hooks/
drwxr-xr-x 1 rgwei 197121   0 3月  10 12:18 info/
drwxr-xr-x 1 rgwei 197121   0 3月  10 12:18 objects/
drwxr-xr-x 1 rgwei 197121   0 3月  10 12:18 refs/

# 创建一个文件readme
$ touch readme

# 将reamde添加到git跟踪
$ git add readme

# 查看git跟踪的明细
$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   readme


# 提交变更明细到本地
$ git commit -m 'add readme'
[master (root-commit) 1c244eb] add readme
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 readme

# 提交变更到远程
$ git push
fatal: No configured push destination.
Either specify the URL from the command-line or configure a remote repository using

    git remote add <name> <url>

and then push using the remote name

    git push <name>
# 由于没有配置远程仓库，因此此处提示需要先添加远程分支，后续会学习
```



## 场景2： 新建的项目直接用 Git 管理

### Git 基本命令

```shell
$ cd dir
$ git init your_project
$ cd your_project
```

### 练习

```shell
# 创建新的项目
$ git init git_learn_2
Initialized empty Git repository in C:/Users/rgwei/AppData/Local/Temp/git_learn_2/.git/

# 进入该目录
$ cd git_learn_2/

# 查看明细
$ ll -al
total 44
drwxr-xr-x 1 rgwei 197121 0 3月  10 12:44 ./
drwxr-xr-x 1 rgwei 197121 0 3月  10 12:44 ../
drwxr-xr-x 1 rgwei 197121 0 3月  10 12:44 .git/
```

# `git init `基础命令总结

## 名称

git-init - 创建一个空的Git存储库或重新初始化现有存储库

## 概要

```
git init [-q | --quiet] [--bare] [--template = <template_directory>]
	  [--separate-git-dir <git dir>]
	  [--shared [= <permissions>]] [目录]
```

| `git init`        | 创建一个空的Git存储库或重新初始化现有存储库    |
| ----------------- | ---------------------------------------------- |
| `git init --help` | 查看帮助文档                                   |
| `git init -q`     | 仅打印错误和警告消息; 所有其他输出都将被抑制。 |



