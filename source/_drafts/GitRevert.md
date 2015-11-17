title: "GitRevert"
date: 2015-11-17 15:11:41
categories: git
tags:
  - git
  - revert
---


   git revert <$id>    # 恢复某次提交的状态，恢复动作本身也创建了一次提交对象
git revert HEAD     # 恢复最后一次提交的状态


重置一个提交（通过创建一个截然不同的新提交）
$ git revert <commit>

git revert：还原一个版本的修改，必须提供一个具体的Git版本号

git revert和git reset的区别

