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