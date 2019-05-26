# Options 请求

## 同时options请求具备以下特性：

选项	是否允许	备注
Request has body	No	没有请求体
Successful response has body	No	成功的响应没有响应体
Safe	Yes	安全
Idempotent	Yes	密等性，不变性，同一个接口请求多少次都一样
Cacheable	No	不能缓存
Allowed in HTML forms	No	不能在表单里使用

- 简言之，options请求是用于请求服务器对于某些接口等资源的支持情况的，包括各种请求方法、头部的支持情况，仅作查询使用。

```javascript
->>> curl -X OPTIONS https://xxxx.com/micro/share/getShareRecord -i

HTTP/1.1 200 OK
Server: nginx/1.13.3
Date: Mon, 30 Jul 2018 12:50:08 GMT
Content-Length: 0
Connection: keep-alive
Allow: GET, HEAD, POST, PUT, DELETE, TRACE, OPTIONS, PATCH
X-Frame-Options: SAMEORIGIN
Access-Control-Allow-Origin: 0
Access-Control-Allow-Credentials: true
Access-Control-Allow-Headers: X-Requested-With

```

- 通过curl来发送一个http请求，在响应头中可以发现服务器上这个接口对请求方法以及一些header的使用允许情况，也就是上面说的获取服务器对于某些资源的选项、支持情况。
而除了这些，options和其他http请求还有什么不同么？答案是有的

## 浏览器级行为

- 把浏览器自主发起的行为称之为“浏览器级行为”。之所以说options是一种浏览器级行为，是因为在某些情况下，普通的get或者post请求回首先自动发起一次options请求，当options请求成功返回后，真正的ajax请求才会再次发起。

- 再来看下这个“某些情况下”都是什么情况？

- 1、跨域请求，非跨域请求不会出现options请求
- 2、自定义请求头
- 3、请求头中的content-type是application/x-www-form-urlencoded，multipart/form-data，text/plain之外的格式

- 当满足条件12或者13的时候，简单的ajax请求就会出现options请求，有没有感觉到一点同源策略的意思，个人理解这个就是浏览器底层对于同源策略的一个具体实现。首先得到服务器端的确认，才能继续下一步的操作，这也是为什么options请求也被叫做“预检”请求的原因吧。

