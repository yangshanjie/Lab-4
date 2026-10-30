# Lab-4
curl命令行工具实验作业
## 、curl 是什么

##一、curl 是一款**命令行的网络请求工具**，可以不用浏览器，直接在终端向服务器发送 HTTP 请求、接收返回数据，支持 HTTP、HTTPS 等多种协议。本次实验使用 Windows 系统自带的 curl.exe。



## 二、本次用到的 HTTP 基础概念


1. **GET 请求**：默认请求方式，用来从服务器获取数据，不需要带`-X`参数。
示例：`curl.exe https://httpbin.org/ip`
2. **POST 请求**：向服务器提交数据，必须用`-X POST`指定请求方法。
   - `-X`：指定 HTTP 请求方法
   - `-H`：添加请求头，`Content-Type:application/json`代表传输 JSON 格式数据
   - `-d`：携带要发给服务器的数据
3. [httpbin.org](https://httpbin.org)：免费 HTTP 测试服务（回声服务器），专门调试网络请求，会把收到的请求信息返回给客户端。

## 三、常见返回状态码

- **200 OK**：请求成功，服务器正常返回数据（成功的 ip 查询就是 200）
- **404 Not Found**：地址不存在，服务器找不到这个接口
- **405 Method Not Allowed**：请求方法和接口不匹配。例：用 GET 访问`/post`接口，`/post`只接收 POST 请求

## 四、实验两条核心命令

1. GET 请求（查询本机公网 IP）

```
curl.exe https://httpbin.org/ip
```

返回 JSON 格式的 IP 信息：`{"origin": "你的公网IP"}`

2. POST 请求（提交 JSON 数据）

```
curl.exe -X POST -H "Content-Type:application/json" -d "{\"name\":\"tommy\"}" https://httpbin.org/post
```

> 
> Windows 终端中 JSON 内部双引号需要加`\`转义<img width="806" height="449" alt="屏幕截图 2026-10-30 192803" src="https://github.com/user-attachments/assets/4a5f34d6-5b3d-4c4d-b2b0-787eb9d60181" />


## 五、实验结论

curl 实现了客户端和 Web 服务器之间的数据收发，验证了 HTTP 不同请求方式的区别；命令行方式可以脱离图形化浏览器，灵活调试接口。
