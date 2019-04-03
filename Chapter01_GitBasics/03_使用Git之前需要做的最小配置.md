[TOC]

# 配置user信息

> 配置user.name 和 user.email

```shell
git config --global user.name 'your_name'
git config --global user.email 'your_email.domain.com'
```

* 仓库中变更的信息会和用户和邮件捆绑在一起，需要配置好user信息。

* 设置，缺省等同于 `--local`
* 清除，`--unset`

```shell
git config --unset --global user.name
git config --unset --global user.email
```

* 优先级 `local > global > system`

# git config 命令

> [官方帮助](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%88%9D%E6%AC%A1%E8%BF%90%E8%A1%8C-Git-%E5%89%8D%E7%9A%84%E9%85%8D%E7%BD%AE)

## 原理

> 命令只是为了更方便地修改配置文件，我们应该知其所以然。

Git 自带一个 `git config` 的工具来帮助设置控制 Git 外观和行为的配置变量。 这些变量存储在三个不同的位置：

1. `/etc/gitconfig` 文件: 包含系统上每一个用户及他们仓库的通用配置。 如果使用带有 `--system` 选项的 `git config` 时，它会从此文件读写配置变量。
2. `~/.gitconfig` 或 `~/.config/git/config` 文件：只针对当前用户。 可以传递 `--global` 选项让 Git 读写此文件。
3. 当前使用仓库的 Git 目录中的 `config` 文件（就是 `.git/config`）：针对该仓库。

每一个级别覆盖上一级别的配置，所以 `.git/config` 的配置变量会覆盖 `/etc/gitconfig` 中的配置变量。

在 Windows 系统中，Git 会查找 `$HOME` 目录下（一般情况下是 `C:\Users\$USER`）的 `.gitconfig` 文件。 Git 同样也会寻找 `/etc/gitconfig` 文件，但只限于 MSys 的根目录下，即安装 Git 时所选的目标位置。

## 语法

`git config [参数]`

| `config 作用域`   | `参数`                | `配置文件`                               | `说明`                         |
| ---------- | --------------------- | ---------------------------------------- | ------------------------------ |
| `一个仓库` | `git config --local`  | `.g`it/config                            | `local`只对某个仓库有效        |
| 当前用户   | `git config --global` | `~/.gitconfig` 或 `~/.config/git/config` | `global`对当前用户所有仓库有效 |
| 当前系统   | `git config --system` | `/etc/gitconfig`                         | `system`对系统所有登陆用户有效 |


## 帮助

```shell
# 查看Manual Page详细帮助信息
$ git help config
# 查看简易帮助信息
$ git config
```

## 练习

> 我的环境为windows

### 1 找到一个仓库，查看该仓库中的所有文件，包含隐藏文件。

```shell
rgwei@DESKTOP-G9S0U3G MINGW64 /
$ ll /c/Users/rgwei/Desktop/GitHub/DBA_Git -a
total 29
drwxr-xr-x 1 rgwei 197121    0 12月 12 20:13 ./
drwxr-xr-x 1 rgwei 197121    0 2月  11 14:27 ../
drwxr-xr-x 1 rgwei 197121    0 12月 12 20:21 .git/
drwxr-xr-x 1 rgwei 197121    0 12月 12 19:57 .idea/
-rw-r--r-- 1 rgwei 197121 1400 12月 12 11:57 README.md
-rw-r--r-- 1 rgwei 197121   13 12月 12 20:13 test.md
drwxr-xr-x 1 rgwei 197121    0 2月  12 10:23 第一章：Git基础/
```

### 2 使用`git config`命令 和 `配置文件` 分别查看**仓库**的配置情况

```shell
rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/GitHub/DBA_Git (master)
$ git config --local --list
core.repositoryformatversion=0
core.filemode=false
core.bare=false
core.logallrefupdates=true
core.symlinks=false
core.ignorecase=true
remote.origin.url=git@github.com:BoobooWei/DBA_Git.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.master.remote=origin
branch.master.merge=refs/heads/master

rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/GitHub/DBA_Git (master)
$ cat .git/config
[core]
        repositoryformatversion = 0
        filemode = false
        bare = false
        logallrefupdates = true
        symlinks = false
        ignorecase = true
[remote "origin"]
        url = git@github.com:BoobooWei/DBA_Git.git
        fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
        remote = origin
        merge = refs/heads/master
heads/master
```

### 3 分别查看当前仓库、当前用户、系统的git配置情况

```shell
rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/GitHub/DBA_Git (master)
$ git config --local --list
core.repositoryformatversion=0
core.filemode=false
core.bare=false
core.logallrefupdates=true
core.symlinks=false
core.ignorecase=true
core.editor=vim
core.excludesfile=~/.gitignore
core.autocrlf=true
remote.origin.url=git@github.com:BoobooWei/DBA_Git.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.master.remote=origin
branch.master.merge=refs/heads/master
alias.amend=commit --amend
alias.amendf=commit --amend --no-edit
alias.br=branch
alias.ct=commit
alias.co=checkout
alias.cp=cherry-pick
alias.df=diff
alias.ds=diff --staged
alias.l=log
alias.lg=log --graph --all --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(bold white)— %an%C(reset)%C(bold yellow)%d%C(reset)' --abbrev-commit --date=relative
alias.lp=log --pretty=oneline
alias.sa=stash apply
alias.sh=show
alias.ss=stash save
alias.st=status
color.ui=auto
color.branch.current=yellow reverse
color.branch.local=yellow
color.branch.remote=green
color.status.added=yellow
color.status.changed=green
color.status.untracked=cyan
color.diff.meta=yellow
color.diff.frag=magenta bold
color.diff.commit=yellow bold
color.diff.old=red bold
color.diff.new=green bold
color.diff.whitespace=red reverse
color.diff-highlight.oldnormal=red bold
color.diff-highlight.oldhighlight=red bold 52
color.diff-highlight.newnormal=green bold
color.diff-highlight.newhighlight=green bold 22
credential.helper=cache --timeout=28800

rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/GitHub/DBA_Git (master)
$ git config --global --list
user.email=weiyaping@jiagouyun.com
user.name=weiyaping
gui.recentrepo=C:/Users/rgwei/Desktop/jigouyun_Git/DevOps-Database-Troubleshooting

rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/GitHub/DBA_Git (master)
$ git config --system --list
http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.required=true
filter.lfs.process=git-lfs filter-process
credential.helper=manager
```

### 4 清空global配置

```shell
# 通过命令查看global配置
$ git config --global --list
user.email=weiyaping@jiagouyun.com
user.name=weiyaping
gui.recentrepo=C:/Users/rgwei/Desktop/jigouyun_Git/DevOps-Database-Troubleshooting

# 通过配置文件查看global配置
rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/GitHub/DBA_Git (master)
$ cat ~/.gitconfig
[user]
        email = weiyaping@jiagouyun.com
        name = weiyaping
[gui]
[gui]
        recentrepo = C:/Users/rgwei/Desktop/jigouyun_Git/DevOps-Database-Troubleshooting
# 清空user.name
rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/GitHub/DBA_Git (master)
$ git config --global --unset user.name
# 清空user.email
rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/GitHub/DBA_Git (master)
$ git config --global --unset user.email
# 再次查看global配置
rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/GitHub/DBA_Git (master)
$ git config --global --list
gui.recentrepo=C:/Users/rgwei/Desktop/jigouyun_Git/DevOps-Database-Troubleshooting

rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/GitHub/DBA_Git (master)
$ cat ~/.gitconfig
[user]
[gui]
[gui]
        recentrepo = C:/Users/rgwei/Desktop/jigouyun_Git/DevOps-Database-Troubleshooting
```

### 5 重新配置global

```shell
rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/GitHub/DBA_Git (master)
$ git config --global user.name booboowei

rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/GitHub/DBA_Git (master)
$ git config --global user.email rgweiyaping@hotmail.com

rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/GitHub/DBA_Git (master)
$ git config --global --list
gui.recentrepo=C:/Users/rgwei/Desktop/jigouyun_Git/DevOps-Database-Troubleshooting
user.name=booboowei
user.email=rgweiyaping@hotmail.com
```

 

# git config 配置文件详解

> 常见的配置，具体参见[官方帮助](https://git-scm.com/docs/git-config.html)

## core 核心

```shell
[core]
	editor = vim
	excludesfile = ~/.gitignore
	autocrlf = true
```

核心设置部分包含与git相关的各种不同设置。我们设置到的部分有：

* `editor = vim` 设置要用于编辑提交消息的编辑器（如果未设置此值，git将首先尝试从环境变量VISUAL或EDITOR读取你当前的编辑器，如果获取不到，最终会使用vi）。

* `excludesfile = ~/.gitignore`允许指定全局性质的`.gitignore`文件。每个git存储库都可以设置特定的项目级别的`.gitignore`文件，该文件指定要从版本控制中排除的文件。但很多时候，每个git存储库中的一些文件都是相同的（例如，macOS上的.DS_Store，或者当你是Python开发人员时是*.pyc），为了避免重复设置，可以设置全局性质的`.gitignore`，该设置就会对该用户下所有的项目都生效。

* `autocrlf = input`。 由于Windows使用的是与Unix和MacOS不同的行结尾，如果来自不同操作系统的人员提交到同一个存储库，则可能会造成一些混乱。关于换行设置三种操作系统（windows，linux和macOS）的是不一样的：MacOS/Linux设置：autocrlf = input  Windows上的autocrlf = true）

## alias 别名

* git别名是我们日常进行git配置使用最多的一部分内容。

* 在git使用中，为了便捷减少输入，git提供了别名机制来将标准的git命令自定义为自己习惯使用的命令。

* 我们可以将git的命令设定别名为为1或2个字母的快捷方式。

```shell
[alias]
	amend = commit --amend
	amendf = commit --amend --no-edit
	br = branch
	ct = commit
	co = checkout
	cp = cherry-pick
	df = diff
	ds = diff --staged
	l = log
	lg = log --graph --all --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(bold white)— %an%C(reset)%C(bold yellow)%d%C(reset)' --abbrev-commit --date=relative
	lp = log --pretty=oneline
	sa = stash apply
	sh = show
	ss = stash save
	st = status
```

此处我们按字母顺序排列别名。注意到这个log命令lg，我们美化了log的显示，是的lg显示更加好看，简洁的图表，说明了仓库库随着时间的推移如何演变。

## color 配色

给你的工作终端设置一个好看的颜色也是每一个码农一直孜孜以求的目标，那就看本部分：

```shell
[color]
	ui = auto # UI的默认设置。它在输出直接到终端时为输出着色，但在输出重定向到管道或文件时会省略颜色控制代码，以免导致问题。分支和状态部分正在以下列方式更改git branch和git status命令的输出颜色。
[color "branch"]
	current = yellow reverse
	local = yellow
	remote = green
[color "status"]
	added = yellow
	changed = green
	untracked = cyan
[color "diff"] # 在执行diff命令时候系统展示的颜色
	meta = yellow
	frag = magenta bold
	commit = yellow bold
	old = red bold
	new = green bold
	whitespace = red reverse
[color "diff-highlight"]
	oldNormal = red bold
	oldHighlight = red bold 52
	newNormal = green bold
	newHighlight = green bold 22
```



## credential 凭据

```shell
[credential]
	helper = cache --timeout=28800
```

凭据部分用来指定希望你需要默认保存的账号和密码。

默认情况下，git根本不会包存储凭据，所以每次连接时（http（s）性质的仓库）都会提示输入用户名和密用,这会很麻烦，你可以在此处设置保存户名密码，这样就可以不用每次都输入了（当然最好方式，是用ssh证书方法，即安全又方便）。

凭据一般可以通过两种方式保存，保存在带有store选项的文件中（它将使用你的凭据创建纯文本文件），或使用cache选项将它们存储在内存中。当然根据你系统不同，还可以使用第三方的方式，比如MacOS下的osxkeychain，Windows下的Git Credential Manager）。

此处我们使用的是，通过内存cache的方式，默认是15分钟，此处我们设置为8小时。

## push 推送

```shell
[push]
default = current
```

`git push`命令中包含分支的名称，如果你没有添加，可能导致意外的行为（例如我正在开发dev分支，但不小心，push到了master分支）。为了防止这种错误，我给push设置了default = current选项。现在，如果忘记包含分支的名称，git将尝试推送到具有相同名称的分支。如果它在远程库中找不到具有相同名称的分支，会新创建一个。

# 课后实践

请动⼿⽐⼀⽐，`local` 和`global` 的优先级。
1. 在 Git 命令⾏⽅式下，⽤ init 创建⼀个 Git 仓库。
2. cd 到 repo 中。
3. 配置 global 和 local 两个级别的 user.name 和 user.email。
4. 创建空的 commit
  $ git commit --allow-empty -m ‘Initial’
5. ⽤ log 看 commit 信息，Author 的 name 和 email 是什么？
  $ git log

```shell
rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/20190212
$ git init my_repo
Initialized empty Git repository in C:/Users/rgwei/Desktop/20190212/my_repo/.git/

rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/20190212
$ ll
total 0
drwxr-xr-x 1 rgwei 197121 0 2月  12 13:31 my_repo/

rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/20190212
$ cd my_repo/

rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/20190212/my_repo (master)
$ git config --local user.name weiyaping

rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/20190212/my_repo (master)
$ git config --local user.email weiyaping@jiagouyun.com

rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/20190212/my_repo (master)
$ git commit --allow-empty -m 'Initial'
[master (root-commit) ca14e14] Initial

rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/20190212/my_repo (master)
$ git log
commit ca14e1450e7b37275b732ea7184687b3be709ff3 (HEAD -> master)
Author: weiyaping <weiyaping@jiagouyun.com>
Date:   Tue Feb 12 13:32:36 2019 +0800

    Initial

rgwei@DESKTOP-G9S0U3G MINGW64 ~/Desktop/20190212/my_repo (master)
$ cat .git/config
[core]
        repositoryformatversion = 0
        filemode = false
        bare = false
        logallrefupdates = true
        symlinks = false
        ignorecase = true
[user]
        name = weiyaping
        email = weiyaping@jiagouyun.com
```



