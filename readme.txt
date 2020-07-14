Git is a distributed version control system.
Git is a free software distributed under the GPL.
Git has a mutable index called stage.
Git tracks changes of files.


Bug 修复
假设 有master 主分支，当前工作在dev 分支，主分支有个 101号bug需要修复

1、将当前改动暂存
git stash

2、切换到需要在那个分支修复
git switch master #在主分支修复

3、创建一个新分支，用于解决当bug
git switch -c issue101

4、解决bug 并提交

5、修复完成切换到分支并合并
git switch master
git merge --no-ff -m "fix issue101" issue101

6、删除修复bug工作分支
git branch -d issue101

// 修复完成
7、切换回当前工作分区
git switch dev

8、将bug修改应用到当前分支
git cherry-pick <commit>
<commit> 为修复bug时所做的提交

9、弹出工作区缓存,继续工作
    git stash pop
或
    git stash  list
    git stash apply stash@{0}
    git stash drop

小结
查看远程库信息，使用git remote -v；

本地新建的分支如果不推送到远程，对其他人就是不可见的；

从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交；

在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；

建立本地分支和远程分支的关联，使用git branch --set-upstream branch-name origin/branch-name；

从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。


查看远程库信息:
git remote 
git remote -v 显示更详细的信息


从远程克隆分支到本地
git clone  git@github.com:MilkTangYuan/learngit.git  
默认情况下只能看到本地的master 
如果想要在dev 分支上开发，就必须创建远程origin的dev分支到本地，于是他用这个命令创建本地dev分支
git checkout -b dev origin/dev

