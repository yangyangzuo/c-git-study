# SVN 迁移到Git



## 1.[git svn](https://git-scm.com/docs/git-svn) 

```bash
# 使用git svn clone 来克隆一个仓库
git svn clone svnURL -T trunk的目录  -b 分支目录  -t tags目录 --no-metadata --authors-file=路径/userinfo.txt  projectDir
#添加远程仓库 gitUrl是git 项目地址
git remote add origin gitUrl
#拉取远程git项目文件
git pull --rebase origin master
#将代码推送到远程
git push -u origin master


# 创建一个分支并追踪 一个已有的svn 转到git的分支

git branch 分支名 --track remotes/origin/分支名
git switch v1.0.1
#or 
git switch -c 分支名 --track remotes/origin/分支名
```



## #附

##### 1.userinfo.txt 是啥？

```bash
#userinfo.txt 保存着svn 用户到 Git 用户的映射 例如
schacon = Scott Chacon <schacon@geemail.com>
selse = Someo Nelse <selse@geemail.com>  #其中<> 和email可以省略
```

##### 2.获取svn 所有的用户

```bash
#获取svn提交记录中所有author  输出到userinfo.txt
svn log --xml | grep "^<author" | sort -u | awk -F '<author>' '{print $2}' | awk -F '</author>' '{print $1}' > userinfo.txt
```

