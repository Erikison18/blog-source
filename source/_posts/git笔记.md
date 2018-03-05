---
title: git笔记
date: 2018-03-04 21:04:43
tags: git
categories: 
  - git
---

##  一.起步
##### 1.版本控制
##### 2.Git 基础
直接记录快照，而非差异比较

所有操作都是本地执行

三种状态：已提交（committed），已修改（modified）和已暂存（staged）

三个工作区域：Git 的工作目录，暂存区域，以及本地仓库
##### 3.安装 Git
 Linux 上安装：$ yum install git-core/$ apt-get install git
 
 Mac 上安装:$ sudo port install git-core +svn +doc +bash_completion +gitweb
 
 Windows 上安装:http://msysgit.github.com/
#####  5 初次运行 Git 前的配置
git-config

用户信息:$ git config --global user.name "John Doe"

文本编辑器:$ git config --global core.editor emacs
 
 差异分析工具:$ git config --global merge.tool vimdiff
 
 查看配置信息:git config --list
 
 $ git config user.name
#####  6.获取帮助
$ git help <verb>

$ git help config
##  二.Git基础
##### 1. 取得项目的 Git 仓库
初始化新仓库:$ git init

git add 命令告诉 Git 开始对这些文件进行跟踪，然后提交：

$ git add *

$ git add README
    
$ git commit -m 'initial project version'

现有仓库克隆:

$ git clone git://github.com/schacon/grit.git

$ git clone git://github.com/schacon/grit.git mygrit

##### 2 记录每次更新到仓库
查当前文件状态：$ git status

跟踪新文件：$ git add README

暂存已修改文件：$ git add benchmarks.rb

忽略某些文件：$ cat .gitignore/*.[oa]/*~

查看已暂存和未暂存的更新:$ git diff

已经暂存起来的文件和上次提交时的快照之间的差异: git diff --cached  /  git diff --staged

提交更新:$ git commit

可以用 -m 参数后跟提交说明的方式:$ git commit -m "Story 182: Fix benchmarks for speed"

加上 -a 选项,跳过使用暂存区域,跳过git add 步骤:$ git commit -a -m 'added new benchmarks'

移除文件:$ rm grit.gemspec  

$ git rm grit.gemspec

rm 'grit.gemspec'

$ git rm --cached readme.txt  /  $ git rm log/\*.log  /  $ git rm \*~

移动文件:$ git mv file_from file_to  /  $ git mv README.txt README

##### 3. 查看提交历史

获取该项目源代码：git clone git://github.com/schacon/simplegit-progit.git

回顾下提交历史:$ git log

-p 选项展开显示每次提交的内容差异，用 -2 则仅显示最近的两次更新：$ git log -p -2

简要的增改行数统计：$ git log --stat

限制输出长度:$ git log --since=2.weeks

##### 4. 撤消操作
修改最后一次提交:$ git commit --amend

取消已经暂存的文件:$ git reset HEAD benchmarks.rb

取消对文件的修改: git checkout -- benchmarks.rb
##### 5. 远程仓库的使用
查看当前的远程库:$ git remote -v

$ cd grit

添加远程仓库:git remote add [shortname] [url]

字符串 pb 指代对应的仓库地址:$ git fetch pb

从远程仓库抓取数据:$ git fetch [remote-name]

推送数据到远程仓库:$ git push origin master

查看远程仓库信息:$ git remote show origin

远程仓库的删除和重命名:$ git remote rename pb paul / $ git remote rm paul

##### 6 打标签
列显已有的标签:git tag

新建标签:

含附注的标签:$ git tag -a v1.4 -m 'my version 1.4' / $ git show v1.4

签署标签:$ git tag -s v1.5 -m 'my signed 1.5 tag'

轻量级标签:$ git tag v1.4-lw

验证标签:git tag -v [tag-name]

后期加注标签:$ git log --pretty=oneline

分享标签:$ git push origin v1.5 / $ git push origin --tags

##### 7. 技巧和窍门
自动补全:$ git co<tab><tab>敲两次跳格键（Tab）

Tab 键看看有哪些匹配的：$ git log --s<tab>

Git 命令别名:$ git config --global alias.co checkout

    $ git config --global alias.br branch
    
    $ git config --global alias.ci commit
    
    $ git config --global alias.st status
    
经常设置 last 命令:$ git config --global alias.last 'log -1 HEAD' / $ git last

## 三. Git 分支
##### 1. 何谓分支
新建一个 testing 分支:$ git branch testing

转换到新建的 testing 分支：$ git checkout testing

回到 master 分支:$ git checkout master

##### 2. 分支的新建与合并
新建并切换到该分支，运行 git checkout 并加上 -b 参数：$ git checkout -b iss53

$ vim index.html
 /   $ git commit -a -m 'added a new footer [issue 53]'

创建一个紧急修补分支 hotfix 来开展工作:$ git checkout -b 'hotfix'

git branch 的 -d 选项执行删除操作：$ git branch -d hotfix

分支的合并:$ git checkout master / $ git merge iss53

##### 3. 分支的管理
所有分支的清单：$ git branch

查看各个分支最后一个提交对象的信息: git branch -v

查看哪些分支已被并入当前分支:$ git branch --merged

查看尚未合并的工作：$ git branch --no-merged

##### 4.分支进行开发的工作流程
长期分支

特性分支

##### 5. 远程分支
(远程仓库名)/(分支名) 这样的形式表示远程分支。查看 origin/master 分支

可以运行 git fetch origin 来同步远程服务器上的数据到本地

推送本地分支:$ git push origin serverfix

在远程分支的基础上分化出一个新的分支来：$ git checkout -b serverfix origin/serverfix

跟踪远程分支:$ git checkout --track origin/serverfix / git checkout -b [分支名] [远程名]/[分支名]

删除远程分支:$ git push origin :serverfix

##### 6. 分支的衍合
用 git rebase 的 --onto 选项指定新的基底分支 master：$ git rebase --onto master server client