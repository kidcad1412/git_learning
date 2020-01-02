# 1、git的全局配置
第一次安装完成git后，告诉git基本信息
随便找个目录，右键，找到Git Bash Here，输入下面的某条，查看配置信息，退出配置信息界面直接输入q

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
## 2.2  在本地编写代码（工作区），并提交到暂存区
```
$ git add XXX 把某个文件或者文件夹提交到暂存区
$ git add . 把当前仓库中所有最新修改的文件都提交到暂存区
$ git add -A 同上（提交所有）
```

