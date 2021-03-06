<!-- vim-markdown-toc GFM -->

            * [install yay on arch(install software from aur)](#install-yay-on-archinstall-software-from-aur)
            * [install linux brew](#install-linux-brew)
            * [install node & npm(nodejs package manager)](#install-node--npmnodejs-package-manager)
            * [pip install & configration](#pip-install--configration)
            * [install source-code-pro-fonts](#install-source-code-pro-fonts)
            * [set goproxy (installing yay time out)](#set-goproxy-installing-yay-time-out)
            * [install ranger pluign](#install-ranger-pluign)
            * [alsamixer to control sound](#alsamixer-to-control-sound)
            * [chromium bookmarks location](#chromium-bookmarks-location)
            * [auto-pep8 not found when format code in (vim/nvim).](#auto-pep8-not-found-when-format-code-in-vimnvim)
            * [install samba server && configration](#install-samba-server--configration)
            * [ag usage (from tldr)](#ag-usage-from-tldr)
            * [add archlinuxcn repo](#add-archlinuxcn-repo)
            * [pacman pgp key error](#pacman-pgp-key-error)
            * [/var/cache/ 空间占用过大](#varcache-空间占用过大)
            * [用 whiskermenu 代替默认的 xfce4 开始菜单](#用-whiskermenu-代替默认的-xfce4-开始菜单)
            * [use swap file instead of swap space](#use-swap-file-instead-of-swap-space)
            * [install bspwm](#install-bspwm)
            * [install steam](#install-steam)
            * [where is the documentation and example(template) on linux](#where-is-the-documentation-and-exampletemplate-on-linux)
            * [install fzf(using git)](#install-fzfusing-git)
            * [alacritty theme selector](#alacritty-theme-selector)
            * [config sxhkd shorcut](#config-sxhkd-shorcut)
            * [Linux Font](#linux-font)
                * [wd-dict install](#wd-dict-install)
                * [config static ip on linux](#config-static-ip-on-linux)
            * [Editing shell cmd with $EDITOR](#editing-shell-cmd-with-editor)
            * [set the display resolution](#set-the-display-resolution)
            * [arch 安装中文字体](#arch-安装中文字体)
                * [使用清华源替换官方 aur 地址](#使用清华源替换官方-aur-地址)
            * [set LANG enviroment](#set-lang-enviroment)
            * [xmodmap 修改键位绑定](#xmodmap-修改键位绑定)
            * [pacman 备份和恢复已安装软件包](#pacman-备份和恢复已安装软件包)
            * [shell 脚本中 echo 显示内容带颜色](#shell-脚本中-echo-显示内容带颜色)
            * [显示当前正在运行的 shell 类型](#显示当前正在运行的-shell-类型)
            * [use terminus font on tty](#use-terminus-font-on-tty)
            * [sed 直接修改文件](#sed-直接修改文件)
            * [bash 批量重命名](#bash-批量重命名)
            * [echo ssid connected](#echo-ssid-connected)
            * [逐行读取的区别(shell)](#逐行读取的区别shell)
            * [youtube-dl 下载视频为 mp3](#youtube-dl-下载视频为-mp3)
            * [xargs usage](#xargs-usage)
            * [Install packages from a text file](#install-packages-from-a-text-file)
            * [cp arguments](#cp-arguments)
            * [show and execable cmd's info](#show-and-execable-cmds-info)
            * [crontab 定时任务](#crontab-定时任务)
            * [tmux manaual](#tmux-manaual)
            * [systemd 电源控制](#systemd-电源控制)
            * [ssh 免密码登陆](#ssh-免密码登陆)
* [scp ~/.ssh/id_rsa.pub user@remote_host:](#scp-sshid_rsapub-userremote_host)
            * [kill and pkill](#kill-and-pkill)
            * [how to read man page](#how-to-read-man-page)
            * [更改电源行为(systemd)](#更改电源行为systemd)

<!-- vim-markdown-toc -->

#### install yay on arch(install software from aur)

Before you begin, make sure you have the base-devel package group installed.

```bash
pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

**setps:**  
clone repo--cd into dir--makepkg -si

#### install linux brew

```bash
git clone https://github.com/Homebrew/brew ~/.linuxbrew/Homebrew
mkdir ~/.linuxbrew/bin
ln -s ~/.linuxbrew/Homebrew/bin/brew ~/.linuxbrew/bin
eval $(~/.linuxbrew/bin/brew shellenv)
```

==> Next steps:

- Run these two commands in your terminal to add Homebrew to your PATH:
  echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> /home/why/.zprofile
    eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
- Run `brew help` to get started
- Further documentation:
  https://docs.brew.sh
- Install the Homebrew dependencies if you have sudo access:
  sudo pacman -S base-devel
  See https://docs.brew.sh/linux for more information
- We recommend that you install GCC:
  brew install gcc

#### install node & npm(nodejs package manager)

sudo pacman -S nodejs npm

#### pip install & configration

- pip 使用国内镜像源

mkdir -p ~/.pip/pip.conf,edit it:  
_pip.conf:_

> > > [global]
> > > index-url = https://pypi.tuna.tsinghua.edu.cn/simple > > > [install]  
> > > trusted-host = https://pypi.tuna.tsinghua.edu.cn

#### install source-code-pro-fonts

```
sudo pacman -S adobe-source-code-pro-fonts
```

#### set goproxy (installing yay time out)

`export GOPROXY=https://goproxy.io`
,or put it to your bashrc/zshrc

#### install ranger pluign

git clone https://github.com/alexanderjeurissen/ranger_devicons ~/.config/ranger/plugins/ranger_devicons
echo "default_linemode devicons" >> ~/.config/rc.conf

#### alsamixer to control sound

把下列配置添加到系统级别的 /etc/asound.conf 或用户级别的 ~/.asoundrc 文件。如果文件不存在，可以手动创建。其中的各个 ID，请根据实际情况调整：

edit ~/.asoundrc:

```
defaults.pcm.card 1
defaults.pcm.device 0
defaults.ctl.card 1
```

#### chromium bookmarks location

~/.config/chromium/Default/Bookmarks.bak

#### auto-pep8 not found when format code in (vim/nvim).

To solve it, simply run `pip install --user autopep8` for singal user,
or if you want it globally:

```
sudo pip install autopep8
```

#### install samba server && configration

安装 软件包 samba。  
Samba 服务的配置文件是 /etc/samba/smb.conf，smb.conf(5)提供了详细的文档。  
samba 软件包没有提供此文件，启动 smb.service 前需要先创建这个文件。从 这里 可以获取到示例文件。  
从上面获取的默认配置文件里把日志 log file 设置到一个不能写的地方, 这会引起错误。下面的办法可以解决这个问题:

```
sambapasswd -a user
```

- there's an example of _smb.conf_:  
  grep -v '#' /etc/samba/smb.conf

[global]  
 workgroup = xinwei  
 server string = Samba Server Version %v  
 netbios name = lulu  
 security = user  
 [share]  
 path = /home/why/333  
 browseable = yes  
 writable = yes  
 read only = no  
 guest ok = yes

#### ag usage (from tldr)

- Find files containing "foo", and print the line matches in context:

  - ag foo

  - Find files containing "foo" in a specific directory:
    ag foo path/to/directory

  - Find files containing "foo", but only list the filenames:
    ag -l foo

  - Find files containing "FOO" case-insensitively, and print only the match, rather than the whole line:
    ag -i -o FOO

  - Find "foo" in files with a name matching "bar":
    ag foo -G bar
  - Find files whose contents match a regular expression:
    ag '^ba(r|z)$'
  - Find files with a name matching "foo":
    ag -g foo

#### add archlinuxcn repo

使用说明   
在 /etc/pacman.conf 文件末尾添加两行：

```
[archlinuxcn]
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
```

然后请安装 archlinuxcn-keyring 包以导入 GPG key。

#### pacman pgp key error

重置所有密钥
如果要删除或重置系统，删除 /etc/pacman.d/gnupg 目录

```
sudo rm -r /etc/pacman.d/gnupg
```

重新初始化 pacman-key.

```
pacman-key --init。
```

通过重新添加默认密钥

```
pacman-key --populate archlinux。
```

如果 archlinux-keyring 不是最新的，需要在更新系统前先执行

```bash
pacman -S archlinux-keyring。
```

#### /var/cache/ 空间占用过大

```
pacman -Scc
```

#### 用 whiskermenu 代替默认的 xfce4 开始菜单

whiskermenu 是一个弹出式菜单,可以搜索并启动应用程序.
使用 `yay -s whiskermenu` 安装即可.
sudo pacman -Q | grep whisker
find the package name,then use **which** to search the path of whiskermenu
在开始菜单-settings-keyboard 中可以绑定一个快捷键用来启动 whiskermenu.

#### use swap file instead of swap space

```
sudo dd if=/dev/zero of=/swapfile bs=1M count=6144 status=progress
sudo chmod 600 /swapfile
sudo makeswap /swapfile
sudo swapon /swapfile
swapon -s
```

then append to following line to /etc/fstab:

> /swapfile none swap defaults 0 0

see also:</br>
[swap_file-arch wiki](https://wiki.archlinux.org/index.php/Swap#Swap_file)

#### install bspwm

```bash
sudo pacman -S bspwm
sudo pacman -S sxhkd
```

#### install steam

edit /etc/pacman.conf:
uncomment #multilib section
then update your source datebase by `sudo pacman -sy`.
now you can install steam with pacman:

```bash
sudo pacman -S steam
```

#### where is the documentation and example(template) on linux

usually,most of utility has default configration files usually in:</br>
**/usr/share/doc**

#### install fzf(using git)

```bash
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```

#### alacritty theme selector

make sure that you have **paru** (aur helper)

```
paru -S alacritty-themes
```

see also:</br>
[alacritty-theme]https://github.com/rajasegar/alacritty-themes

#### config sxhkd shorcut

如果你想要用 Fn 键控制音量，需要自己绑定快捷键。比如说你可以用 sxhkd，然后创建配置文件 ~/.config/sxhkd/sxhkdrc，并加入以下内容

```
F8
amixer set Master toggle
{F9,F10}
amixer set Master 10{-,+} unmute
```

这样子就是 F8 静音，F9, F10 减小 / 增大音量。</br>
还可以用 xbindkeys，详情请 Google。

**losevka ttf font**  
https://aur.archlinux.org/packages/ttf-iosevka

#### Linux Font

**字体类型**

现今计算机使用的绝大多数字体，都是属于点阵字体或者轮廓字体二者之一。
点阵格式

    Bitmap Distribution Format (BDF) - 来自 Adobe
    Portable Compiled Format (PCF) - 来自 Xorg
    PC Screen Font (PSF) 内核终端字体，Xorg 不支持此格式 (Unicode PSF 文件的扩展是 psfu)

此格式可以通过 gzip 压缩。
轮廓格式

    PostScript 字体 - 来自，包含打印机 ASCII 字体 (PFA) 和打印机二进制字体 (PFB)
    TrueType - Apple 和 Microsoft 定义(ttf)
    OpenType - 基于 TrueType，Microsoft 定义(otf, ttf)

大部分情况下，TrueType 和 OpenType 之间的差异可以忽略.
**install fonts manually** </br>
要在系统范围内（对所有用户有效）安装字体，请将文件夹移动到 /usr/share/fonts/ 目录。这些文件需要对每个用户而言都是可读的，使用 chmod 来设置合理的权限 (比如，文件至少为 0444 ，而目录至少为 0555)

**更新缓存字体**

```
sudo fc-cache -vf
```

**remove package installed(and config files)**

```bash
sudo pacman -Rnsc <package_name>
```

**alacritty theme selector**</br>

```
paru -S alacritty-themes
alacritty-themes
```

##### wd-dict install

see [here](https://github.com/ChestnutHeng/Wudao-dict)

##### config static ip on linux

on arch ip can be set via ip command:

```bash
ip address add 192.168.10.110/24 dev wlan0
```

xxx.xxx.xxx.xxx/xx 其中 ip 地址最后的 24 代表的含义是 24 个连续的 1,也就是 10 进制的 255.255.255,也就是说最后剩下 8 位 2 进制的可用地址，换算成 10 进制就是 0-254.最后可有/24 得出此接口上的子网掩吗是 255.255.255.0.此种表示掩吗的写法叫做 CIDR 表示法。

check if ip is changed:
`ip link`

**set the dns server**</br>
nvim /etc/resolv.conf</br>

> ##dns configration</br>
> nameserver xxx.xxx.xxx.xxx

#### Editing shell cmd with $EDITOR

\<c-x>\<c-e> can edit the current shell command

显示命令类型</br>
type -a ping

#### set the display resolution

```bash
xrandr -q
xrandr --output eDP-1 --mode 1920x1080 --rate 60.00
xrandr --listmonitors
```

#### arch 安装中文字体

sudo pacman -S wqy-microhei ttf-nerd-fonts-symbols

##### 使用清华源替换官方 aur 地址

`yay --aururl https://aur.tuna.tsinghua.edu.cn" --save`

修改后的配置文件位于~/.config/yay/config.json

**使用下面的命令可以查看 yay 的配置文件** :

```bash
yay -P -g
```

**查看已安装的软件包信息**  
`yay -Ps`

ls ~/Downloads/suckless/\*/config.h

name=hello
为变量"name"赋值
name = hello
执行"name"命令 参数是 "="和"hello"
变量值的扩展($var)要用双引号包裹，而字符串的引用一般用''

#### set LANG enviroment

edit /etc/locale.conf:

> #LANG=en_US.UTF-8 #can be comment with '#'  
> LANG=zh_CN.UTF-8 #标准输出也会变成中文，debug 不方便，不推荐  
> LC_TIME=zh_CN.UTF-8 #只修改时间格式

#### xmodmap 修改键位绑定

把右 Alt 键作为 Mod4（Win 键）使用

当把 Mod4（Win 键）作为 MODKEY 时，你可能希望右 Alt 键也可以作为 Mod4，这样就两个手都可以按到了

首先，找到按键对应的键码,并记录下来：

xmodmap -pke | grep Alt
xmodmap -pke | grep Super

然后只需要在启动脚本（比如 ~/.xinitrc）添加如下内容, 把 113 换成之前 xmodmap 的结果：

```
xmodmap -e "keycode 64 = Super_L" # reassign Alt_R to Super_L
xmodmap -e "remove mod1 = Super_L" # make sure X keeps it out of the mod1 group
xmodmap -e "keycode 133 = Alt_L"
xmodmap -e "remove mod4 = Alt_L"
```

#### pacman 备份和恢复已安装软件包

定期备份软件包是个好习惯。万一系统出了大问题，需要重装，就可以利用备份的软件包恢复到原先的系统。

1. 生成系统上安装的非本地（即从官方仓库获取的）软件包列表：

```
$ comm -23 <(pacman -Qeq|sort) <(pacman -Qmq|sort) > pkglist
```

2. 把生成的 pkglist 存储在一个安全的地方，比如 U 盘，或者 gist.github.com、evernote、dropbox 之类的文本储存网站。

今后重装系统时，把 pkglist 复制到新系统。

3. 使用如下命令安装所有软件包：

```
pacman -S $(< pkglist)
```

#### shell 脚本中 echo 显示内容带颜色

shell 脚本中 echo 显示内容带颜色显示,echo 显示带颜色，需要使用参数-e  
格式如下：

`echo -e "\033[字背景颜色；文字颜色m字符串\033[0m" `

例如：

> echo -e "\033[41;36m something here \033[0m"

#### 显示当前正在运行的 shell 类型

```
echo $0
```

#### use terminus font on tty

install terminus:

```
sudo pacman -S terminus-font
```

edit _/etc/vconsole.conf:_  
FONT=ter-932n.psf.gz

#### sed 直接修改文件

`sed -i 's/111/aaa' example.txt`

#### bash 批量重命名

假如我们现在有一堆 .txt 文件，我们想将它们的后缀改成 .cpp。先来看完整的代码：

```bash
#!/bin/bash
for name in $(ls *.txt)
do
    mv $name ${name%.txt}.cpp
done
```

#### echo ssid connected

```
iwctl station wlan0 show \
| grep -i network | sed 's/Connected network/SSID:/'
```

#### 逐行读取的区别(shell)

说明：
假定有个名为 file 的文本文件.

```
$ cat file
aaaa
bbbb
cccc dddd
```

```
$ cat file | while read line; do echo $line; done
aaaa
bbbb
cccc dddd
```

```
for line in $(<file); do echo $line; done
aaaa
bbbb
cccc
dddd
```

**区别**:for 以空格作为分割符，while 以换行作为分割符.

#### youtube-dl 下载视频为 mp3

youtube-dl -x --audio-format mp3 'url'

#### xargs usage

在 linux 中许多命令只能支持直接在命令后输入参数，只有少部分命令支持从 stdin 作为参数，而这时候 xargs 命令就派上用场了.  
_xargs 命令最重要的作用就是将标准输入作为 linux 命令的输入_

_interactive find:_

```
xargs -L 1 find -name
```

上面命令指定了每一行（-L 1）作为命令行参数，分别运行一次命令（find -name）。
xargs -n 2 find -name
上面命令指定了每一项（-n 2）作为命令行参数(默认以空格分割)，分别运行一次命令（find -name）。

```
cat test.txt | xargs -I line sh -c 'echo line;mkdir line'
```

解释:从文件读取每一行，xargs 转换为 sh 命令的参数，执行一次 echo 和一次 mkdir.

```
echo "banana:apple:orange" | xargs -d: -n1
banana
apple
orange
```

#### Install packages from a text file

```
pacman -S $(cat /tmp/pack1.txt)
```

```
cat /tmp/pack1.txt | xargs pacman -S
```

```
for pack in `cat /tmp/pack1.txt` ; do apt -y install $pack; done
```

#### cp arguments

-n do not overwrite
-v explain what is being done
-L follow the symbolic links

#### show and execable cmd's info

```
type -a rm
file $(which ping)
```

#### crontab 定时任务

\*/2 \* \* \* \* date >> ~/date.log
min hour date month day-of-week

#### tmux manaual

rename a session in shell:

```
tmux rename-session -t oldname newname
```

concepts:  
session,window,panel

rename session c-b $

**panel control:**  
create a new panel(vertical) c-b %  
switch the pane c-b o  
kill a panel c-b x  
maximumize panel c-b z

**windows control:**  
create new window c-b c  
kill current win c-b &  
next window c-b n  
previous window c-b p  
rename window's name c-b ,  
switch the window in a list c-b w

**sessions control**  
switch the session in a list c-b s  
detach the current session and exit tmux c-b d  
rename session c-b $

**run tmux with a exist session:**

```
tmux att -t session-name
```

**tmux plugins manager (tpm)**

_Installation_

Requirements: tmux version 1.9 (or higher), git, bash.

```
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

put this at the bottom of ~/.tmux.conf

> # List of plugins
>
> set -g @plugin 'tmux-plugins/tpm'
> set -g @plugin 'tmux-plugins/tmux-sensible'
>
> \# Other examples:
>
> \# set -g @plugin 'github_username/plugin_name'
>
> \# set -g @plugin 'github_username/plugin_name#branch'
>
> \# set -g @plugin 'git@github.com:user/plugin'
>
> \# set -g @plugin 'git@bitbucket.com:user/plugin'
>
> \# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
>
> run '~/.tmux/plugins/tpm/tpm'

#### systemd 电源控制

nvim /etc/systemd/logind.conf:

```
[Login]
#HandlePowerKey=ignore
#HandleLidSwitch=ignore
```

uncomment the \# line above
**for more info,search 电源管理 systemd at arch wiki**

#### ssh 免密码登陆

原理

步骤  
generate a keypair on local :

```
ssh-keygen -t rsa
```

#scp ~/.ssh/id_rsa.pub user@remote_host:

```
ssh-copy-id user@remote_host
```

the ssh public key's path(remote_host):  
~/.ssh/authorized_keys

#### kill and pkill

kill multi process with regex:(pkill is used to do this)

```
pkill '^ssh$'
```

```
killall -9 firefox
```

show the pid of porcess name
ps aux | grep ssh

head -n 10 /etc/passwd | tail -n 5
tail -f /var/log/nginx/access.log

#### how to read man page

[ ] 表示可选
| 表示二选一
大写字母 表示需要被替换(类似变量名)
小写字母 表示具体的字符

#### 更改电源行为(systemd)

systemd 可以控制笔记开合盖,按下电源键,休眠键盘等一系列行为.  
若要更改电源行为模式,更改 /etc/systemd/logind.conf,  
更多请查阅 [systemd-archwiki](<https://wiki.archlinux.org/title/Systemd_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)>) 中的电源管理章节.
