---
title: vue-element-admin后台集成方案
description: 仅供参考
date: 2024-04-21
slug: 
image: 2.jpg
categories:
    - 工具分享
    - 测试
# comments: true
---

[https://panjiachen.github.io/vue-element-admin-site/zh/](https://panjiachen.github.io/vue-element-admin-site/zh/)

错误： git SSL certificate problem: unable to get local issuer certificate

这个问题是由于没有配置信任的服务器HTTPS验证。默认，cURL被设为不信任任何CAs，就是说，它不信任任何服务器验证。

只需要执行下面命令就可以解决：

```
git config --global http.sslVerify false
```
[安装失败可以看这个](https://blog.csdn.net/qq_64760783/article/details/131340578)
