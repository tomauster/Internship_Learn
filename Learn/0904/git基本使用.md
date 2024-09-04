# Git基本使用

## 初始化Git仓库

进入目录，初始化仓库

```bash

$git init
Initialized empty Git repository in E:/Neusiri/b/.git/


```

## 查看目录

```bash
$ls -ah
./  ../  .git/  Learn/

```

## 查看相关目录

```bash
31926@LAPTOP-6RVPE2IE MINGW64 /e/Neusiri/b (master)
$ cd .git

31926@LAPTOP-6RVPE2IE MINGW64 /e/Neusiri/b/.git (GIT_DIR!)
$ ls -ah
./  ../  HEAD  config  description  hooks/  info/  objects/  refs/

```

## 新建文件加入到本地仓库

```
#创建文件
31926@LAPTOP-6RVPE2IE MINGW64 /e/Neusiri/b/Learn/0904 (master)
$ touch test

31926@LAPTOP-6RVPE2IE MINGW64 /e/Neusiri/b/Learn/0904 (master)
$ ls -ah
./  ../  git基本使用.md  test


#添加到仓库提交缓存
git add test


#添加描述信息
git commit -m "add new file \"test\""

-->
$ git commit -m "add new file \"test\""
[master (root-commit) 38ad55b] add new file "test"
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 Learn/0904/test


#改写提交
git commit --amend


#查看日志
git log

-->
$ git log
commit 011b07ecf9562b0ce9b61714e3271aac0c75e795 (HEAD -> master)
Author: tomauster <3192684562@qq.com>
Date:   Wed Sep 4 08:50:18 2024 +0800

    add new a file "test"

```

## 回滚历史版本



--soft    回复头指针，已经add的暂存区以及工作区间所有东西都不变

--mixed    恢复头指针以及已经add的暂存区，工作区间不变

--hard    全部恢复



```
#查看历史版本
git log


#使用命令回滚
git reset --hard id

-->
31926@LAPTOP-6RVPE2IE MINGW64 /e/Neusiri/b/Learn/0904 (master)
$ ls -ah
./  ../  git基本使用.md  test  test1.md

31926@LAPTOP-6RVPE2IE MINGW64 /e/Neusiri/b/Learn/0904 (master)
$ git reset --hard HEAD^
HEAD is now at a81f272 add i file "test"

31926@LAPTOP-6RVPE2IE MINGW64 /e/Neusiri/b/Learn/0904 (master)
$ ls -ah
./  ../  test

```

## 查看修改状态

```
A:未修改
AM:修改
Untracked:未提交
modfile:新文件未提交
```

## 工作区，缓存区

```
#将所有文件添加到缓存区
git add --all
//这个命令会将当前目录下包括子目录的所有操作进行提交
//包括删除文件的操作


git add .
//这命令与git add --all 相同，但是不会将删除操作提交
```

## 文件恢复

```
#区别于回滚操作，这个操作可以将单个文件恢复到上一次提交的状态
git checkout --file
```


