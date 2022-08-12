# Git 

## 简介

Git是什么？

Git是目前世界上最先进的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。

什么是“**版本控制**”？为什么要关心它呢？ 

​	举例：

- 如果你用Microsoft Word写过长篇大论，那你一定有这样的经历：想删除一个段落，又怕将来想恢复找不回来怎么办？有办法，先把当前文件“另存为……”一个新的Word文件，再接着改，改到一定程度，再“另存为……”一个新文件，这样一直改下去，最后你的Word文档变成了这样：

 ![lots-of-docs](https://www.liaoxuefeng.com/files/attachments/918921393733152/0) 

- 如果你是位图形或网页设计师，可能会需要保存某一幅图片或页面布局文件的所有修订版本(这或许是你非常渴望拥有的功能)。

**版本控制**就是一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统。在本书所展示的例子中，我们对保存着软件源代码的文件作版本控制，但实际上，可以对任何类型的文件进行版本控制。有了它就可以将某个文件回溯到之前的状态，甚至将整个项目都回退到过去某个时间点的状态，可以比较文件的变化细节，查出最后是谁修改了哪个地方，从而找出导致怪异问题出现的原因，又是谁在何时报告了某个功能缺陷等等。 使用版本控制系统通常还意味着，就算你乱来一气把整个项目中的文件改的改，删的删了，这也没有关系，你也照样可以很容易地就恢复到原先的样子。但额外增加的工作量却微乎其微。

 ![img](https://www.runoob.com/wp-content/uploads/2015/02/git-process.png) 

## 安装

在使用Git前我们需要先安装 Git。Git 目前支持 Linux/Unix、Solaris、Mac和 Windows 平台上运行。

Git 各平台安装包下载地址为：http://git-scm.com/downloads

- Windows 平台上安装

  安装包下载地址：https://gitforwindows.org/
  官网慢，可以用国内的镜像：https://npm.taobao.org/mirrors/git-for-windows/

  完成安装之后，就可以使用命令行的 git 工具（已经自带了 ssh 客户端）了，另外还有一个图形界面的 Git 项目管理工具。在开始菜单里找到"Git"->"Git Bash"，会弹出 Git 命令窗口，你可以在该窗口进行 Git 操作配置。

更详细教程：https://blog.csdn.net/mukes/article/details/115693833
可视化工具小乌龟：https://www.cnblogs.com/tzwbk/p/13896509.html



## 配置

在安装完成 Git 后，开始正式使用前，是需要有一些全局设置的，如用户名、邮箱。 

**设置的主要命令是 `git config:`**

注意`git config`命令的`--global`参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。	

```
git config --global user.name "Your Name"      		//设置用户名
git config --global user.email "email@example.com"  //设置邮箱
git config -l									//查看所有的已经做出的配置
```

​	  其中， --global 指定为全局配置，不使用该参数，则为当前所在仓库配置。

 

## 连接Gitee/GitHub

 Gitee 提供了基于SSH协议的Git服务，在使用SSH协议访问仓库之前，需要先配置好账户/仓库的SSH公钥。 

 **你可以按如下命令来生成 sshkey:** 

```
ssh-keygen -t rsa -C "youremail@example.com"
```

查看公钥

```
cat ~/.ssh/id_rsa.pub
```

 密钥类型可以用 -t 选项指定。如果没有指定则默认生成用于SSH-2的RSA密钥。这里使用的是rsa。  同时在密钥中有一个注释字段，用-C来指定所指定的注释，可以方便用户标识这个密钥，指出密钥的用途或其他有用的信息。所以在这里输入自己的邮箱或者其他都行。 

更详细教程：https://www.win7zhijia.cn/win10jc/win10_47245.html



## 常用命令

![](C:\Users\Administrator\Desktop\git 学习\9d64a05c0bed45debba481cd227c6613.jpg)



![](C:\Users\Administrator\Desktop\git 学习\23d380d2ab7546d795a6be2dc769077e.png)



Git 工作流:
Git 常用的是以下 6 个命令：git clone、git push、git add 、git commit、git checkout、git pull

![](C:\Users\Administrator\Desktop\git 学习\614e5c7e19b7422cb3913241dbb6f708.jpg)

说明：
workspace：工作区
staging area：暂存区/缓存区
local repository：版本库或本地仓库
remote repository：远程仓库

## 初始化和推送流程

1. 创建版本库

    ```
    git init
    ```

2. 用命令`git add`告诉Git，把文件添加到仓库： 

    ```
    git add readme.txt
    ```

3. 用命令`git commit`告诉Git，把文件提交到仓库： 

    ```
    git commit -m "wrote a readme file"
    ```

4. 推送到远端

   ```
   git push -u origin "master"
   ```

   ![1660203432440](C:\Users\Administrator\Desktop\git 学习\1660203432440.png)