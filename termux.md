## termux user guide

###安装 OpenSSH
$ pkg install openssh

###运行 SSH Server
$ sshd

###设置密码
$ passwd

###获得 Android IP
$ ifconfig

###客户端运行
$ ssh android_ip -p 8022

### termux-api 命令无效

安装 termux-api
如果是从 f-droid 安装的 tmux,那么需要在 f-droid 安装 termux-api,然后再在手机 termux 终端内安装一遍,然后就可以通过 ssh 用 termux-api 控制手机了.
