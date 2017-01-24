# X 相关配置

## 调整console界面显示分辨路
```
# 显示支持的分辨率模式
sudo hwinfo --framebuffer

# 编辑/etc/default/grub
GRUB_GFXMODE=1440x900x32
GRUB_GFXPAYLOAD=1440x900x32
```
