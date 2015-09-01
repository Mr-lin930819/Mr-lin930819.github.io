---
layout: page
title: Mr-Lin个人主页
tagline: (使用Jekyll Bootstrap)
---
{% include JB/setup %}

测试页面 [点此进入](https://mr-lin930819.github.io/test.html)

此测试页面的源代码如下：

	<!DOCTYPE html>
	<html>
	<body>

	<svg xmlns="http://www.w3.org/2000/svg" version="1.1" height="190">
	   <polygon points="100,10 40,180 190,60 10,60 160,180"
	   style="fill:red;stroke:blue;stroke-width:3;fill-rule:evenodd;" />
	</svg>
	 
	</body>
	</html>

阅读 [Jekyll Quick Start](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)

完整的使用以及有用的文档: [Jekyll Bootstrap](http://jekyllbootstrap.com)

## 更新作者信息

记得在 `_config.yml` 文件中指定你自己的个人数据:
    
    title : My Blog =)
    
    author :
      name : Name Lastname
      email : blah@email.test
      github : username
      twitter : username

主题将会在需要的时候用到这些变量属性.
    
## 文章发表例子

这个博客包含发布示例，可以帮助进行文章和博客数据的筹划。
当你不再需要这些示例了，可以将 `_posts/core-samples` 文件夹删除。

    $ rm -rf _posts/core-samples

下面是一个 "posts list"例子.

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## To-Do

这个主题还未完成. 如果你想加入我们成为一个贡献者, [请 fork](http://github.com/plusjade/jekyll-bootstrap)!
我们需要整理这个主题, 让其用法指南经特定主题标记出来.


