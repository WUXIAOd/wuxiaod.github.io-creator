---
title: "web性能优化"
date: 2019-09-22T19:17:26+08:00
draft: false
---
#### web性能优化：（从理论上来讲）

地址栏输入url到按下回车这一过程中有哪些前端相关的内容：

1. 看有没有缓存
2. DNS查询
3. 建立TCP连接
4. 发送HTTP请求   后台处理
5. 接收响应
6. 接收完成得到一个html
7. 判断文本类型，DOCTYPE     html/xml
8. 浏览器逐行解析html
9. 看到<h1>chrom会等css加载完再渲染到页面
10. 看到CSS，下载css，如果有多个css便同时下载(chrom8个)。css,并行下载，串行解析。
11. 看JS，下载并行，串行解析。在chrom中，css会阻塞html渲染，IE不会。JS一定会阻塞html渲染（不管什么浏览器）。

#### 跟前端无关的优化：
* 优化DNS查询：减少DNS查询（减少域名数量）。
  
* TCP连接复用（keep-alive）http/2.0多路复用。

#### 前端优化：
1. 发送http请求：

* 减少cookie体积（减少请求）；合并文件。

* 使用cache-control（干掉请求）；

* 同时发多个请求，如ie中一个域名能发4个请求，但我可以使用两个域名或多个。于是与上面的DNS查询优化有矛盾，但是经过权衡之后，文件少的时候，就减少域名使用。文件多时，增加DNS查询时间，但减少了请求时间（用户带宽足够前提下）。

1. 接收响应

* 使用ETAG，如果请求时带上服务器给的ETAG时，服务器便不再响应新的内容，返回304,表示not modifile；

* 文件大时使用Gzip压缩。

1. 返回的html中的DOCTYPE不能不写，不能写错。尽量减少标签。
   
2. CSS和JS优化：
   
* 使用CDN（内容分发网络）；
  
* CSS放到head, JS 放body最后。css放前面的原因是让它尽早下载完，下载完就可以渲染了。js放后面是因为页面没有js还是可以看的，所以可以保证用户优先看到完整的页面。尽早显示页面，获取节点。

* 延迟加载，懒加载：必须初始化的先加载，剩余的延迟加载。如第一屏先加载，其余的等用户滚到再加载。

* 使用外部js和css，就是不要把js,css写在html中。

* 压缩图片。