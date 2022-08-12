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

![](.\9d64a05c0bed45debba481cd227c6613.jpg)



![](.\23d380d2ab7546d795a6be2dc769077e.png)



Git 工作流:
Git 常用的是以下 6 个命令：git clone、git push、git add 、git commit、git checkout、git pull

![](.\614e5c7e19b7422cb3913241dbb6f708.jpg)

说明：
workspace：工作区
staging area：暂存区/缓存区
local repository：版本库或本地仓库
remote repository：远程仓库

## 基础操作

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

4. 添加远端仓库

   ```
   git remote add origin git@gitee.com:HRlijie/git_test.git
   ```

5. 推送到远端

   ```
   git push -u origin "master"
   ```

   ![1660203432440](.\1660203432440.png)



## 分支管理

详细说明：https://blog.csdn.net/bobozai86/article/details/119521826

常见的分支策略有以下三种：GitFlow、GitHubFlow以及GitLabFlow

### Git Flow模式

通常包含五种类型的分支：Master分支、Develop分支、Feature分支、Release分支以及Hotfix分支:

   - **Master分支**：主干分支，也是正式发布版本的分支，其包含可以部署到生产环境中的代码，通常情况下只允许其他分支将代码合入，不允许向Master分支直接提交代码（对应生产环境）
- **Develop分支**：开发分支，用来集成测试最新合入的开发成果，包含要发布到下一个Release的代码（对应开发环境）
- **Feature分支**：特性分支，通常从Develop分支拉出，每个新特性的开发对应一个特性分支，用于开发人员提交代码并进行自测。自测完成后，会将Feature分支的代码合并到Develop分支，进入下一个Release。
- **Release分支**：发布分支，发布新版本时，基于Develop分支创建，发布完成后，合并到Master和Develop分支（对应测试环境）
- **Hot fix分支**：热修复分支，生产环境发现新Bug时创建的临时分支，问题验证通过后，合并到Master和Develop分支。

通常开发过程中新特性的开发过程如下：
       1. 从Develop分支拉取一条Feature分支，开发团队在Feature分支上进行新功能开发；
    2. 开发完成后，将Feature分支合入到Develop分支，并进行开发环境的验证；
    3. 开发环境验证完成，从Develop分支拉取一条Release分支，到测试环境进行SIT/UAT测试；
    4. 测试无问题后，可将Develop分支合入到Master分支，待发版时，直接将Master分支代码部署到生产环境

![](.\2811679-20220705075624666-1361846447.png)

![![git-flow开发.jpg](.\11.awebp) 

### GitHub-Flow 模式

GitHub-Flow 模式相较于 Git-Flow 模式更为简洁，没有了 Git-Flow 模式中 develop ， hoxfix 和 release 分支，对于 GitHub-Flow 模式来说，发布版本应该是持续的，快速的。feature 分支即 develop 分支，master 分支即 release 分支，对于 hotfix 的处理，GitHub-Flow 模式认为本质上也是特性修改，处理方式和 feature 分支理念是一致的。总的来说，所有特性修改都能快速集成到 master 上发布，小步快走，快速迭代。

 ![github-flow.jpg](.\22.awebp) 

GitHub-Flow 模式在特性分支开发模式中最为简洁，持续集成部署的效率最高。因为所有特性修改的内容会频繁的合入 master 中，并频繁进行部署，这意味着可以最小粒度部署特性修改的代码，在当前倡导持续快速交付的环境下，显然这种模式具有很大的优势。但因为没有 release 分支的存在，需要建立完善的 rollback 机制来保障线上服务问题后的快速恢复。



## Tag标签

在我们用git做版本管理的时候，每次提交代码都会生成唯一标识本次提交的编码，对于这个编码我们直观的看是没有任何意义的。为了很好标识每个版本的变化，我们会在每个版本发布的同时打上一个tag，通常和版本名称相同。

​    比如我们开发了V1.0、V1.1，不同的版本对应不同的代码，当我们在V1.1上面发现bug时，但并不确定V1.0是否存在bug，那我们怎么确认V1.0存在bug呢？怎么知道哪些提交的代码属于V1.0？此时tag就很有用了。我们在发布V1.0和V1.1这两个版本时，分别为这两个版本加上tag1.0和tag1.1，当我们需要验证V1.0是否存在bug时，切换到tag1.0上就可以验证了。



## 进阶使用

### 解决冲突

1. 两个分支之间进行push、pull操作。
		- 一般是把远程的分支pull到本地
	- 一般是把本地分支push到远程

2. 两个分支之间进行merge操作
   
   - 一般是本地A分支merge到本地B分支，操作时首先切换到B分支，然后执行merge A

  git的合并中产生冲突的具体情况：
　　<1>两个分支中修改了同一个文件（不管什么地方）
　　<2>两个分支中修改了同一个文件的名称
  两个分支中分别修改了不同文件中的部分，不会产生冲突，可以直接将两部分合并。 

#### 情况1：push操作

![](.\8456a0f104264f7587f67e51056ca09b.png)

造成这种情况是因为，本地master分支修改了A.txt文件，并且远程master的A.txt文件也被修改了（此时我不知道远程被改了）。
解决方案就是（其实报错截图很清楚了，在push之前先pull一下），当我们pull完之后会发现本地分支的A.txt文件有变化如下图，然后手动选择一个要保留的，是保留第二行还是保留第四行，然后删除其他所有行，保存后执行命令add、commit（会弹出对话框提示冲突信息，直接:q即可）。然后git push即可

### ![](.\ba1960a3fae041338fb8a96c9b3170ea.png)

#### 情况2：merge操作

![](.\0c7f838602f244049694bafcbbd370a1.png)

造成这种情况的原因是，我在本地分支master上修改了B.txt文件(修改内容echo b >> B.txt)，然后add、commit。然后本地分支conflict也修改了B.txt文件(修改内容echo a >> B.txt)，然后add、commit。接下来我就切换到本地master分支执行merge，报错。
解决方案就是，当你执行merge后，查看本地master分支的B.txt文件发现有变化如下图，选择保留第二行还是保留第四行，然后删除其他所有行，保存后执行命令add、commit（会弹出对话框提示冲突信息，直接:q即可）。到此代码合并完毕。
![](.\2f7f50b4d08445b598274373f838ddba.png)



详细:https://www.cnblogs.com/gavincoder/p/9071959.html

### 暂存修改

一个被提交了的改动会被永久地保存在仓库（repository）中。然而，在你日常工作中你经常需要“暂时地”保存一下你的一些本地改动。例如，如果你正在开发一个新的功能，但是与此同时又得到了一个错误报告，并且需要马上修复它，而你现在的本地改动又和这个错误毫无关系，因此你必须暂时地停止新功能的开发，来开始着手修复这个错误。并且你还想要保存那些已完成的开发工作，以便之后能继续来完成它。
像这样的情况会随时发生，比如你必须要开始一个新的工作，而在你的当前工作版本中还有一些并不想立即提交的本地改动。在处理好这些本地改动的同时，我们还需要把当前的工作副本（working copy）清理出来，Git 提供的 “储藏（Stash）” 功能可以非常好地解决这个问题。

可以把储藏想象成一种剪贴板，它会获取你工作副本（working copy）中的所有改动，并且保存到一个新的剪贴板上。然后你就会得到一个“干净”的工作副本，也就是说一个不存在任何改动的工作目录。

之后你随时都可以重新调回那些保存在剪贴板中的改动到你的工作副本中来，从而继续你之前没有完成的工作。

你可以建立多个储藏单元，不仅仅局限于存储一组变化。同样，储藏也会不绑定在你所处的当前分支或是任何其它分支上，如果你想要调回任意一个储藏单元，它的改动将会被应用在你当前的 HEAD 分支上。

详细：https://blog.csdn.net/it_xiangqiang/article/details/125643351

### 子模块

有种情况我们经常会遇到：某个工作中的项目需要包含并使用另一个项目。 也许是第三方库，或者你独立开发的，用于多个父项目的库。 现在问题来了：你想要把它们当做两个独立的项目，同时又想在一个项目中使用另一个，或者有多个项目公用同一个。

我们可以通过Git 通过子模块来解决这个问题。 子模块允许你将一个 Git 仓库作为另一个 Git 仓库的子目录。 它能让你将另一个仓库克隆到自己的项目中，同时还保持提交的独立。

#### 子模块的添加
添加子模块非常简单，命令如下：

git submodule add <url> <path>

其中，url为子模块的路径，path为该子模块存储的目录路径。

执行成功后，git status会看到项目中修改了.gitmodules，并增加了一个新文件（为刚刚添加的路径）

git diff --cached查看修改内容可以看到增加了子模块，并且新文件下为子模块的提交hash摘要

git commit提交即完成子模块的添加

子模块的使用
克隆项目后，默认子模块目录下无任何内容。需要在项目根目录执行如下命令完成子模块的下载：

```
git submodule init
git submodule update
```

或者

```
git submodule update --init --recursive
```

#### 子模块的更新

子模块的维护者提交了更新后，使用子模块的项目必须手动更新才能包含最新的提交。

在项目中，进入到子模块目录下，执行 `git pull`更新，查看`git log`查看相应提交。

完成后返回到项目目录，可以看到子模块有待提交的更新，使用`git add`，提交即可。

详细：https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E5%AD%90%E6%A8%A1%E5%9D%97

# gitee

详细：https://blog.csdn.net/m0_51411338/article/details/124380516

gitee免费部署静态网站：https://blog.csdn.net/young_0609/article/details/124813681

# github

详细：https://blog.csdn.net/qq_34229228/article/details/86445535

github免费部署静态网站：https://blog.csdn.net/qq1808814025/article/details/105895378

