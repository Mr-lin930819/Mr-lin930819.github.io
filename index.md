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

Read [Jekyll Quick Start](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)

Complete usage and documentation available at: [Jekyll Bootstrap](http://jekyllbootstrap.com)

## Update Author Attributes

In `_config.yml` remember to specify your own data:
    
    title : My Blog =)
    
    author :
      name : Name Lastname
      email : blah@email.test
      github : username
      twitter : username

The theme should reference these variables whenever needed.
    
## Sample Posts

This blog contains sample posts which help stage pages and blog data.
When you don't need the samples anymore just delete the `_posts/core-samples` folder.

    $ rm -rf _posts/core-samples

Here's a sample "posts list".

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## To-Do

This theme is still unfinished. If you'd like to be added as a contributor, [please fork](http://github.com/plusjade/jekyll-bootstrap)!
We need to clean up the themes, make theme usage guides with theme-specific markup examples.


