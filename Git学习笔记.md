# Git学习笔记

## 1.1 Git是什么

### 1.1.1 Git：版本管理工具

### 1.1.2 Git工作流程

#### 	git仓库：用于存放提交记录

#### 	暂存区：临时存放被修改的文件

#### 	工作目录：被Git管理的项目目录

## 1.2 Git的使用

### 1.2.1 常用指令

#### 	git config --list 查看已经配置的信息

#### 	git config --global user.name 配置用户名

#### 	git config --global user.name 配置邮箱

![1641991999820](C:\Users\wangjunjie\AppData\Roaming\Typora\typora-user-images\1641991999820.png)

### 1.2.2 Git提交步骤

#### 	git init 初始化仓库

#### 	git status 查看文件状态

#### 	git add 文件列表 追踪文件

#### 	git commit -m 提交信息 向仓库中提交代码

#### 	git log 查看提交记录

#### git checkout 文件名称：将提交的内容覆盖本地内容。

#### git rm --cached 文件：将文件从暂存区中删除

#### git rest --hard commitID:将Git仓库中指定的更新记录恢复，并且覆盖暂存区和工作目录

### 1.2.3 分支

#### 	分支：当前文件的一段副本（备份文件）

#### 	1、主分支（master）：第一次向git仓库提交更新记录时自动产生的一个分支

#### 	2、开发分支（develop）：作为开发的分支，基于master分支创建

#### 	3、功能分支（feature）：开发分支的分支

#### 	1.2.3.1 分支命令

#### 		git branch 查看分支

​			![1641994725152](C:\Users\wangjunjie\AppData\Roaming\Typora\typora-user-images\1641994725152.png)

#### 		git branch 分支名称 创建分支

​			![1641994829492](C:\Users\wangjunjie\AppData\Roaming\Typora\typora-user-images\1641994829492.png)

#### 		git checkout 分支名称 切换分支

​			![1641994873004](C:\Users\wangjunjie\AppData\Roaming\Typora\typora-user-images\1641994873004.png)

#### 		git merge 来源分支 合并分支

​			

#### 		git branch -d 分支名称 删除名称（分支合并后才允许删除）（-D 强制删除）	

​			![1641995251147](C:\Users\wangjunjie\AppData\Roaming\Typora\typora-user-images\1641995251147.png)

### 1.2.4 暂时保存更改

#### 	在git中，可以暂时提取所有分支上所有的改动并存储，让开发人员得到一个干净的工作副本，临时转向其他工作，分支临时切换

#### 	存储临时改动：git stash

#### 	恢复改动：git stash pop	

## 1.3 远程仓库

#### 向远程仓库推送文件

#### git push 远程仓库地址 分支名称

#### git push 远程仓库地址别名 分支名称

#### git push -u 远程仓库地址别名 分支名称

#### 	-u记住推送地址及分支，下次推送只需要输入git push即可

#### git remote add 远程仓库地址别名 远程仓库地址