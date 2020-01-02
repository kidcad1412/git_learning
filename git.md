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