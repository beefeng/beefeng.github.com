---
layout: post
title: "jekyllbootstrap 相关命令记录"
description: ""
category: 
tags: []
---
{% include JB/setup %}



##文章  
####新建文章
	$ rake post title="Hello World"


##页面
####新建页面  
	$ rake page name="about.md"  

####新建子页面  
	$ rake page name="pages/about.md"
	
##主题
####安装主题
	$ rake theme:install git="https://github.com/jekyllbootstrap/theme-the-program.git"  
   or  
   
	$ rake theme:install name="THEME-NAME"

####切换主题
	$ rake theme:switch name="the-program"




已安装主题：  
>rake theme:install git="https://github.com/jekyllbootstrap/theme-the-minimum.git"  
>rake theme:install git="https://github.com/jekyllbootstrap/theme-tom.git"  
>rake theme:install git="https://github.com/jekyllbootstrap/theme-mark-reid.git"  
>rake theme:install git="https://github.com/acanimal/JB_simplestyle_7.git"  
>rake theme:install git="https://github.com/bcachet/theme-modernist.git"  
>rake theme:install git="https://github.com/FlorianWolters/jekyll-bootstrap-theme.git"  