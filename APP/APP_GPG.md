# GnuPG的安装及使用

## 对Linux需要安装
```
1 GnuPG2
2 ccrypt
3 Seahorse
4 Seahorse-nautilus
```

## 对Windows需要安装
```
1 gpg4win
2 ccrypt
```

## 两个个人公钥

* [个人](gpgkeys/Xei4kau9.personal.public.asc)
* [工作](gpgkeys/EiX8rooc.office.public.asc)

## 为Github添加GPG签名认证
```
1 向Github添加生成的密钥对的公钥
2 git config --global user.signingkey KeyID # 设置默认使用的密钥的ID
3 git commit -S -m "somthing" # 在commit时使用-S选项
4 确保使用密钥的邮件地址与git的user.email相同
```
