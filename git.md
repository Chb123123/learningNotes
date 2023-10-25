### git 的基本使用

分布式版本控制系统的特点：

1. 服务器保存文件的所有更新版本
2. 客户端是服务器的完整备份，并不是只保留文件的最新版本

分布式版本控制系统的优点：

1. 联网运行，支持多人协作开发
2. 客户端断网以后支持离线本地提交版本更新
3. 服务器故障或损坏后，可以使用任何一个客户端的备份进行恢复

git 记录快照：

缺点：占用磁盘空间大

优点：版本切换时非常快，因为每个版本都是完整的文件快照，切换版本时直接恢复目标文件的快照即可

特点：空间换时间

下载Git 网址：https://git-scm.com/downloads

设置自己的用户名和邮箱

git config --global user.name '用户名'

git config --global user.email '邮箱地址'

#### 查看当前仓库的状态 

#### git status  

如果想要以精简的方式查看可以在后面添加一个 -s : git status -s

状态为 绿色的M表示以修改 并以暂存

状态为 绿色的A表示 之前未被跟踪的文件 回来被加入到了暂存区

红色的M表示已经修改但是没有加入到暂存区



#### 跟踪文件：

 git add + 文件名



#### 撤销对文件的修改：

把工作区对应文件的修改，还原成Git仓库中所保存的版本

操作结果：所有的修改会丢失，且无法恢复！危险性比较高，慎重操作

git checkout -- + 想撤销对文件操作的文件名

它就会回到提交文件时的状态



#### 取消暂存的文件

git reset HEAD + 要移除的文件名称

git reset HEAD .  表示将暂存区的文件全部移出暂存区 



#### 移除文件

从Git仓库和工作区移除 文件

git rm -f + 文件名

仅从 Git 仓库移除文件 但会保留工作区的 文件

git rm --cached + 文件名



#### 忽略文件

可以创建一个名为 gitignore 的配置文件

1. 以 # 开头是注释
2. 以  / 结尾的是目录
3. 以 / 开头防止递归
4. 以 ！ 开头表示取反
5. 可以使用 glob 模式进行文件与文件夹的匹配（glob 表示简化了正则表达式）

| *.a           | 忽略所有 .a 的文件                                      |
| ------------- | ------------------------------------------------------- |
| !lib.a        | 跟踪所有 lib.a 的文件 即使 你在前面忽略了 .a 的文件     |
| /TODO         | 忽略当前目录下的TODO文件 但不忽略其他目录下的文件       |
| build/        | 忽略任何目录下名为 build 的文件                         |
| doc/*.txt     | 忽略doc/note.txt 文件 但不忽略 doc/server/arch.txt 文件 |
| doc/**/ *.pdf | 忽略 doc/ 目录下所有  .pdf 的文件                       |



#### 查看提交历史

git log

查看最近两条的提交历史

git log -2

在一行上面显示两条提交历史

git log -2 --pretty=onelin

在一行显示最近两条的提交历史 并自定义输出的格式

1. %h  提交的简写哈希值
2. %an  作者的名字
3. %ar 作者修订的日期
4. %s  显示提交说明

#### 回退到指定版本

1. 在一行展示所有提交历史

   git log --pretty=oneline

2. 所有 git reset --hard <CommitID>

   git reset --hard<CommitID>

#### 回到最新版

1. 在旧版中使用 git reflog --pretty=oneline 命令查看操作的历史

   git reflog --pretty=oneline

2. 再次根据最新提交的 ID 跳转到最新的版本

   git reset --hard <CommitId>



github 开源概念

GPL 

具有传染性的一种开源协议 不允许修改后的衍生代码作为闭源的商业软件

MIT 

目前限制最少的协议 唯一条件：在修改后的代码或者发行包，必须包含原作者的许可信息

远程仓库的两种访问许可

1. HTTPS 零配置；但是每次访问仓库时，需要输入Github 账号才能访问成功
2. SSH 额外配置； 但是配置成功后，每次访问仓库时，不需要输入 Github 账号和密码

#### Github 远程仓库生成 SSH key 密钥

ssh-keygen -t rsa -b a096 -C "注册Github邮箱"

ssh-keygen -t rsa -b a096 -C "3277981179@qq.com

敲击三次回车

配置 SSH key

1. 用记事本打开 id_rea.pub 文件 并复制文本内容（文件在C盘的用户名下的 .ssh 文件）
2. 在浏览器中登入Github 点击头像>Settings>SSH and GPG Keys>New SSH key
3. 将 id_res.pub 文件内的内容 粘贴到对应的文本框中
4. 在Title 文本框中任意填写一个名称 来标识这个 key 从何而来

#### 检测 SSH key 是否配置成功

ssh -T git@github.com



#### 将远程仓库的代码克隆到本地

git clone 远程仓库地址

#### 查看分列表

git branch

#### 创建分支

git branch 分支名称

创建了分支后 但是用户还是处于主分支

#### 切换分支

git checkout + 分支名

#### 快速的创建和切换分支

```git
#-b 表示创建了一个新分支

#checkout 表示切换到了刚才新建的分支上

git checkout -b 分支名称
```

#### 代码合并

先切换到主分支 再将分支的代码合并

1. 切换到 master 分支

   git branch master

2. 在 master 分支上运行 git merge 命令 将 login  分支的代码合并到 master 分支

   git merge login

#### 删除分支

git branch -d 分支名称

#### 将本地分支推送到远程仓库

-u 表示把本地分支和远程仓库进行关联 只在第一次推送时需要携带参数 -u

git push -u 远程仓库别名 本地仓库分支名称：远程分支名称

#### 创建远程分支

git push -u 远程仓库名称 本地分支：创建的远程仓库名称

实际案例

git push -u origin payment:pay

如果希望将远程分支的名称和本地分支名称保持一致 可以对命令进行简化

git push -u origin payment

#### 查看远程仓库所有的分支列表

git remote show 远程仓库名称

#### 跟踪分支

从远程仓库中，把对应的远程分支下载到本地仓库，并保持本地分支和远程分支名称相同

git checkout 远程分支名称



从远程仓库中，把对应的远程分支下载到本地仓库，并把下载的本地分支进行重命名

git checkout -b 本地分支名称 远程仓库名称/远程分支名称



#### 拉取远程仓库的最新代码下载到本地仓库

git pull   // 当前处在那个分支 执行这个命令就表明更新那个分支的代码

#### 删除远程仓库分支

git push 远程仓库的名称 --delete 远程仓库的分支