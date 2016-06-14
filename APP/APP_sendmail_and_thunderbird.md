# 配置sendmail支持本地收发邮件及配置Thunderbird账户

## 安装sendmail
```
sudo apt-get install sendmail mailutils
# 如果Hostname不规范先修改/etc/host进行修改
sudo adduser codevampire mail
# 将自己的用户添加进mail组，使Thunderbird有权限访问/var/mail
```
此时已经可以使用mail命令行工具发邮件了，之后配置Thunderbird。

## 配置Thunderbird
```
# 账户管理-》添加其它账户-》unix mailspool(movemail)
# 填写用户名及邮箱地址，如codevampire,codevampire@localhost
# 修改新添加的账户属性，将本地目录设置为/var/mail
# 账户管理-》添加SMTP服务器-》描述localhost-》服务器地址localhost-》端口25-》链接安全无-》认证无-》用户codevampire@localhost
```
至此可以通过Thunderbird发送邮件，为Thunderbird添加engimail插件，配合GNUPG发送经签名并加密的邮件。
