
<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [通过git log 查看版本演变历史](#通过git-log-查看版本演变历史)
	- [简洁的查看](#简洁的查看)
	- [查看最近的几次](#查看最近的几次)
- [课堂练习](#课堂练习)
- [基础命令`git log`](#基础命令git-log)
	- [帮助](#帮助)

<!-- /TOC -->
# 通过git log 查看版本演变历史

## 简洁的查看

```shell
git log --oneline
```
并非字面意义的一行，而是打印11行

## 查看最近的几次

```shell
git log -n4 --oneline
```
`-n4 代表只打印4行`

# 课堂练习

1. 查看版本演变历史，只查看最近的3次
2. 根据其中一次版本编号，创建分支temp
3. 修改temp分支中的文件，并提交
4. 查看temp分支的版本演变历史
5. 查看所有分支的版本演变历史
6. 通过图形化方式查看所有分支的版本演变历史
7. 切换到master分支，查看tmp分支的版本演变历史


```shell
git log -n3 --oneline
git checkout -b temp xxx
add temp.txt
git add -A
git commit -m 'add temp.txt'
git log
git log --all --oneline -n3
git log --all --graph --oneline -n3
git checkout master
git log --online -n3 temp
```

# 基础命令`git log`

## 帮助

```shell
git help log
```
