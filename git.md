gitflow
master分支推送了新建分支之后的代码，需要重设master分支
git reset --hard HEAD^（回退一个版本可以用reset）
git push origin -f master （强制推送，需要看仓库是否支持）


什么时候使用 rebase/merge
假设场景：从dev拉出分支feature-a。那么当dev要合并feature-a的内容时，使用git merge feature-a；
反过来当feature-a要更新dev的内容时，使用git rebase dev。
使用时主要看两个分支的"主副"关系。

注意
一般来说，rebase后的dev和远程的origin/dev会发生分离，在命令行界面中会提示：
Your branch and 'origin/dev' have diverged,
and have 1 and 1 different commits each, respectively.
(use "git pull" to merge the remote branch into yours)
这时需要用git push -f强制推送，覆盖远程分支。若使用了提示中的git pull，结果会变成合并，并产生一个合并提交点。

慎用git push -f!
