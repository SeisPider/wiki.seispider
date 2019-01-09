+++
date = "2017-08-02T16:24:01+08:00"
title =  "Fundamental Usage"
+++
# 版本回退
* 查看版本log
```
$ git log --pretty=oneline
3628164fb26d48395383f8f31179f24e0882e1e0 append GPL
```
`3628164fb26d48395383f8f31179f24e0882e1e0`是版本号。

* 版本回退
```
$ git reset --hard HEAD^
```
`HEAD`表示当前版本，`HEAD^`表示上一个版本，`HEAD~100`表示前100个版本。
或者--hard后面可以加版本号。
```
$ git reset --hard 3628164
```
写版本号前多少位没关系，关键是能够定位到只有一个版本。

`Note:`git reflog 记录了用户所有的操作。

# 删除文件
通常利用`rm`删除了文件，此时可以有两种选择：

* 在版本库中删除文件`git rm file`
* 删错了，恢复文件`git checkout --file`
`git checkout`其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。

# 从coding.net克隆仓库
```bash
git clone git@git.coding.net:SeisPider/repo_name.git
```
