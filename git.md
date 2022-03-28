gitflow
master分支推送了新建分支之后的代码，需要重设master分支
git reset --hard HEAD^（回退一个版本可以用reset）
git push origin -f master （强制推送，需要看仓库是否支持）

