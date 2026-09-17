# Nmap 常用参数速查表

## 一、主机发现（不扫端口）
nmap -sn 192.168.1.0/24  # Ping 扫描，发现存活主机
nmap -Pn 192.168.1.0  # 跳过 Ping，直接扫端口（目标禁 Ping 时用）

## 二、端口扫描
sudo nmap -sS 192.168.1.1   # SYN 半开扫描（快、隐蔽，需 root）
nmap -sT 192.168.1.1  # TCP Connect 扫描（完整握手）
sudo nmap -sU -p 53,161 192.168.1.1   # UDP 扫描（慢）

## 三、指定端口
nmap -p 80 192.168.1.1   # 只扫 80
nmap -p 1-1000 192.168.1.1  # 扫 1-1000
nmap -p- 192.168.1.1  # 扫全端口 1-65535
nmap -p 22,80,443,3306,3389,8080 192.168.1.1  # 指定多个

## 四、服务与系统探测
sudo nmap -sV 192.168.1.1  # 探测服务版本
sudo nmap -O 192.168.1.1  # 探测操作系统
sudo nmap -A -T4 192.168.1.1  # 全开扫描（版本+OS+脚本+路由）

## 五、输出保存
nmap -oN result.txt 192.168.1.1  # 普通文本
nmap -oX result.xml 192.168.1.1 # XML 格式
nmap -oG result.grep 192.168.1.1  # Grepable 格式

## 六、常用组合（实战）
# 快速扫描 Top 1000 端口
sudo nmap -sS -sV -T4 192.168.1.1

# 全面扫描
sudo nmap -sS -A -p- -T4 192.168.1.1 -oN full_scan.txt

# 局域网主机发现
sudo nmap -sn 192.168.1.0/24

## 七、状态解读
| 状态 | 含义 |
|------|------|
| open | 端口开放，服务在运行 |
| closed | 端口关闭，无服务 |
| filtered | 被防火墙过滤，无法确定 |
| unfiltered | 端口可达，但 Nmap 无法确定开闭 |

