# HTTP协议学习笔记

## 一、HTTP 基础
- HTTP = 超文本传输协议，基于 TCP 端口 80
- 无状态：服务器默认不记得你是谁
- 请求-响应模型：客户端发请求，服务器返回响应

## 二、请求方法
| 方法 | 作用 | 参数位置 |
|------|------|---------|
| GET | 获取资源 | URL 后面 (?id=1) |
| POST | 提交数据 | Body |
| PUT | 更新资源 | Body |
| DELETE | 删除资源 | URL/Body |
| HEAD | 只获取响应头 | — |

GET vs POST
- GET参数在 URL，有长度限制，会被浏览器记录
- POST参数在 Body，相对安全（但 HTTP 仍明文）

## 三、状态码
| 类别 | 范围 | 常见码 |
|------|------|--------|
| 1xx | 信息 | 100 Continue |
| 2xx | 成功 | 200 OK, 201 Created |
| 3xx | 重定向 | 301 永久, 302 临时, 304 缓存 |
| 4xx | 客户端错误 | 400 格式错, 401 未认证, 403 无权限, 404 不存在 |
| 5xx | 服务端错误 | 500 内部错误, 502 网关错误, 503 不可用 |

## 四、常见请求头
| 字段 | 含义 |
|------|------|
| Host | 目标域名 |
| User-Agent | 客户端身份 |
| Accept | 接受的数据类型 |
| Content-Type | Body 格式 |
| Cookie | 携带的身份凭证 |
| Referer | 从哪个页面跳转 |


## 五、常见响应头
| 字段 | 含义 |
|------|------|
| Server | 服务器软件 |
| Content-Type | 响应体格式 |
| Set-Cookie | 服务器下发 Cookie |
| Location | 重定向地址 |

## 六、Cookie vs Session
- Cookie：存在客户端，每次请求自动带上
- Session：存在服务器，Cookie 里只存 Session ID
- HTTP 无状态，靠 Cookie/Session 实现"记住登录"

## 七、HTTPS = HTTP + TLS
- 加密：防止窃听
- 完整性：防止篡改
- 身份认证：数字证书确认服务器身份
- TLS 握手：交换密钥 → 生成会话密钥 → 加密通信

## 八、curl 常用命令
curl -I http://example.com  #只看响应头
curl -v http://example.com  #详细模式
curl -H "UA: xxx" http://example.com  # 自定义头
curl -x POST -d "a=1" http://bin.com  #POST
curl -L http://example.com  # 跟随重定向
curl -o file.html http://example.com  # 保存文件

## 九、Wireshark 过滤
- http — 只看 HTTP 包
- http.request.method == "GET" — 只看 GET
- http.response.code == 200 — 只看 200 响应

## 十、HTTP 请求报文结构图

┌─────────────────────────────────────┐
| 请求行 (Request Line)               |
| GET /index.html HTTP/1.1            |
|-------------------------------------|
| 请求头 (Request Headers)            |
| Host: example.com                   |
| User-Agent: Mozilla/5.0             |
| Accept: text/html                   |
| Cookie: sessionid=abc123            |
| Content-Length: 0                   |
|-------------------------------------|
| 空行 (\r\n)                         |
|-------------------------------------|
| 请求体 (Request Body)               |
| (GET 通常为空，POST/PUT 有数据)     |
| username=admin&password=123         |
└─────────────────────────────────────┘

## 十一、HTTP 响应报文结构图

┌─────────────────────────────────────┐
│  状态行 (Status Line)               │
|  HTTP/1.1 200 OK                    |
|-------------------------------------|
|  响应头 (Response Headers)          |
|  Server: nginx/1.18                 |
|  Content-Type: text/html            |
|  Content-Length:1256                |
|  Set-Cookie: id=xyz;Path=/          |
├─────────────────────────────────────┤
│  空行 (\r\n)                        │
├─────────────────────────────────────┤
│  响应体 (Response Body)             │
|  <html>...web content...</html>     |
└─────────────────────────────────────┘

