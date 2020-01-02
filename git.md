# 1、git的全局配置
第一次安装完成git后，告诉git基本信息
随便找个目录，右键，找到Git Bash Here，输入下面的某条，查看配置信息
，退出配置信息界面直接输入q

```
$ git config -l 查看配置信息
$ git config --global -l 查看全局信息

```
进行配置：分别在xxx处输入自己的github的名字和邮箱

```
$ git config --global user.name 'xxx'
$ git config --global user.email 'xxx'
```
清屏：
```
$ clear
```
配置只需要一次，之后就不需要了
# 2、创建仓库
## 2.1、创建本地仓库
*windows* 下:先新建一个文件夹，在文件夹下右键，进入*Git Bash Here* 执行下面的指令。

*Mac或者linux或者win* 下，打开终端，然后进入自己建的文件夹下，执行下面的指令。

创建仓库命令：
```
$ git init
#会生成一个隐藏文件".git"（这个文件夹不能删，暂存区和历史区 还有些其他的信息都在这个文件夹下，删了就不是一个完整的git仓库
```
##  2.2、在本地编写代码（工作区），并提交到暂存区
在刚才建立的文件夹下，新建一些文件，然后右键git
输入命令
```
$ git status 查看当前状态

会显示以下信息：
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        git.md（这里显示的是我新建的一个.md文件）

nothing added to commit but untracked files present (use "git add" to track)

```
如果显示的信息中，
- 自己建立的文件是红色的，表示这些红色的文件都是在工作区，未进入缓存区；
- 如果是绿色的，表明文件在暂存，还没有到历史区；
- 看不见东西则所有修改信息已经到历史区（working tree clear）。
```
$ git add XXX 把某个文件或者文件夹提交到暂存区
$ git add . 把当前仓库中所有最新修改的文件都提交到暂存区
$ git add -A 同上（提交所有）
```
如果想删除提交到缓存区的文件，执行：
```
$ git rm --cached xxx
```

将暂存区的内容提交到历史区
```
$ git commit -m'描述信息：本次提交内容的一个描述'
#注意：-m后面不加空格
提交完成之后显示：
[master (root-commit) 8d142ed] 第一次上传git.md
 1 file changed, 38 insertions(+)
 create mode 100644 git.md
 
其中8d142ed是历史版本号
```
查看历史记录：
```
$ git log #查看提交记录
$ git reflog #查看所有历史记录（包括历史区回滚后）
```
*从工作区提交到暂存区，从暂存区提交到历史区，这个过程其实都是复制一份内容，每个区域中都有这些信息，所以在更改内容的时候可以对比出修改了那些*

从历史区回滚到之前版本：
```
$ git reset --hard xxx
xxx是版本号（前七位或者全部）
```
# 3、 远程仓库
## 3.1、 github
### 3.1.1 settings
- Profile 基本信息
- Account 账户：username注册时用的那个，最好别改，变的太多了
- Security 安全隐私：改变密码啥的
- Emails 修改增加邮箱，需要校验
- ...
### 3.1.2 创建仓库
头像旁边有个加号
new repository

*起个名字，然后进行描述，Public是所有人都可看到的，Private私有的（能不能看由owner定，之前收费现在也免费了）*
*可选择初始仓库的时候是否包含readme文件*

填完信息选*create repository*

对仓库进行操作（在仓库中有个settings）

- 删除仓库：settings -> options里面有各种管理选项，选择delete this repository
- Collaborators：设置协作开发者（指定可操作此仓库的人）（直接输入github账号，add collaborator就可）
- code ：可查看查看历史版本信息和分支信息（commit信息）

## 3.2 本地仓库与远程仓库信息同步
### 3.2.1 本地仓库关联远程仓库
```
#建立本地仓库与远程仓库的链接
$ git remote -v #查看当前链接情况
$ git remote add origin [Git 仓库地址] #Git仓库地址，是在github上创建仓库之后的ssh地址，或者是git地址，origin是随便起的一个名字，只不过一般都叫这个名字，写的时候不加[]

$ git remote rm origin  #取消关联
```
### 3.2.2 本地仓库上传文件到远程
```
# 提交之前最好先拉取，origin是之前自己取的名
$ git pull origin master

# 把本地代码提交到远程仓（需要输入github的用户名密码）
$ git push origin master

```
如果没有权限无法拉取，则需要进行key的配置：
https://blog.csdn.net/weixin_44394753/article/details/91410463

如果在pull的时候出现如下错误：(https://www.cnblogs.com/yiduobaozhiblog1/p/9125465.html)

```
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
#先检查一下key是否添加，然后由于在github上初始化库的时候有readme文件存在，需要先pull一下

$ git pull --rebase origin master
#pull=fetch+merge

然后再
$ git push --set-upstream origin master
```

