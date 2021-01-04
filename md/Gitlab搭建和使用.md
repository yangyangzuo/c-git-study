### Gitlab搭建

#### 	1.[安装地址](https://www.baidu.com/link?url=aZM2Rec8yGmYP6nGkSJ2efx2Vhi7KVLeIfyUxn_uBQrmfB7mUorjHjfJJQQmboqf&wd=&eqid=dbe571f60023d089000000035fcb32)

####      2.docker 安装

​		在window中安装docker的要求

​        ![](.\image\system require.png)

​         docker 安装成功后

在C:\Users\用户名\\.docker\daemon.json 的registry-mirrors加入国内镜像源

```json
    "https://9cpn8tt6.mirror.aliyuncs.com",
    "https://registry.docker-cn.com",
    "http://hub-mirror.c.163.com",
    "https://docker.mirrors.ustc.edu.cn"
```

下载安装gitlab

```bash
docker pull gitlab/gitlab-ce
```

安装成功后在801端口运行

```bash
docker run -d -it -p 4431:443 -p 801:80 -p 2221:22  docker.io/gitlab/gitlab-ce
```

​    在浏览器  http://ip:801打开

### gitlab的使用

######         1. 修改密码，修改密码之后进行登录 

######        2.    可在设置中修改语言

![](.\image\language.png)

###### 3.添加ssh秘钥

```bash
#在git-bash中运行下面的命令 获取ssh秘钥
ssh-keygen -o -t rsa -b 4096 -C "注册的邮箱地址"
```



###### 4.项目目录，显示已参与的项目

![](.\image\project.png)

###### 5.群组 可以新建群组

​	![](.\image\group.png)

​	

###### 6..控制面板，可以在控制面中查看项目的相关情况和可以在成员中创建新用户

![](.\image\panl.png)

###### 7.为群组或项目添加成员

![](.\image\user.png)

###### 8.合并请求  点击新建

![](.\image\mergeRequest.png)

![](E:\git\markdown\image\newMergeR.png)



![](.\image\newMergeRequest1.png)

###### 9.合并请求的审核

​	合并请求的入口在页面的右上方![](.\image\审核入口.png)

  点击之后进入待审核列表			![](.\image\待审核list.png)

​    审核页面，可以查看所有提交的更改

![](.\image\审核.png)

### Gitlab的权限问题

1. ###### Gitlab用户在组中有五种权限：

   Guest、Reporter、Developer、Master、Owner

   - Guest：可以创建issue、发表评论，不能读写版本库
   - Reporter：可以克隆代码，不能提交，QA、PM可以赋予这个权限
   - Developer：可以克隆代码、开发、提交、push，RD可以赋予这个权限
   - Master：可以创建项目、添加tag、保护分支、添加项目成员、编辑项目，核心RD负责人可以赋予这个权限
   - Owner：可以设置项目访问权限 - Visibility Level、删除项目、迁移项目、管理组成员，开发组leader可以赋予这个权限

2. ###### Gitlab中的组和项目有三种访问权限：Private、Internal、Public

   - Private：只有组成员才能看到
   - Internal：只要登录的用户就能看到
   - Public：所有人都能看到

### Gitlab 的问题解决

#####   git clone 地址为一串字符的问题

1. 打开cli 工具

   ![](.\image\docker-cli.png)

2. 输入 vim  /opt/gitlab/embedded/cookbooks/gitlab/templates/default/gitlab.yml.erb

   修改gitlab.yml.erb文件的gitlab > host和port

   ![](.\image\ip.png)

   vim    i ->可进入编辑模式    esc->推出编辑模式     :wq->保存退出       进行docker 重启

##### 项目分支保护问题

​		可在项目仓库中修改![](.\image\branch-protect.png)或者在项目设置中修改

![](E:\git\markdown\image\setting.png)