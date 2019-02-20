## Git

[TOC]



### 一、为什么要使用Git？

#### 1.传统文档管理

![not use git](../images/not_use_git.jpg)



在我们写毕业论文时可能会遇到，多次修改之后的论文命名方式：

```text
论文_改.doc、论文_改改.doc、论文_改改改.doc、论文_改改改改.doc、论文_改改改改再改.doc、
论文_改改改改再改TM不改了.doc
```



#### 2.源代码管理的好处

- 方便多人协同开发
- 方便版本控制



#### 3.Git的诞生

![linux Torvalds](../images/Linus_Torvalds.jpg)

- 作者Linux之父：**Linux Torvalds**

- git开发目的：为了辅助 Linux 内核的开发

- 是 Linux Torvals 在**无奈被逼**的情况下创造的
- 2008年，GitHub 网站上线，为开源项目免费提供 Git 存储，无数开源项目开始迁移至 GitHub
- Git 迅速成为最流行的分布式版本控制系统（没有之一）



### 二、Git结构

#### 1.结构分析

​	`Git`是分布式管理系统。服务器和客户端都有版本控制能力,都能进行代码的提交、合并、...

​	**结构图一：**

![git interview](../images/GIT_interview.png)

​	**结构图二：**

![git structure](../images/work_directory_index.png)



#### 2.本地代码管理

**工作区（Workspace）**：添加`、`修改`、`删除`文件

**暂存区（Index）：**将工作区中的操作完成小阶段的存储，是版本库的一部分

**本地仓库区（Respository）:** 对个人开发的一个小阶段代码存储

- 记录的各版本可以查看或者回退
- 但是在暂存区的版本一旦提交就再也没有了（保存到仓库区中）



### 三、本地仓库操作

#### 1.安装git

```linux
# 在虚拟机上安装
sudo apt-get install git
```



#### 2.查看是否安装成功

```linux
git --version
```



#### 3.创建项目

a.创建一个项目文件夹用于演示（MyProjects）

b.新建本地仓库

```linx
cd ~/MyProjects/
# 初始化
git init

# 会创建一个.git隐藏文件
pyvip@TL:~/MyProjects$ ls -al
total 12
drwxrwxr-x  3 Conner Conner 4096 11月 27 16:22 .
drwxr-xr-x 14 Conner Conner 4096 11月 27 16:22 ..
drwxrwxr-x  7 Conner Conner 4096 11月 27 16:22 .git
```

c.配置个人信息

```linux
# 全局配置个人信息
git config --global user.name "Youkou"
git config --global user.email "python@admin.com"

# 配置信息会保存在家目录下
pyvip@TL:~/MyProjects/.git$ more ~/.gitconfig
[user]
	email = python@admin.com
	name = Youkou
	
# 针对本项目的个人配置信息
git config user.name "Youkou"
git config user.email "python@admin.com"

# 配置信息出现在.git/config文件中
```

d.新建测试文件

```linux
vim test01.py
```

e.查看文件状态

```linux
git status
```

f.将工作区添加到暂存区

```linux
# 添加项目中所有文件
git add .
或者
# 添加指定文件
git add test01.py
```

g.将暂存区文件提交到仓库区

```linux
git commit -m '一些描述'
```

h.查看历史版本

```linux
git log
git reflog
```

>git reflog 可以查看所有分支的所有操作记录（包括commit和reset的操作），包括已经被删除的commit记录，git log 不能察看已经删除了的commit记录



#### 4.回退版本

方法一：

- `HEAD`表示当前最新版本
- `HEAD^`表示当前最新版本的前一个版本
- `HEAD^^`表示当前最新版本的前两个版本，**以此类推...**
- `HEAD~1`表示当前最新版本的前一个版本
- `HEAD~10`表示当前最新版本的前10个版本，**以此类推...**

```git
git reset --hard HEAD^
```



方法二：

**当版本非常多时可选择的方案**

```linux
# 通过每个版本的版本号回退到指定版本
git reset --hard 版本号
```

#### 

#### 5.撤销修改

- 只能撤销工作区、暂存区的代码

  - 撤销工作区代码

    ```linux
    git checkout 文件名
    ```

  - 撤销暂存区代码

    ```linux
    # 第一步：将暂存区代码撤销到工作区
    git reset HEAD  文件名
    # 第二步：撤销工作区代码
    git checkout 文件名
    ```

- 撤销仓库区的代码就相当于回退版本操作


#### 6.版本对比

- 对比本地仓库库与工作区
  - 在工作区，修改文件
  - `git diff HEAD -- test1.py`

- 对比本地仓库各版本代码
  - `git diff HEAD HEAD^ -- test1.py`



#### 7.文件删除

- 确定删除处理

  ```linux
  # 删除文件
  rm 文件名
  # git确定删除文件，对比添加文件git add 
  git rm 文件名
  # 删除后记录删除操作版本
  git commit -m '删除描述'
  ```

- 误删处理，撤销修改

  ```linux
  # 删除文件
  rm 文件名
  # git撤销修改
  git checkout -- 文件名
  ```
