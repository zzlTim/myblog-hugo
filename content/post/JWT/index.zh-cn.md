---
title: JWT跨域
description: 仅供参考
date: 2024-04-21
slug: 
image: 2.jpg
categories:
    - web
    - 测试
# comments: true
---
用户认证一般流程
	用户向服务器发送用户名和密码
	服务器验证通过后，在当前对话（session）保存相关数据，比如登录时间
	服务器返回一个session_id,写入用户的cooKie
	用户之后的每一次请求，都会通过cookie，将session_id传回服务器
	服务器根据session_id，找到之前保存的数据，得知用户身份

但是这样session扩展性不好，多台服务器如何共享session
每次请求服务，分配的服务器可能不同
①session持久化，写入数据库
②数据保存在客户端，每次请求都发回服务器，Token认证就是代表

Token是服务端产生的字符串，是客户端访问资源节课（API）所需的资源凭证，
	客户端使用用户名和密码，服务端收到请求，验证
	验证成功，服务器会签发一个token病把这个token发送给客户端
	客户端收到token后，会存起来，放到cookie或者localstorage
	客户端每次请求服务器都要带这个签发的token（令牌）
	服务端收到请求，去验证token，验证成功就返回它请求的数据

token方法服务器不存数据，因此减轻压力
但是解析token需要时间，因此用时间换空间
token由应用管理，可以避开同源策略

JWT是JSON Web Token
JWT原理是，服务器认证后，生产一个json对象，发回给用户
{“姓名”：’111‘,
"角色"：‘root’,
“到期时间”:'2022-2-2-0:0'
}
每次通信，都要发回这个json对象，服务器完全靠这个认证用户身份
为了防止用户篡改，会生产对象时加上签名

JWT有3部分
header头部
payload负载
signature签名
最终组合为一个字符串，用.分开
Header部分是一个json对象，描述JWT的元数据，例如签名算法“alg”:"HS256",令牌类型‘type’：‘JWT’
payload也是json，存实际需要传递的数据选用，客户也看得到
signature只有服务器知道，利用签名header的签名算法生成签名

JWT可以存在cookie也可以存在localSTORAGE
但是这样不能跨域
所以最好放在HTTP请求的头信息“authorization”