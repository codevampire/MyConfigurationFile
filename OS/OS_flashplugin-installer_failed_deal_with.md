# 解决UBUNTU更新flashplugin-installer错误
```
$ cd /usr/share/package-data-downloads/
$ sudo rm * -rf
$ cd /var/lib/update-notifier/package-data-downloads/
$ sudo rm * -rf
$ cd /var/lib/update-notifier/user.d/
$ sudo rm data-downloads-failed
```

