---
title: 使用github做代码贡献的基本流程
tags:
  - Git
categories:
  - 开发笔记
cover: https://picsum.photos/1080/1080?random=1221
feature: false
date: 2022-08-16 17:51:01
---
# 使用github做代码贡献的基本流程
1. fork,复制其他作者的代码仓库到自己的账号，后续可以直接在自己的账号进行代码修改，与原作者代码仓库互不影响。


2. ` git clone https://github.com/自己用户名/项目名`克隆到本地编辑器
3. `git remote -v`查看远程
4.
    - `git branch`查看分支
    -  `git checkout [分支名称]`切换到要修改的分支
    -  `git checkout -b [分支名称1]`**在要修改的分支上新建一个分支来修改**。
    
5.利用git基础命令，在本地进行提交。<br>
- `git status` 查看哪些文件被修改<br>
- `git diff`查看修改内容<br>
-  增加内容到暂存区
    -  `git add  [文件名1][文件名2] `从工作区添加指定文件到暂存区
    -  `git add . `将工作区的被修改的文件和新增的文件提交到暂存区，不包括被删除的文件（！常用
    -  `git add -u .` u指update，将工作区的被修改的文件和被删除的文件提交到暂存区，不包括新增文件
    -  ` git add -A .` A指all，将工作区被修改、被删除、新增的文件都提交到暂存区
- 提交暂存区的代码到本地仓库（加-m是指直接在后面写上版本的注释，不加-m的话会用一个vim打开文件让你写入massage，有未追踪的文件将会失败，需要add加入暂存区。）
    -  `git commit -m [massage]` 将暂存区所有文件添加到本地仓库（！常用
    - `git commit [file1] [file2] -m [massage`] 将暂存区指定文件添加到本地仓库
    - `git commit -am [massage]` 将工作区的内容直接加入本地仓库
    - `git commit --amend` 快速将当前文件修改合并到最新的commit，不会产生新的commit。在提交commit后发现还有部分文件修改忘记提交了可以用该命令
-  push将本地仓库提交到远程仓库
    -  `git push` 将文件添加到远程仓库
    -  `git push -f` 强制提交，当我们本地reset到旧的版本时，然后普通push会被拦截，因为此是本地HEAD指向比远程库还要旧
    -  `git push origin [branch-name]` 推送当前本地分支到指定远程分支
 
 6.到Github上将自己修改的分支Pull request到源作者上，**new pull request->create pull request.**
 源作者测试成功便点击**Squash and merge->Confirm squash and merge.**.则加入开源项目成功。


 7.同步源作者最新代码<br>
     （0）`git remote add upstream [源作者github仓库]`,添加源作者的远程仓库
     （1）切换到更新的分支（这也是为什么修改的时候要新建分支，因为拉取会方便很多）
     （2）`git pull --rebase upstream [分支名称]`
     



