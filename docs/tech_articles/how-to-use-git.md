## 一、下载安装Git

下载地址：[下载Git](https://git-scm.com/downloads)  

下载完成后根据提示安装。    

安装完成后，输入两条命令来设置本地Git仓库的用户名和邮箱：   

```bash
git config --global user.name "Rick"
git config --global user.email "1161764559@qq.com"
```

### 创建一个初始化空仓库

创建一个空目录：    

`mkdir learngit`     

切换到该目录下：`cd learngit`

查看当前目录：`pwd`   

初始化该目录：  

```bash
git init
Initialized empty Git repository in F:/learngit/.git/
```

初始化后，在该目录下自动生成 `.git` 目录  

创建一个文件：  

```bash
touch readme.txt
```

打开文件输入一些内容：`vim readme.txt`    

使用两个命令提交文件：

```bash
git add readme.txt
git commit -m "添加文件readme.txt"
```

使用`git status`命令查看仓库的状态，是否有修改了的文件，是否有添加到暂存区未提交的文件。    

## 二、如何与GitHub账号建立通信  

本地仓库与远程仓库的通信依赖于`SSH key`

### 1、在本地通过命令创建`SSH key`   

```bash
ssh-keygen -t rsa -C "1161764559@qq.com"
```

输入这条命令之后，一路回车  

```bash
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/Administrator/.ssh/id_rsa):
Created directory '/c/Users/Administrator/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/Administrator/.ssh/id_rsa  //这里是保存密钥的地址
Your public key has been saved in /c/Users/Administrator/.ssh/id_rsa.pub    //这里是保存密钥的地址
The key fingerprint is:
SHA256:8Ve5J+t9YiDGNn+zTM0TZTaq462xwjXsyq+m84fgZTA 1161764559@qq.com
The key's randomart image is:
+---[RSA 3072]----+
|                 |
|               . |
|        .     o.+|
|       E o   ..+o|
|        S.o ..o..|
|       . o*=o  *.|
|      . =o+B..o.o|
|       o.=.o*+=.o|
|       .==*=.+++o|
+----[SHA256]-----+
```

打开这个目录下的这个文件：`/c/Users/Administrator/.ssh/id_rsa.pub`  

打开后，内容如下：

```bash
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDjLcK2wFVtjQr0zTpvyeao7TOO/
CYPLeIgDVjyYeQIizm1LlpdxbNkRorX5tnzf/D7eE34QnvXv7glEvGk0bk8FESK6Dz
YxK909B4A1tA9Yr7yGGUAOgzdoS17fO7eaKi8GKa1xg5NFhrNv/McpWtHjIsftMq8k
WAublnrdd7t4vgNKp8HaqzjEEmGlDrUCxCINMJLSJz60jGQ66alW17NWws5SiFdx7L
PbJs1WMygA0f6VTFyHxh5rEanYRtKvs9oAAZXk51DUuZivKRXlk/5s3jqzcf/tz9ZT
ZTAh0MBl+7vGJUculOX2HfrcT+LmoaT4QktyEBSVgakOUqSC4J5ccUxI+WShLUXCrC
Kylo3Au9PNgYsAwO9lmVmaB4WrTlJt95jZ3F/V+Elves/ThOU3tCBnbZEDESJgXyr6
cApj4oQ+g1RNNLOzAsbPPUei0Vttv191AMiYXz8lKiFr/Ew1tr6sqZ9hHMYN09oRvF
8DaEHWKaFxnQWI2Llj7iITAU= 1161764559@qq.com
```

### 2、打开GitHub，添加密钥

点击右上角的头像的三角号，点击`Settings`    

继续点击`SSH and GPG keys` 

输入一个title，将`/c/Users/Administrator/.ssh/id_rsa.pub`中的内容复制到key内，添加即可。 

## 3、本地库与远程库关联/克隆远程库

### 3.1 本地库与远程库关联

在本地仓库下使用命令：

```bash
git remote add origin git@github.com:rongxu-Github/rongxu-github.git
```

`origin`是仓库别名，可以自己起。    

`git branch`可以查看当前分支名称。  

通常为master。  

如果仓库关联错了，可使用如下命令移除关联：

```bash
git remote rm origin
```

### 3.2 克隆远程库

打开GitHub，点击`Code`，点击`HTTPS`，复制URL    

```bash
https://github.com/rongxu-GitHub/rongxu-github.git
```

输入命令：

```bash
git clone https://github.com/rongxu-GitHub/rongxu-github.git
```

出现如下提示，说明已克隆到本地当前目录下：

```bash
Cloning into 'rongxu-github'...
remote: Enumerating objects: 12, done.
remote: Counting objects: 100% (12/12), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 12 (delta 1), reused 12 (delta 1), pack-reused 0
Receiving objects: 100% (12/12), done.
Resolving deltas: 100% (1/1), done.
```

切换到克隆的仓库目录下，查看相关文件内容：

```bash
cat readme.txt
Git is a distributed version control system.
I think Git is great!
Git is a amazing software.
main branch.
```

## 三、Git控制版本

### 1、分支的创建和切换

#### 创建分支

```bash
git checkout -b login

// 输出如下
Switched to a new branch 'login'
* login // 创建并切换到当前分支
  master // 原分支 
```

#### 查看所有分支

```bash
git branch
```

#### 切换分支

```bash
git checkout master // 切换到主分支
```

### 2、版本回退

查看历史提交版本记录：

```Git
git log
commit 2527684fcb85fac40f1f838e28fc4e930b5343c5 (HEAD -> main, origin/main, origin/HEAD)
Author: rongxu-GitHub <1161764559@qq.com>
Date:   Wed Jan 20 19:17:13 2021 +0800

    xiugai

commit ffe522c4fdb8e4110d20286b307f90f432f49b1c
Author: rongxu-GitHub <1161764559@qq.com>
Date:   Wed Jan 20 18:16:41 2021 +0800

    add new

commit 487b7f0344b201bdf638037a3bc920af7718780b
Author: rongxu-GitHub <1161764559@qq.com>
Date:   Wed Jan 20 17:53:12 2021 +0800

    add new line

commit 008bf1e75569b3082948ca89571f47d7bf96722c
Author: rongxu-GitHub <1161764559@qq.com>
Date:   Wed Jan 20 17:46:01 2021 +0800
```

`git log`命令可以查看历史版本信息，`commit`后面的一串字符就是版本号。    

输入下面的命令就可以回退到指定版本：

```Git
git reset --hard 487b
HEAD is now at 487b7f0 add new line
```

使用下面的命令可以查看历史版本信息：

```
git reflog
487b7f0 (HEAD -> main) HEAD@{0}: reset: moving to 487b
2527684 (origin/main, origin/HEAD) HEAD@{1}: reset: moving to 25276
487b7f0 (HEAD -> main) HEAD@{2}: reset: moving to 487b
2527684 (origin/main, origin/HEAD) HEAD@{3}: clone: from https://github.com/rongxu-GitHub/rongxu-github.git
```

## 四、常见问题

### git提交分支出现already up to date

输入以下命令得以解决：

```git
git checkout master
git reset --hard 分知名
git push --force origin master
```

### git删除本地代码库文件后同步到远程仓库同时删除远程仓库文件

```
1.更新本地代码库
git pull

2.对需要删除的文件、文件夹进行如下操作:
git rm ss.c(删除文件)
git rm -r aaa (删除文件夹)

3.提交修改
git commit -m “Delete files.”

4.将修改提交到远程仓库的xxx分支:
git push origin xxx
```