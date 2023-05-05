# GIT

### 概述

git是一个版本管理工具，它是用于管理对应的代码的版本的。它是一个集中式的代码管理工具（支持分布式）。相同的软件还有svn（集中式版本管理工具，它不具备分布式的功能）。

### svn及git的区别

![git和svn](C:\Users\29769\Desktop\文件\git和svn.png)

##### 了解git及svn的区别

### GIT环境搭建

[git官网地址](https://git-scm.com/)

- ##### 下载git

  ![image-20230316113655333](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316113655333.png)

  ![image-20230316113836297](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316113836297.png)

- ##### 安装git

  无脑安装

- ##### 测试（出现了对应 git gui（ui视图） 以及 git bash（指令））

  wind+r 进入 cmd

  ```shell
  git --version #查看版本
  ```

  ![image-20230316114634382](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316114634382.png)

  ![image-20230316114433536](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316114433536.png)

### git的分区

- 工作区 （代码书写）
- 暂存区 （暂存对应的文件）
- 版本库（历史区 记录所有的提交历史）

![img](https://img-blog.csdnimg.cn/img_convert/cc3510e8f32578ed0f39756e298749de.png)

### git的相关操作

#### 指令化操作

git bash 里面是对应的linux指令区，支持linux指令

###### 常见的linux指令

- cd 进入某个文件夹
- ls 查看当前的文件
- showdown  关机
- reboot 重启
- tar 解压
- vi 编辑器（编辑文件）
- rm 删除
- mv 移动
- clear 清空控制台
- ...

```shell
ls 
```

##### 创建本地仓库

```
git init
```

![image-20230316120150495](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316120150495.png)

创建一个隐藏的文件夹 .git文件夹（本地仓库）

![image-20230316120905325](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316120905325.png)

### 暂存区操作

#### 加入到暂存区

##### 存入文件到暂存区

```
git add 文件
```

![image-20230316141902810](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316141902810.png)

##### 查看状态

```
git status
```

![image-20230316142106115](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316142106115.png)

##### 添加文件夹（添加文件夹的下的所有的文件）

```
git add 文件夹路径
```

![image-20230316142331792](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316142331792.png)

##### 添加所有的文件

```
git add *
git add .
git add --all
```

![image-20230316142500104](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316142500104.png)

![image-20230316142729008](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316142729008.png)

#### 从暂存区撤回

- 不会影响工作区

```shell
git reset HEAD -- 文件名
git reset HEAD -- 文件夹名
git reset HEAD -- * #撤回所有
git reset HEAD -- . #撤回所有
```

![image-20230316144509290](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316144509290.png)

### 版本库操作

#### 从暂存区提交到版本库 (暂存区就没有了)

###### 如果是第一次进行提交操作需要设置对应的用户名及邮箱号

```shell
git config user.username 名字 --global
git config user.email 邮箱 --global
```

###### 提交指令进入vi编辑器

```shell
git commit 文件
git commit 文件夹
git commit *
git commit .
```

###### vim 编辑器模式

- 阅读模式 （进入就是阅读模式）
- 插入模式 （在阅读模式中 按下 a 或 i 或 o进入对应的插入模式  返回阅读模式按下esc键）
- 命令行模式 （通过阅读模式进入命令行模式 :wq (保存后退出)）

![image-20230316144839757](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316144839757.png)

![image-20230316145321009](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316145321009.png)

###### 提交指定对应的信息

```shell
git commit 文件 -m 信息
```

![image-20230316150459634](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316150459634.png)

#### 查看提交记录

```
git log
```

![image-20230316150039830](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316150039830.png)

#### 从版本库撤回

```shell
git reset --hard 版本号 
git reset --hard HEAD #撤回最新一次的提交
```

|                    | 是否影响工作区 | 是否影响暂存区 |
| ------------------ | -------------- | -------------- |
| --soft             | √              | ×              |
| --mixed （默认的） | ×              | √              |
| --hard             | √              | √              |

![image-20230316154605878](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316154605878.png)

### 分支

分支是对应的git的主要组成，git通过对应的分支操作来进行功能的合并和对应的冲突的解决。分支相当于将对应的功能进行拆分每个子功能单独开辟一个分支，这样就可以让俩个分支之间的耦合和冲突就减少了。

##### 分支的命名规范

git 分支分为集成分支、功能分支和修复分支，分别命名为 master、feature 和 fix，均为单数。不可使用 features、future、hotfixes、hotfixs 等错误名称。

- master（主分支，永远是可用的稳定版本，**不能直接在该分支上开发**）
- master_check（未上线前的开发分支，该分支只做只合并操作，不能直接在该分支上开发，前期开发完成后将feature分支合并到此分支）
- online（线上分支，由发版人员确认测试没问题后，将online_check分支合并到此分支）
- develop 开发主分支
- online_check（开发主分支，所有新功能以这个分支来创建自己的开发分支，该分支只做只合并操作，不能直接在该分支上开发）
- feature-xxx（功能开发分支，在develop上创建分支，以自己开发功能模块命名，功能测试正常后合并到develop分支，开发完成后合并到online_check分支上）

```text
feature/siliwu_querySchdule
```

- fix-xxx（修改bug分支，在master分支上创建，修复完成后合并到 online_check）

注意事项：

- 一个分支尽量开发一个功能模块，不要多个功能模块在一个分支上开发。
- feature 分支在申请合并之前，最好是先 pull 一下master_check分支下来，看一下有没有冲突，如果有就先解决冲突后再申请合并。

##### 分支的创建

```
git branch 分支名
```

##### 分支的查询（*表示当前分支）

```
git branch
```

![image-20230316160213435](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316160213435.png)

##### 分支的切换

```
git checkout 分支名
```

![image-20230316160319533](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316160319533.png)

##### 分支的删除（不能在当前分支内删除当前分支）

```
git branch -d 分支名
git branch -D 分支名
```

![image-20230316160549628](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316160549628.png)

##### 分支合并

会产生一个新的版本记录

###### 将对应的分支合并到当前分支

```
git merge 分支
```

![image-20230316161102410](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316161102410.png)

##### 衍合分支

```
git rebase 分支
```

![image-20230316161619385](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316161619385.png)

## Git EE

#### 概述：

git ee（码云 国内）是一个代码托管平台（远程仓库），它主要是用于托管对应的代码。与之相关的平台还有Git hub（国际）。

#### 主要代码托管

- gitEE 国内的代码托管
- gitHub 国际的代码托管（很多的框架的代码）
- 公司内部如果使用的是git进行对应的版本管理那么会使用**git lab**作为远程仓库（它是自己内部搭建的（私服））

#### gitEE仓库创建

- 注册、登录

  ![image-20230316171304291](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316171304291.png)

- 新建仓库

![image-20230316171503343](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316171503343.png)

![image-20230316171705580](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316171705580.png)

#### 第一种情况不设置对应的内容

拷贝对应的路径

在本地创建对应的git仓库 连接对应的远程仓库

```shell
git init
git remote add origin url #远程连接建立 第一次需要输入密码（一次）
#数据准备 本地仓库操作
git add .
git commit .
#推送到对应远程仓库
git push origin 分支名
```

![image-20230316174020655](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316174020655.png)

#### 第二种方法内容已经存在

拷贝路径

```shell
git clone url #克隆对应的内容
#本地仓库操作
git add .
git commit .
#推送到远程仓库
git push origin 分支名
```

### 相关指令

- git pull 拉取最新的数据 （默认会进行合并的操作）
- git fetch 拉取数据 （不会进行合并操作）
- git remote add origin url  建立连接
- git push  origin 分支名  推送到远程仓库
- git diff  比对对应的分支之间的差异
- git clone 克隆对应的远程仓库内容

### 对应的冲突解决

对应的俩个人在完成一个功能的时候 操作同一个分支中的内容，第一个版本号为0，a先提交 那么对应的远程仓库的版本就是1 如果b再进行提交它的版本是0 是小于远程仓库的版本的，这个时候就会产生冲突。需要人工介入。

##### 解决冲突的方式

先拉取最新的再进行对应的操作（是保留谁的内容）

git pull 会合并对应的内容

###### 使用命令行

```shell
git fetch origin master:hello
#再进行比对 出现差异
git diff hello
#人工干预
#再合并
git merge hello
```

###### 使用vscode来解决

![image-20230316180751446](C:\Users\29769\AppData\Roaming\Typora\typora-user-images\image-20230316180751446.png)

![img](https://www.likecs.com/default/index/img?u=L2RlZmF1bHQvaW5kZXgvaW1nP3U9YUhSMGNITTZMeTl3YVdGdWMyaGxiaTVqYjIwdmFXMWhaMlZ6THprNE9DOWlPREkwTWpNMVl6bGtNR1kzTXprNE5USmtZemN5WVRGbE5XVm1ZVEJtWXk1d2JtYz0=)