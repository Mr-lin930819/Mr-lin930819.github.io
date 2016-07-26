# Mr-lin930819.github.io/github_page_generator
##简介
该分支为Mr-lin930819.github.io master分支的源项目，在分支中运行：

    hexo deploy
可以将生成的静态页面发布到master分支上，通过访问 http://Mr-lin930819.github.io 即可访问主页面了

##使用的框架
  项目使用Hexo作为静态博客页面生成框架，而主题则使用litten的yilia这款简洁主题。
  
  yilia主题的github页面：[litten/hexo-theme-yilia](https://github.com/litten/hexo-theme-yilia)
##Hexo常见使用命令
    hexo new "postName"        新建文章
    hexo new page"pageName"   新建页面
    hexo generate             生成静态页面至public目录
    hexo deploy               将.deploy目录部署到GitHub
    hexo server               开启预览访问端口（默认端口4000）

##Hexo在Ubuntu的安装
1.在Node.js官网下载安装包

[Node.js](https://nodejs.org/en/)

2.下载并解压 node, 解压后文件夹移到通用的软件安装目录 /opt/ 
	sudo mv node-v4.x.x-linux-x64 /opt/

3.安装 npm 和 node 命令到系统命令 
	sudo ln -s /opt/node-v4.x.X-linux-x64/bin/node /usr/local/bin/node
	sudo ln -s /opt/node-v4.x.x-linux-x64/bin/npm /usr/local/bin/npm

4.安装成功后，使用npm淘宝源
	npm install -g cnpm --registry=https://registry.npm.taobao.org

[淘宝npm镜像](https://npm.taobao.org/)

5.转到博客根目录，输入下面命令安装Hexo
	sudo cnpm install -g hexo
###Hexo的安装参考文章
[HEXO+Github,搭建属于自己的博客](http://www.jianshu.com/p/465830080ea9)

[Ubuntu 16.04 64位 搭建 node.js NodeJS 环境](http://blog.csdn.net/caib1109/article/details/51804687)

