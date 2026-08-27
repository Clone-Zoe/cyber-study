# OSI 七层模型 vs TCP/IP 四层模型

## OSI 七层模型（物数网传会表应）

7. 应用层 Application    -> HTTP, FTP, SSH, DNS
6. 表示层 Presentation   -> SSL/TLS, 加密, 编码
5. 会话层 Session        -> 会话管理
4. 传输层 Transport      -> TCP, UDP
3. 网络层 Network        -> IP, ICMP, ARP, 路由器
2. 数据链路层 Data Link  -> MAC地址, 以太网, 交换机
1. 物理层 Physical       -> 网线, 光纤, 集线器

## TCP/IP 四层模型

4. 应用层                -> HTTP/FTP/SSH/DNS (合并OSI的7+6+5)
3. 传输层                -> TCP/UDP
2. 网络层                -> IP/ICMP/ARP
1. 网络接口层            -> MAC/以太网 (合并OSI的2+1)

## 核心概念

### 为什么需要 IP 和 MAC 两种地址？
- IP：全局寻址，跨网络路由（门牌号）
- MAC：局域网内点对点传输（身份证号）
- ARP：IP → MAC 的查询协议

### ICMP类型
- Type 8 Code 0 = Echo Request (ping请求)
- Type 0 Code 0 = Echo Reply (ping回复)
- Type 11 = Time Exceeded (TTL耗尽)  

### TTL
- 每经过一个路由器减1
- 减到0被丢弃，防止环路
- Linux默认64, Windows默认128
