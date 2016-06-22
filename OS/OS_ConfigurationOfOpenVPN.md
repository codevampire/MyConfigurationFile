# OpenVPN服务

## 服务器配置

### 安装OpenVPN
```
$ sudo apt-get install openvpn easy-rsa

$ mkdir /etc/openvpn/easy-rsa/
$ sudo cp /usr/share/easy-rsa/* /etc/openvpn/easy-rsa/

```
编辑/etc/openvpn/easy-rsa/vars文件，填写必要的信息。
```
export KEY_COUNTRY="CN"
export KEY_PROVINCE="JL"
export KEY_CITY="ChangChun"
export KEY_ORG="codevampire"
export KEY_EMAIL="ywh.office@qq.com"
export KEY_CN=MyVPN
export KEY_NAME=MyVPN
export KEY_OU=MyVPN
export KEY_ALTNAMES="MyVPN"
```
切换root用户，创建服务器证书与密钥。
```
$ su -
# cd /etc/openvpn/easy-rsa
# source vars
# ./clean-all
# ./build-ca

# ./build-key-server server_name
# ./build-dh

# cd keys
# cp server_name.crt server_name.key ca.crt dh2048.pem /etc/openvpn/
```
用户证书及密钥创建。
```
$ su -
# cd /etc/openvpn/easy-rsa
# source vars
# ./build-key client_name
```
客户端需要服务器的ca.crt文件、client_name.crt、client_name.key三个文件，外加OpenVPN的配置文件。证书与密钥生成后，服务器端不必保留客户端的crt与key文件。

### 配置OpenVPN
将默认配置文件复制到etc下，并修改到可用状态。
```
sudo cp /usr/share/doc/openvpn/examples/sample-config-files/server.conf.gz /etc/openvpn/
sudo gzip -d /etc/openvpn/server.conf.gz
sudo cp /usr/share/doc/openvpn/examples/sample-config-files/client.conf ~/client.ovpn
```
更改服务器端配置/etc/openvpn/server.conf，注意保持部分选项在服务器端、客户端同步，如压缩、协议类型、端口等。
```
port 443
# 默认1194端口可能会被设置严格的网关过滤掉，使用https的443端口避免这一问题
proto tcp
# udp的性能更好，但可能会被过滤掉
dev tun
ca ca.crt
cert usrv.fagcrdc.com.crt
key usrv.fagcrdc.com.key  # This file should be kept secret
dh dh2048.pem
# 指定服务器的证书、密钥
server 10.8.0.0 255.255.255.0
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 208.67.222.222"
push "dhcp-option DNS 208.67.220.220"
duplicate-cn
keepalive 10 120
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
```
配置系统防火墙及转发规则
```
# echo 1 > /proc/sys/net/ipv4/ip_forward
# vim /etc/sysctl.conf
# 将net.ipv4.ip_forward=1的注释去掉
# ufw allow 443/udp
# vim /etc/default/ufw
# 修改DEFAULT_FORWARD_POLICY="ACCEPT"
# vim /etc/ufw/before.rules
```
在before.rules中添加转发规则，如下所示。
```
#
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#

# START OPENVPN RULES
# NAT table rules
*nat
:POSTROUTING ACCEPT [0:0]
# Allow traffic from OpenVPN client to eth0
-A POSTROUTING -s 10.8.0.0/8 -o eth0 -j MASQUERADE
COMMIT
# END OPENVPN RULES

# Don't delete these required lines, otherwise there will be errors
*filter
```
重启防火墙，重启openvpn服务。
