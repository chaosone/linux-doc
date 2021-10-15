v2rayA 入门指南
v2rayA 是个基于 v2ray 的 web 端实现。
因为 v2rayA 是基于 v2ray 的，所以首先安装 v2ray-core,在 arch 下使用 pacman 即可：

## Installation

### Install v2ray

sudo pacman -S v2ray
安装后使用 systemctl 查看服务
sudo systemctl list-units | grep v2ray
如果看到有 v2ray.service 表示安装成功

### Install v2rayA

使用 aur 助手安装 v2rayA
yay -s v2raya
选择 v2raya-bin 那一项安装即可

## Starting

先 enable 服务创建 symbol link,在用 systemctl start 启动服务

```
sudo systemctl enable v2ray
sudo systemctl enable v2rayA
sudo systemctl start v2ray
sudo systemctl start v2rayA
```

最后查看一下 v2ray 和 v2rayA 的服务状态

```
sudo systemctl status v2ray
sudo systemctl status v2rayA
```

如果状态都是 loaded,active,running 并且没有报错那么就表示启动服务成功了。

### v2rayA configration

v2rayA 提供一个易用的 web 管理页面来设置 v2ray.
打开浏览器，在地址栏输入 localhost:2017, 登陆 web 管理页面.
首次登陆需要设置登陆帐号密码，设置好后点登陆进入管理页面。

点击右上角的设置可以进入设置界面，透明代理那一项一般选择[大陆白名单]即可
其余选项按需要设置即可.更多设置可以参与官方文档
[导入]用来导入机场订阅链接.

### see also

more info you can visit this office document:
https://v2raya.org/docs/prologue/installation/archlinux/
