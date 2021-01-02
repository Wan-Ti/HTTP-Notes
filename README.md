# HTTP-Notes

**IP**

IP分为内网和外网；
几个特殊IP：

    · 127.0.0.1表示自己
    · localhost通过hosts指定为自己；
    · 0.0.0.0不表示任何设备

**端口号**

一台机器可以提供多个服务，每个服务拥有自己的一个号码，该号码称作端口号port.

提供HTTP服务最好使用80端口;</br>
提供HTTPS服务最好使用443端口</br>
提供FTP服务最好使用21端口；</vr>
一共有65535个端口；

端口使用规则

    · 0到1923号端口是留给系统使用；
    · 只有拥有了管理员权限后，才能使用1024个端口；
    · http-server默认使用8080端口

**域名(IP)**

想知道该域名对应什么IP，可通过```ping 该域名```得到

知识点

    · 一个域名可以对应不同IP；(这就是负载均衡)
    · 一个IP对应不同域名; (这个叫做共享主机)
    
**域名和IP对应过程**

参考博客：<a href="https://juejin.cn/post/6844903985556488205">在浏览器输入 URL 回车之后发生了什么</a>

 ---

## URL

**协议+域名或IP+端口号+路径+查询字符串+锚点**

---


## HTTP协议

**基于TCP和IP两个协议**

客户端向服务器发出请求，服务器收到请求会对客户端做出响应;

<a href="https://github.com/FrankFang/nodejs-test/blob/master/server.js">服务器响应代码</a>

注意事项：

    · 这些代码就是服务器代码，一般放在服务器上；
    · path是不带查询参数的路径/x
    · query是查询参数的对象形式{a:'1'};
    · queryString是查询参数的字符串形式?a=1;
    · pathWithQuery是带查询参数的路径，一般不用；
    · request是请求对象；
    · response是响应对象
代码逻辑：</br>
每次收到请求都会把中间代码段执行一遍；</br>
用if else判断路径，并返回响应；</br>
如果是已知路径，一律返回200；</br>
如果是位置路径，一律返回404；</br>
Content-Type表示内容的[类型/语法]；/br>
response.write()可以填写返回的内容；</br>
response.end()表示响应可以发给用户了；</br>

### HTTP基础概念

```
请求:
请求动词 路径加查询参数 协议名/版本
Host: 域名或IP;
Accept:text/html;
Content-Type:请求体的格式；
回车；
请求体(上传内容);

响应：
协议名/版本 状态码 状态字符串
Content-Type:响应体的格式
回车；
响应体；                                   
```
**用curl构造请求**

 curl -v http://127.0.0.1:8888
 
 设置请求动词：</br>
 -X POST</br>
 注意大小写</br>
 
 设置路径和查询参数：直接在url后面加
 
 设置请求头：
 -H 'Name:Value'或者--header'Name:Value'
 
 设置请求体：
 -d '内容' 或者 --data '内容'

**用Node.js读取请求**

读取请求动词：request.method;

读取路径：</br>
request.url路径，带查询参数；</br>
path纯路径，不带查询参数；</br>
query只有查询参数</br>

读取请求头：request.headers['Accept']

**用Node.js设置响应**

设置响应状态码：reponse.statusCode=200;

设置响应头：response.setHeader('Content-Type','text/html');

设置响应体：response.write('内容')；


    
