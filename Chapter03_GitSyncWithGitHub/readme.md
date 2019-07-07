# Git与GitHub的简单同步

|课程|内容|备注|
|:--|:--|:--|
|30 | 注册一个GitHub账号|[https://github.com/](https://github.com/)|
|31 | 配置公私钥|[https://help.github.com/cn](https://help.github.com/cn)|
|32 | 在GitHub上创建个人仓库|[https://help.github.com/cn](https://help.github.com/cn)|
|33 | 把本地仓库同步到GitHub|[https://help.github.com/cn](https://help.github.com/cn)|


```shell
git remote -v 查看远程版本库信息
git remote add github <url> 添加github远程版本库
git fetch github 拉取远程版本库
git merge -h 查看合并帮助信息
git merge --allow-unrelated-histories github/master 合并github上的master分支（两分支不是父子关系，所以合并需要添加 --allow-unrelated-histories）
git push github 推送同步到githup仓库
```
