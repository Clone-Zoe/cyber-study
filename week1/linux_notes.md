# Week 1 linux 基础命令笔记

## 一、文件与目录操作
| 命令 | 作用 | 示例 |
|------|------|------|
| pwd | 显示当前路径 | pwd |
| ls | 列出目录 | ls -la |
| cd | 切换目录 | cd /home, cd .., cd ~ |
| touch | 创建空文件 | touch test.txt |
| mkdir | 创建目录 | mkdir folder |
| cp | 复制 | cp a.txt b.txt |
| mv | 移动/重命名 | mv a.txt b.txt, mv file /tmp/ |
| rm | 删除 | rm file, rm -r folder |

## 二、权限管理
- r=4, w=2, x=1
- chmod 755 file -> rwxr-xr-x
- chmod +x file -> 添加执行权限
- chmod user:group file -> 修改所有者

## 三、搜索与文本
- find / -name "*.log" 2>/dev/null
- grep "keyword" file
- cat file | grep "keyword"

## 四、进程与网络
- ps aux | grep process
- top -> 按q退出
- kill PID, kill -9 PID
- ip addr -> 查看IP
- ping -c 3 baidu.com

## 五、软件与服务
- sudo apt update / upgrade /install / remove
- sudo systemctl start / stop / enable / disable ssh

## 六、用户管理
- sudo useradd -m username
- sudo passwd username
- sudo usermod -aG sudo username
- su - username


