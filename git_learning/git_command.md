#<center>关于git的常用命令

###全局设置
1. `git config --global user.name xxx`:设置全局用户名，保存在./.gitconfig
2. `git config --global user.email xxx`
3. `git init`:将当前目录配置成git仓库，信息保存在.git文件夹中

###本地仓库常用命令
1. `git add xx`:将文件添加到暂存区
2. `git commit -m "备注"`:将暂存区的内容提交到当前分支
3. `git status`:查看当前仓库状态
4. `git log`:查看当前分支的所有版本
5. `git log pretty=oneline`
6. `git reflog`
7. `git rm --cached xx`:不管理这个文件
8. `git restore --staged xx`:将xx从暂存区内移除
9. `git restore xx`:将尚未加入暂存区的修改全部撤销
10. `git reset --hard 版本号`



###远程仓库关联
1. `git remote add origin xxx`：将本地仓库关联到远程仓库
   
###推送到远程仓库
1. `git push --set-upstream origin branch_name`:设置远程仓库分支对应本地分支
2. `git push -u`:第一次需要加参数u


###分支命令
1. `git branch`:查看分支
2. `git checkout -b branch_name`：创建分支，并指向分支
3. `git checkout branch_name`:指向某一分支
4. `git branch -d branch_name`:将本地某一分支删除

###远程仓库下载
1. `git clone ssh..`:从远程仓库下载到本地
2. `git pull --set-upstream-to=origin /branch1 branch2`:对应
3. `git pull origin branch`:将远程仓库与本地当前分支合并

###远程仓库删除
1. `git push -d branch`:删除远程仓库的某一分支
   