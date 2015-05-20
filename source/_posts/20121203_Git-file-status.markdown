---
title: Git库文件状态
date: 2012-12-03 11:00:34
categories: tools
tags: [git,版本管理,工具]
---
git库所在的文件夹(即.git所在的文件夹)中的文件的状态：

-  untracked：未跟踪，此文件在文件夹中，但并没有加入git库，不参与版本控制。 通过”git add”,”git commit”可将它置入跟踪库。

- unmodify：文件已经库中，未对文件未修改，即版本库中的文件快照内容与文件夹中文件内容完全一致。这种类型的文件有两个去处，如果它被修改，而成为modified。如果使用”git rm”移出版本库，则成为untracked文件。

-  modified：文件已修改，仅仅是修改，并没有进行其它操作。这个文件也有两个去处，通过”git add”可进入暂存(staged)状态，使用"git checkout"则丢弃修改，返因到unmodify状态。这个checkout很好理解，就是取出库中文件，覆盖当前文件。

-  staged：暂存状态。执得"gitcommit"则将修改同步到库中，这时库中的文件与本地文件又一致了，于是文件是unmodify状态。执行”git reset HEAD filenam”取消暂存，文件状态变为modified.