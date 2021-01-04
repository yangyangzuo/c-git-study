## Git的一些基本概念

####  1.Git工程中的四个区域

 工作区（Working Directory）

暂存区/索引 （Stage/Index）

本地仓库 （Repository）

远程仓库  （Remote）

![267f9e2f0708283880b630e1a2d22e054d08f158.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/455647/1608039562181-61e3c629-87ad-44f5-9a3e-888f7bf5a299.jpeg)

#### 2.Git 文件的状态

已提交（committed），已修改（modified）和已暂存（staged） 未追踪（untracked）

![1283669-20190801113109820-164609398.png](https://cdn.nlark.com/yuque/0/2020/png/455647/1608040154098-36e614ee-00e2-4dfc-872f-cb605b1df1ad.png)

#### 3[.引用](https://git-scm.com/book/zh/v2/Git-%E5%86%85%E9%83%A8%E5%8E%9F%E7%90%86-Git-%E5%BC%95%E7%94%A8)

​    引用：其实就是一个保存commit sha-1值的文件 ,而该文件有一个简单的名字， 然后用这个名字指针来替代原始的 SHA-1 值的话会更加简单.这种简单的名字被称为“引用（references，或简写为 refs）”。 你可以在 `.git/refs` 目录下找到这类含有 SHA-1 值的文件。

引用又分为：分支引用，HEAD引用 ，tag引用，远程分支引用

- 分支引用

   在.git\refs\heads文件夹下。保存当前所有分支    文件中存储的就是对应commit提交的sha-1值

  ```bash
  $ cat .git/refs/heads/master
  049ac6b72cb826caf999f51e2ea0cd27f816dd7b
  ```

- HEAD引用

   HEAD引用是一种特殊的引用，通常情况下它指向一个分支 如：

  ```bash
  $ cat .git/HEAD
  ref: refs/heads/master
  ```

- Tag引用

    它像是一个永不移动的分支引用——永远指向同一个提交对象，只不过给这个提交对象加上一个更友好的名字罢了

- 远程引用

   如果你添加了一个远程版本库并对其执行过推送操作，Git 会记录下最近一次推送操作时每一个分支所对应的值，并保存在 refs/remotes 目录下

   远程引用和分支（位于 refs/heads 目录下的引用）之间最主要的区别在于，远程引用是只读的。 虽然可以 git checkout 到某个远程引用，但是 Git 并不会将     HEAD 引用指向该远程引用。因此，你永远不能通过 commit 命令来更新远程引用