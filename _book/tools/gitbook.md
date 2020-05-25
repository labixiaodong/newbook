#  结合 GitHub Pages 使用 GitBook

### 0、gitbook可以做什么

使用gitbook结合github提供的pages功能，可以让你非常方便的搭建起自己的知识管理平台，你可以把你日常的读书笔记、工作总结、方法论、以及任何有被记录价值的信息，记录在上面。

然后，你可以随时随地通过网页来访问这些内容，因为人的精力都是有限的，学过一次的东西就不需要从头再来，gitbook可以极大地节省信息检索的时间，同时可以让自身有一个积累。

下面就来说一下这个神奇工具的使用方式：

### 1、安装node.js

gitbook是Node.js环境下，用于构建电子书的工具，所以要先安装Node.js。

下载链接：https://nodejs.org/en/

### 2、安装gitbook-cli

gitbook-cli 是gitbook的命令行工具，可在cmd中运行如下命令：

```
npm install -g gitbook-cli
```

执行下面命令，查看 `gitbook-cli` 的版本，以确定其是否成功安装。

```
$ gitbook -V
CLI version: 2.3.2
GitBook version: 3.2.3
```

### 3、生成github项目

登录github账号，点击New repository，创建项目 ;

添加项目名称和描述，然后创建项目 ;

并克隆到本地；

### 4、构建电子书

#### 4.1 进入上一步clone的github项目文件夹

#### 4.2 初始化电子书：

```
$ gitbook init
```

这时候会生成下面两个文件：

```
├── README.md
└── SUMMARY.md
```

#### 4.3 启动gitbook

```
$ gitbook serve
```

启动之后可打开浏览器，在[http://localhost:4000](http://localhost:4000/)，查看最终效果。

这一步会生成_book文件夹；

### 5、把本地项目推到github

```
git add .
git commit -m 'init' 
git push -u origin master
```

 `_book` 目录中包含静态电子书页面，执行下面命令，将 `_book` 目录推送到 GitHub 仓库的 `gh-pages` 分支，

便于他人访问；

```
$ git subtree push --prefix=_book origin gh-pages
```

GitHub Pages 是 GitHub 提供的静态网站托管服务。

GitHub 上的每个仓库都可以拥有一个 GitHub Pages，对应的 URL 如下：

```
https://<username>.github.io/<repository>/
```

其中，<username>是你的github用户名，<repository>是项目名称，打开URL即可访问推到线上的gitbook

### 6 更新gitbook

工具：markdown编辑器 [typora](https://typora.io/)

每次更新之后需要执行命令：

```
$ gitbook build
```

这一步是把更新的内容同步到_book文件夹中；

接着推到github:

```python
git add .
git commit -m 'aaa' 
git push
```

并推到gh-pages分支：

```
$ git subtree push --prefix=_book origin gh-pages
```

每次更新本地项目之后，重复以上几条命令即可使线上同步更新。



### 7 、配置gitbook

#### 7.1 导航栏伸缩

在根目录下（summary.md同级）创建文件：book.json

添加：

```
{
	"plugins": ["expandable-chapters"]
}
```





