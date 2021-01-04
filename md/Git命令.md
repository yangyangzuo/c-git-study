## 1.[git config](https://git-scm.com/docs/git-config) 

```bash
#git config 常用options
     #配置项放到哪个文件
	--local   -----当前仓库（默认）
	--global  ----当前用户可用 
	--system  ----系统范围可用 在git安装目录/etc/gitconfig
	
    #设置配置项
    git config --global user.name "李四"
    #查看某一配置项
    git config --global user.name
    #or 
    git config --global --get user.name
    #查看所有有的配置项
   	git config --global --list
    # 移除配置项
    git config --global --unset user.name
  
```

## 2.[git clone](https://git-scm.com/docs/git-clone)

```bash
#git clone <repository> <directory>  克隆某个远程项目到本地  本地目录名称为gitdemo1
    git clone http://192.168.31.136:801/demogroup/gitdemo.git   gitdemo1
    #制定clone 某个分支 切HEAD指向这个分支 例dev
    git clone -b dev http://192.168.31.136:801/demogroup/gitdemo.git
```

## 3.[git branch](https://git-scm.com/docs/git-branch)

```bash
#git branch 查看，创建，删除分支
 git branch    #列出已有的分支
 git branch --list 'maint-*'  #列出满足条件的分支
 git branch branchName  # 创建分支 branchName
 git branch -d branchName  # 删除分支 branchName
 git branch -r -d branchName  # 删除远程分支 branchName
 git branch -m oldName  newNmae #修改分支名称
```

## 4.[git checkout](https://git-scm.com/docs/git-checkout)

```bash
#git checkout 切换分支或还原工作树文件
git checkout  branchName  #切换到branchName分支
git checkout -b branchName  #创建branchName分支并切换
git checkout -- index.js   #从索引树中还原index.js
git checkout -- "*.js"  #从索引树中还原.js
```

## 5.[git switch](https://git-scm.com/docs/git-switch)

```bash
#git switch  切换分支  2.27.0版本添加
git switch  branchName  #切换到branchName分支
git switch -c branchName  #创建branchName分支并切换
```



## 6.[git  status](https://git-scm.com/docs/git-status)

```bash
#git status 查看工作区，暂存区文件的状态
 -s or --short # 输出简短的信息
```

## 7.[git add](https://git-scm.com/docs/git-add)

```bash
#git add 开始追踪选择的文件，并将其添加到暂存区
    git add . #添加所有文件
    git add src  #添加指定的文件夹 例src
    git add src/index.js src/index1.js  #添加指定文件
    git add src/index*.js #利用*来匹配添加
    
    git add -i #有选择性的添加
```

## 8.[git commit](https://git-scm.com/docs/git-commit)

```bash
#git commit 将暂存区的文件提交到仓库
     -m or --message "msg" # 本次提交的文件主要改了什么，要做一个描述信息 
     --allow-empty-message #如果不使用 -m  则需要使用这个
     --no-verify  #会绕过 pre-commit and commit-msg hooks 不推荐使用
     --amend  #用来修改最后一次提交
```

## 9.[git pull](https://git-scm.com/docs/git-pull)

```bash
#git pull 从一个远程仓库或本地分支拉取并合并到当前分支  相当于 git fetch 和 git merge 的结合
 git pull origin master 
```

## 10.[git push](https://git-scm.com/docs/git-push)

```bash
#git push 将本地分支的提交推送到远程
git push origin master
```

## 11.[git merge](https://git-scm.com/docs/git-merge)

```bash
#git merge 将一个或者多个分支合并到当前分支
git merge master  #如果有冲突  则会有  CONFLICT (content): Merge conflict in 的提示  

--ff    # 尽可能 将合并作为 fast-forward进行， 如果不行则创建合并提交 ff 表示  fast-forward
--no-ff # 所有情况下都可以创建合并提交
--ff-only # 如果不能将合并作为 fast-forward 则拒绝合并，并退出
--no-commit  #只合并，不创建合并提交
--squash  # 压缩提交记录
```

## 12 [git fetch](https://git-scm.com/docs/git-fetch)

```bash
#git fetch 将远程仓库中的内容更新到本地
git fetch origin master
```

## 13.[git stash](https://git-scm.com/docs/git-stash)

```bash
#git stash  储藏工作区和暂存区的更改  默认只会储藏已经在索引中的文件

git stash push [--include-untracked / -u] [name] #添加名称为name 的储藏
git stash list #显示已有的储藏
git stash apply [name] # 恢复对应的储藏
git stash drop [name] #删除
git stash pop  #相当于apply 加 drop

```

## 14 [git rm](https://git-scm.com/docs/git-reset)

```bash
#git rm  用于删除单个文件或文件集合 
git rm  file  #删除 文件 git reset HEAD  git checkout .
git rm --cached file #删除暂存区的文件 工作区的文件不变
```



## 15 [git restore](https://git-scm.com/docs/git-restore#_name)

```bash
#git restore 恢复工作区文件
git restore [--worktree]  file # 默认 还原工作区的修改
git restore --staged file #表示从暂存区删除文件，但工作区文件内容保持不变
git restore --source  #通过--source 可以指定 commitid 分支 或tag
```

## 16 [git reset](https://git-scm.com/docs/git-reset)

```bash
#git reset 重置到指定的commit 或HEAD
git reset [--soft | --mixed | --hard] [HEAD]
--mixed #为默认，可以不用带该参数，用于重置暂存区的文件与上一次的提交(commit)保持一致，工作区文件内容保持不变。
--soft #参数用于回退到某个版本
--hard #参数撤销工作区中所有未提交的修改内容，将暂存区与工作区都回到上一次版本，并删除之前的所有信息提交：
```

## 17 [git revert](https://www.git-scm.com/docs/git-revert)

```bash
#git revert 撤销 某次操作，此次操作之前和之后的commit和history都会保留

git rever [commit | HEAD]
```

## 18 [git log](https://www.git-scm.com/docs/git-log)

```bash
#git log 显示提交日志
--pretty=[format] #  取值有 oneline, short, medium, full, fuller, reference, email, raw
--abbrev-commit  #仅显示一部分 sha-1值     可用--abbrev = <n>指定
--oneline  #相当于 --pretty=oneline --abbrev-commit

--stat  # 输出文件增删改的统计数据
-p  #修改的内容 用diff的形式显示
```



## 19 [git reflog](https://www.git-scm.com/docs/git-reflog)

```bash
#git reflog 用来查看所有分支的所有操作记录，包括commit和reset的操作，也包括已经被删除的commit记录
git reflog
```



## 20 [git diff](https://www.git-scm.com/docs/git-diff)

```bash
#git diff 比较差异
git diff 
git diff [--cached | --staged]  
git diff  branch1 branch 2
git diff file

--name-only #仅显示已更改文件的名称
--stat  #显示统计数据
```

## 21 [git mv](https://git-scm.com/docs/git-mv) 

```bash
#git mv 移动或重命名文件，目录 删除原文件或目录并创建一个新的文件或目录 添加到暂存区
git mv  filename   filename1
```

## 22 [git tag](https://git-scm.com/docs/git-tag) 

```bash
#git tag 创建，列出，删除 标签
git tag #查看本地所有tag
git tag tagName #创建tag
git push origin tagName #推送到远程
git tag -d tagName #删除本地tag
git push origin tagName #推送到远程删除
```

## 23 [git rebase](https://git-scm.com/docs/git-rebase)

```bash
#git rebase 变基
git rebase branch   # 
git rebase -i  #将多个提交记录合并
                #pick：保留该commit（缩写:p）
                #reword：保留该commit，但我需要修改该commit的注释（缩写:r）
                #edit：保留该commit, 但我要停下来修改该提交(不仅仅修改注释)（缩写:e）
                #squash：将该commit和前一个commit合并（缩写:s）
                #fixup：将该commit和前一个commit合并，但我不要保留该提交的注释信息（缩写:f）
                #exec：执行shell命令（缩写:x）
                #drop：我要丢弃该commit（缩写:d）
```

## 24 [git cherry-pick](https://git-scm.com/docs/git-cherry-pick)

```bash
#git cherry-pick  #将指定的提交（commit）应用于其他分支
git cherry-pick commit1
```

