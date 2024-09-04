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
deleted:删除未提交
modified:修改未提交
Untracked:新文件未提交
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

## 查看单个文件历史版本

```
git log filename
```



## 删除文件

```
##普通删除文件
rm filename
//这个操作后查看状态会提示未提交到缓存，需要进行add commit操作
#git 删除文件
git rm filename
//这个操作后查看状态没有提示，他会自动帮我们add 我们只需要进行commit 操作

#git rm 后恢复文件
在未commit前，使用git rm 删除文件后可以使用 git reset，git checkout恢复
```

## 查看提交历史

```
#查看当前版本库的提交历史
git reflog
```



## Git基本组成框架

```
workspace：开发者工作区间
index：缓存区
Repository：本地仓库
Remote：远程仓库
```



## Git rm 后恢复文件

```
#进行git rm删除文件后，未commit前可恢复文件

-->
31926@LAPTOP-6RVPE2IE MINGW64 /e/Neusiri/b/Learn/0904 (master)
$ git rm test.c
rm 'Learn/0904/test.c'

31926@LAPTOP-6RVPE2IE MINGW64 /e/Neusiri/b/Learn/0904 (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    test.c

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   "git\345\237\272\346\234\254\344\275\277\347\224\250.md"


31926@LAPTOP-6RVPE2IE MINGW64 /e/Neusiri/b/Learn/0904 (master)
$ git reset
Unstaged changes after reset:
M       Learn/0904/git基本使用.md
D       Learn/0904/test.c

31926@LAPTOP-6RVPE2IE MINGW64 /e/Neusiri/b/Learn/0904 (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   "git\345\237\272\346\234\254\344\275\277\347\224\250.md"
        deleted:    test.c

no changes added to commit (use "git add" and/or "git commit -a")

31926@LAPTOP-6RVPE2IE MINGW64 /e/Neusiri/b/Learn/0904 (master)
$ git checkout test.c
Updated 1 path from the index

31926@LAPTOP-6RVPE2IE MINGW64 /e/Neusiri/b/Learn/0904 (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   "git\345\237\272\346\234\254\344\275\277\347\224\250.md"

no changes added to commit (use "git add" and/or "git commit -a")

```

## 创建分支

```
#创建分支后会自动切换
git chechkout -b dev

#查看当前是哪个分支
git branch
```
