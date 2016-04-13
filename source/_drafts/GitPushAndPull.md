title: "GitPushAndPull"
date: 2015-11-17 14:31:16
categories: git
tags:
  - git
  - push
  - pull
---

git push orign HEAD --force  

git push #推送本地所有分支
git push <-u | --set-upstream> origin dev  # 推送当前分支到远程dev分支，且设置当前分支为远程跟踪的分支

# 以下配置是针对git push、git pull设置
git config --global push.default matching 	# 推送本地所有存在跟踪(关联)的所有分支到对应远程分支
git config --global push.default simple 	# 推送当前分支到其远程跟踪分支
git push --all origin 	# 推送本地所有分支到远程对应(相同分支名)分支
git push <[-f|--force]> origin   # 强制推送到远程(远程的更新会被覆盖)


git push origin source

 将本地托管代码库push到Git服务器： git push -u origin master ( 即就是：git push -u [remote name] [local branch : remote branch] )

 git  push  origin  master
 上面两句代码等价于：git  push  git@github.com:verphen/test.git  master（push本地默认分支master到服务器master分支）
 通式：git  push   remoteURL  [ localBranch ] :  remoteBranch
       git push -u origin master (-u 指定默认主机)


git push -f 强制推送本地的替换服务端


# 推送本地仓库的指定分支到远程仓库的指定分支
git push <remote_name> <local_branch>:<remote_branch> 
# 删除远程仓库的指定分支
git push <remote_name> :<remote_branch>
# 推送本地仓库的指定分支到远程仓库，并初始化远程仓库的默认分支
git push -u <remote_name> <local_name>


强制提交线上： git push -u origin master -f

git push -u : http://www.yiibai.com/git/git_push.html
修改远程仓库
$ git remote set-url --push [name] [newUrl]


不要忘记使用git push --tags将tags推送到远端











取得一个发布的新特性分支:取得其它用户发布的新特性分支。
git flow feature pull origin MYFEATURE

git fetch <remote_name>                     # 从远程仓库抓取更新
git fetch <remote_name> <branch_name>       # 从远程仓库的指定分支拉取更新

# 拉取远程仓库的指定分支，并合并本地仓库的指定分支
git pull <remote_name> <remote_branch>:<local_branch>
# 拉取远程仓库的所有分支，不合并到本地仓库的指定分支
git pull --no-ff


git pull --rebase 

     git pull      #抓取远程所有分支快速合并到本地

     git pull --no-ff   # 抓取远程所有分支合并到本地，不使用快速合并

     git pull [remote name] [remote branch] [local branch] （相当于执行git fetch和git merge）


                    1、git fetch需要先下载远程更新，然后在合并（不是自动提交，建议采用：先下载更新，我们看是否需要合并，更安全）
                  git fetch [remote name]  [remote branch]:[local branch1] （下载远程代码）


git pull 使用-rebase

