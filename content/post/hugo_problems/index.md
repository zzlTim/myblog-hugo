---
title: 使用hugo-stack遇到的问题和解决方法
description: 仅供参考
date: 2024-04-21
slug: hugo-problems
image: 2.jpg
categories:
    - 建站
    - 测试
# comments: true
---
## 0基础教学

{{< bilibili BV15f4y157a6 >}}

## 博文头信息解析

>title: 博文标题  
>description: 副标题/博文描述   
>date: 日期2024-04-21  
>slug: 博文代号/博文url/若使用已有的slug，则会直接覆盖，因为文件目录唯一    
>image: 封面图片.jpg  
>categories:  
>    - 博文标签1  
>    - 博文标签2

## 网站图片插入问题
[Hugo 静态网站图片插入问题](https://blog.dontjudge.cn/post/hugo-%E9%9D%99%E6%80%81%E7%BD%91%E7%AB%99%E5%9B%BE%E7%89%87%E6%8F%92%E5%85%A5/#:~:text=%E6%98%BE%E7%84%B6%E4%B8%8D%E8%83%BD%EF%BC%8C%E5%9B%A0%E4%B8%BA%E8%B7%AF%E5%BE%84%E4%B8%8D%E4%B8%80%E8%87%B4%EF%BC%9A%20static%EF%BC%9AC%3AUsersDeng-OneDrive%5B%26Hu%26%5DgoBlogstaticimg%20markdown%E6%96%87%E6%A1%A3%EF%BC%9AC%3AUsersDeng-OneDrive%5B%26Hu%26%5DgoBlogcontentpost%20%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%88%20%E5%9F%BA%E4%BA%8E%E4%BB%A5%E4%B8%8A4%E7%82%B9%E5%8E%9F%E5%9B%A0%EF%BC%8C%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%88%E6%9C%89%E4%BB%A5%E4%B8%8B%E5%87%A0%E7%A7%8D%EF%BC%9A%20%E5%9C%A8,%2Fpost%2Fimg%20%E9%87%8C%E6%94%BE%E5%9B%BE%E7%89%87%EF%BC%8C%E7%84%B6%E5%90%8E%E5%A4%8D%E5%88%B6%E5%88%B0%20%2Fstatic%2Fimg%20%E8%AF%84%E4%BB%B7%EF%BC%9A%E9%BA%BB%E7%83%A6%20%E5%9C%A81%E7%9A%84%E5%9F%BA%E7%A1%80%E4%B8%8A%EF%BC%8C%E5%86%99%E4%B8%80%E4%B8%AA%E6%89%B9%E5%A4%84%E7%90%86%EF%BC%8C%E5%AE%8C%E6%88%90%E5%A4%8D%E5%88%B6%E7%9A%84%E4%BB%BB%E5%8A%A1%EF%BC%9B%EF%BC%88%E5%9B%A0%E4%B8%BA%E4%B9%8B%E5%89%8D%E5%86%99%E8%BF%87%E7%9A%84%E6%89%B9%E5%A4%84%E7%90%86%EF%BC%9A%E7%94%9F%E6%88%90%20public.cmd%EF%BC%8C%E5%8F%AA%E8%A6%81%E5%9C%A8%E5%89%8D%E9%9D%A2%E5%8A%A0%E4%B8%8A%E5%A4%8D%E5%88%B6%E7%9A%84%E5%91%BD%E4%BB%A4%E5%B0%B1%E8%A1%8C%EF%BC%89%20%E8%AF%84%E4%BB%B7%EF%BC%9A%E5%8F%AF%E8%A1%8C%EF%BC%8C%E4%BD%86%E6%98%AF%E4%B8%8D%E5%AE%8C%E7%BE%8E%EF%BC%8C%E5%8F%AF%E8%83%BD%E5%87%BA%E7%8E%B0%E6%96%87%E4%BB%B6%E6%9D%83%E9%99%90%E9%97%AE%E9%A2%98)

>新版hugo-stack直接复制example的内容会出现无法加载图片的问题。
>因为对于新版的的hugo主题，他默认静态资源都是存储在static文件夹下，
>所以图片路径不能存放到.md同目录，而是需要放到static文件夹，同时保持相对路径。

## MarkDown常用语法

*[MarkDown常用语法](https://www.youtube.com/watch?v=3aypp_YlBzI)*

## 插入图片

![测试图片相对路径](./1.jpg)  
![Photo by Luca Bravo on Unsplash](luca-bravo-alS7ewQ41M8-unsplash.jpg) 


```markdown
![测试图片相对路径](./1.jpg)  
![Photo by Luca Bravo on Unsplash](luca-bravo-alS7ewQ41M8-unsplash.jpg) 

```

控制菜单栏的文件目录
>\content\page\

头信息解析
```markdown
title: "标题"
layout: "查找3" # 搞不懂
menu:
    main:
        weight: 100 #控制菜单项位置顺序，数值越大越下面，越小越上面 
        params: 
            icon: user #图标去网站看代码
```
## 头像路径
>\themes\hugo-theme-stack\assets\img
其实可以直接改路径，但是还是直接替换原图片最简单好懂