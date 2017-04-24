title: Git 差异比较
date: 2015-11-17 14:31:16
categories: git
tags:
  - git
  - diff
---

git diff <file>     # 比较当前文件和暂存区文件差异
git diff
git diff <$id1> <$id2>      # 比较两次提交之间的差异
git diff <branch1>..<branch2>   # 在两个分支之间比较 
git diff --staged   # 比较暂存区和版本库差异
git diff --cached   # 比较暂存区和版本库差异
git diff --stat     # 仅仅比较统计信息

git diff --cached >XXX.patch     ???

git diff –cached 查看差异 

git diff commit1 commit2 比较两次提交所有文件的变好
git diff commit1:filepath commit2:filepath   比较某次提交的某个文件的对比


git diff localBranch..origin/temoteBranch (比较本地分支和远程分支的差异)
如：git diff dev..origin/dev


	git diff : 查看文件变动情况(diff -- difference)

	---------------------------   使用git须知    ----------------------------------------------------------------
使用 Git 的一些基本守则： 当要commit/提交patch时：

	* 使用 git diff --check 检查行尾有没有多余的空白
	* 每个 commit 只改一件事情。如果一个文档有多个变更，使用 git add --patch 只选择文档中的部分变更进入 stage
	* 写清楚 commit message



查看合并的冲突：git diff --merge

git diff 显示与上次提交版本文件的不同（对比）

git diff                # 查看已暂存与未暂存的差异
git diff --cached       # 查看已暂存与最近提交的差异

git diff对比的客户端工具(git gui)

git diff <commitID> <file>  查看指定CommitID与当前工作区改变的比较
git diff <CommitID> <CommitID> 查看两次提交的比较
git diff --cached <commitID> <file>  查看指定CommitID与暂存区改变的比较

