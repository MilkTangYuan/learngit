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

