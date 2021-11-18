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
        * [使用清华源替换官方 aur 地址](#使用清华源替换官方-aur-地址)
    * [set LANG enviroment](#set-lang-enviroment)
    * [xmodmap 修改键位绑定](#xmodmap-修改键位绑定)
* [pacman 备份和恢复已安装软件包](#pacman-备份和恢复已安装软件包)

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

sudo pacman -S adobe-source-code-pro-fonts

#### set goproxy (installing yay time out)

export GOPROXY=https://goproxy.io

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

To solve it, simply run `pip install --user autopep8`  
or if you want it globally:  
`sudo pip install autopep8`

#### install samba server && configration

安装 软件包 samba。  
Samba 服务的配置文件是 /etc/samba/smb.conf，smb.conf(5)提供了详细的文档。  
samba 软件包没有提供此文件，启动 smb.service 前需要先创建这个文件。从 这里 可以获取到示例文件。  
从上面获取的默认配置文件里把日志 log file 设置到一个不能写的地方, 这会引起错误。下面的办法可以解决这个问题:

#### ag usage (from tldr)

- Find files containing "foo", and print the line matches in context:
  ag foo

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

make sure you have **paru** (aur helper)

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

<c-x><c-e> can edit the current shell command

显示命令类型</br>
type -a ping

#### set the display resolution

```bash
xrandr -q
xrandr --output eDP-1 --mode 1920x1080 --rate 60.00
xrandr --listmonitors
```

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

### pacman 备份和恢复已安装软件包

定期备份软件包是个好习惯。万一系统出了大问题，需要重装，就可以利用备份的软件包恢复到原先的系统。

    第一步，生成系统上安装的非本地（即从官方仓库获取的）软件包列表：

```
$ comm -23 <(pacman -Qeq|sort) <(pacman -Qmq|sort) > pkglist
```

    把生成的pkglist存储在一个安全的地方，比如U盘，或者gist.github.com、evernote、dropbox之类的文本储存网站。

    今后重装系统时，把pkglist复制到新系统。

使用如下命令安装所有软件包：

```
pacman -S $(< pkglist)
```
