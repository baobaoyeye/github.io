cherry-pick相关技巧
==================

Q1:
--- 

* 在本地 b1 分支上做了一个commit {X0}，把其放到本地b2分支

A1:
---

* 基础命令

```shell
$ git cherry-pick <commit id>
```

```shell
$ git checkout b2
$ git cherry-pick {X0}     # 这个 {X0} 号码，位于：

$ git log 
commit {X0}
Author: Somebody <example@a.b>
Date: sometime
```

1. 如果顺利，就会正常提交。结果：

```shell
Finished one cherry-pick.
# On branch b2
# Your branch is ahead of 'origin/b2' by {x0} commits.
```

2. 如果在cherry-pick 的过程中出现了冲突

```shell
Automatic cherry-pick failed.  After resolving the conflicts,
mark the corrected paths with 'git add <paths>' or 'git rm <paths>'
and commit the result with: 

        git commit -c {X1}
```

3. 手工解决冲突

```shell
$ git status    # 看哪些文件出现冲突

both modified:      dir/foo.c 

$ vim dir/foo.c  # 手动解决它。 
$ git add dir/foo.c
$ git commit -c {X1}
```