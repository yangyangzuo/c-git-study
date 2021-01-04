# Pull Request  拉取请求（以gitlab为主）

## 1.从主项目中将代码fork（派生）到自己的账号下  这样你就拥有一个和原来仓库一样的内容

![](E:\git\markdown\image\pr-fork.png)

## 2. clone 到本地

```bash
git clone  giturl
```



## 3.设置与原仓库的代码同步

```bash
# 添加原仓库的地址
git remote add 别名 源仓库url

#同步代码
git pull 别名  分支名[master] # 可以加 --rebase 处理可能的冲突
```



## 4. 进行代码开发，并提交到远程

## 5. 在gitlab中创建合并请求

- #####     在项目中找到合并请求 并点击进去

![](E:\git\markdown\image\createpr.png)

- #####   点击新建合并请求

![](E:\git\markdown\image\createpr2.png)

- ##### 进入合并请求填写界面

  ![](E:\git\markdown\image\cratepr3.png)

- ##### 点击submit 合并请求 并通知你选择的审核人对你的代码进行审核合并，如何你提交的代码与源项目中的代码存在冲突，会有这样的提示

   ![](E:\git\markdown\image\prConliect.png)

​     且这个代码在审核人员那里也无法进行合并  

​		![](E:\git\markdown\image\conclient.png)

