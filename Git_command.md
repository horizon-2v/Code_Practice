# Git基本操作
## 1. 初始化操作
1. 第一步初始化操作 `git init` 
2. 配置Git的用户名和邮箱账号<br>
   ```git
   git config --global user.name "username"
   git config --global user.email "youemail@xx.com"
   ```
## 2. 添加到暂存区
添加操作通过`add`指令完成
```
git add <filename>
```
也可以用\*来表示所有文件
## 3. 提交到仓库
提交操作通过`commit`指令完成
```
git commit <filename> -m "your commit"
```   
## 4. 查看状态
通过`status`指令查看本地仓库的状态，即是否有修改后未提交的文件
```
git status
```
## 5. 查看文件修改内容
通过`diff`可以查看文件修改的具体内容
```
git diff <filename>
```
## 6. 查看每次提交的版本
通过`git log`可以查看每次提交的详细信息和commit
```
git log
```
## 7. 回退版本
回退版本有两种方式：<br>
1. 回退回前一个或前n个版本：<br>
   ```
   git reset --hard HAED^ 
   ```
   ^的数量表面要回退回之前的第n个版本，一个^回退回前一个，^^回退回前两个，依次类推。
   但要回退很多时，可以直接用：
   ```
   git reset --hard HEAD~n
   ```
   其中n为要回退的版本数
2. 回退回指定的版本号的版本：<br>
   回退回某一个版本号，因此可以做类似撤销一样的操作，例如：初始版本为1，更新到2后，想回退回版本1，但后续发现还是需要版本2，此时用上一种方法是无法回退回版本2的，于是可以通过指定版本号来回退
   ```
   git reset --hard <version>
   ```
   version为要回退的版本号。查询版本号的指令为:
   ```
   git reflog
   ```
## 8. 设置远程仓库
首先生成SSH Key, 在本地通过以下指令生成：<br>
```
ssh-keygen -t rsa –C “youremail@example.com”
```   
生成后在用户主目录下的.ssh目录中应该有id_rsa和id_rsa.pub两个文件，id_rsa.pub文件内为公钥，设置远程仓库的时候会用到。在GitHub中setting->SSH and GPG keys->New SSH Key，输入id_rsa.pub即可添加SSH Key，之后给repo命名后创建即可<br>
创建好远程repo后需要将本地的repo与远程的相连，输入:<br>
```
git remote add origin <repo url>
```
再把本地分支推送到远程
```
git push -u origin master
```
该指令将master分支推送到了远程repo，只有第一次提交的时候需要关联远程repo，所以添加了-u指令，之后推送的时候可以省略-u<br>
也可以先在GitHub中创建远程repo后直接clone到本地。
## 9. 分支管理
创建并切换分支：
```
git checkout -b <branch name>
```
-b参数表示创建并切换，相当于同时做了如下两条指令：
```
git branch <branch name>
git checkout <branch name>
```
查看当前的分支：
```
git branch
```
合并分支指令：
```
git merge <target brach>
```
该指令将目标分支合并到当前分支上<br>
删除分支指令：
```
git branch -d <branch name>
```
## 10. 其他
-  git fetch 和git pull的区别:<br>
   fetch是将远程仓库的代码拉到本地，但是不和本地的仓库合并，例如:
   ```
   git fetch origin master
   ```
   是将本地的`origin/master`这个分支更新了，但是`master`这个分支还是保持不变<br>
   如果需要和本地仓库合并，还需要merge指令：
   ```
   git merge origin/master
   ```
   pull则直接一步将本地的仓库更新到和远程仓库一致
   ```
   git pull origin master
   ```
   相当于做了fetch和merge的操作，但因为合并前不检查，方便但可能会不安全
-   相关链接：<br>
   [git 基本教程](https://zhuanlan.zhihu.com/p/30044692)<br>
   [github Token设置](https://zhuanlan.zhihu.com/p/401978754)<br>
   [Token 过期的处理](https://blog.csdn.net/weixin_51696091/article/details/123960933)