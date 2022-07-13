---
title: 寒江孤影，江湖故人，阁下安好！ 
---
# 欢迎来到子顾的流岚坞



本站使用*hexo*博客框架+github仓库快速搭建，下面是整个博客的搭建过程



下面介绍本人搭建博客的大致过程（环境为win10）（目前正在整理）



## 1、环境准备

- nodeJS环境和git环境

  nodeJS和git直接百度搜索下载，一键傻瓜式安装即可

安装好nodeJS之后可以在cmd命令行使用 *node -v* 查看node版本，如果有显示版本号即表示安装成功

git则使用命令 git --version 进行查看

- hexo框架安装

nodeJS安装好之后，已经附带安装好了npm(node package manager),然后使用下列命令安装hexo框架

- ```
  npm i hexo-cli -g
  ```

  

## 2、初始化博客

``` 
hexo init [blog-name]
```

其中中括号里面的内容为你自己的博客的名字

命令执行后会在当前的目录下生成一个[blog-name]的文件夹，进入文件夹并执行命令

```
cd [blog-name] #进入文件夹
npm i安装框架项目所需的依赖
```

安装过程出现缓慢的情况可以自行更换安装源，可以使用命令行命令更换，也可以使用更改配置文件的方式

- 更换安装源 可以使用临时更换

  ```
  npm i --registry https://registry.npm.taobao.org

- 可以对配置进行永久修改

  ```
  npm config set registery https://registry.npm.taobao.org

- 也可以暴力对配置文件进行修改，在__C:\Users\[userName]\.npmrc__文件中添加一行（如果已经存在registery则修改‘=’后面的值即可）

  ```
  registery=https://registry.npm.taobao.org/
  ```

- 安装之后，目录中会生成一个__node_modules__文件夹，这是博客项目的依赖

- 另外还有其他一些文件夹以及文件

  ```
  public：存放生成的页面
  scaffolds：生成文章的一些模板
  source：用来存放你的文章
  themes：主题
  _config.yml: 博客的配置文件
  ```

- 然后再在命令行依次执行以下命令：

  ```
  hexo g
  hexo s
  
  其中 
  
  - g：generate
  
  - s：server
  ```

​	然后就在本地部署了一个博客了，打开__localhost:4000__就可以看见博客的首页

## 3、创建gitHub账号，绑定邮箱，生成并添加ssh密钥

- 打开gitbash命令行界面（安装git之后右键菜单可打开，或者在开始菜单栏打开），输入以下命令

  ```
  ssh-keygen -t rsa -C "绑定的邮箱"
  ```

- 打开目录——__C:\Users\用户名\.ssh__

- 打开目录下文件“id_rsa.pub”复制所有内容（如果未发现该文件则先修改文件查看选项，勾选其中__隐藏的项目__）
- 登录到github
- 点击头像
- 打开settings栏目
- 在左边菜单栏内找到__SSH and GPG keys__
- 右边栏目的右上角出现按钮“new ssh keys”
- key的名字随便，将复制的内容粘贴到下面的key栏

## 4、创建github仓库

1. 在github找到主页右上角“+”,点击出现菜单，然后选择new Repository：

2. Repository name 中填入以下格式：

   ```
   你的用户名+'.hithub.io'
   
   如：你的用户名为 ’zhangsan‘ ==> 仓库名则为：'zhangsan.github.io'
   ```

   ==一定不要自己随便命名，不然部署博客会出现问题==

其它选项选填

## 5、部署 Hexo 到 gitHub



- 在创建的博客文件夹打开命令行输入以下命令安装 hexo-deployer-git：

  ```
  npm install hexo-deployer-git --save
  ```

- 然后修改博客配置文件_config.yml

  ```
  deploy:
    type: git
    repository: 	去github仓库复制你的仓库地址（github仓库找到code——》clone界面有三个选项，选择SSH复制地址到此处
    				或者自己拼写=》'git@github.com:用户名/用户名.github.io.git'
    branch: master =》 你的仓库主分支是什么分支就写什么
  ```

  修改完成后可以开始部署了：

  建议先按顺序执行

  - `hexo clean`

  - `hexo g` 

  - `hexo d`

    这样就将网站上传部署到了 GitHub Pages。

## 6、域名绑定和解析

- 当博客部署到了github之后，你就有了一个自己的博客的访问地址（用户名.github.io），但是这样对于一些有强迫症的同学来说还不太美观，于是我们可以自己申请一个域名让后绑定上去（当然你也可以不绑定）

- 注册之后，在控制台添加域名解析
  - 在解析页面添加CNAME解析记录，将域名解析指向自己的github地址
- 将github的地址与域名绑定，具体操作如下
  - 打开本地博客的source目录
  - 右键新建txt文件，并命名为“CNAME"注意去掉文件扩展名
  - 然后重新清除缓存并生成文件发布



博客的部署就到此为止了，欢迎下次光临
