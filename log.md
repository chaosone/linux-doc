### install yay on arch

Before you begin, make sure you have the base-devel package group installed.

```bash
pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

### install linux brew

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

#### install archlinux(2020 new)

** - connect network **

```bash
iwctl
>>>device list
>>> station wlan0 scan
>>> station wlan0 connect [ssid]
>>> exit
ping www.baidu.com
```

- sync time from ntp server
  timedatectl set-ntp true

- set the disk partition
  use fdisk or cfdisk

- install base package on /mnt

```
pacstrap /mnt base linux linux-firmware
```

- change root

```bash
mkdir /mnt/efi
mount /dev/sdx1 /mnt/efi
mount /dev/sdx2 /mnt
arch-chroot /mnt
pacman -S iwd
then, run "pacman -S xxx" to install utilities you want
```

### localization

- hosts & hostname

- set passwd for root
  passwd

- install grub and gen the fstab

```bash
pacman -S grub efibootmgr
uname -a
grub install --target=x86_64-efi --efi-directory=/efi --bootloader-id=ArchLinux
grub-mkconfig -o /boot/grub/grub.cfg
```

#### install node & npm(nodejs package manager)

sudo pacman -S nodejs npm

#### pip install & configration

- pip 使用国内镜像源

mkdir -p ~/.pip/pip.conf,edit it:  
_pip.conf:_

> > > [global]
> > > index-url = https://pypi.tuna.tsinghua.edu.cn/simple > > > [install]  
> > > trusted-host = https://pypi.tuna.tsinghua.edu.cn

### install source-code-pro-fonts

sudo pacman -S adobe-source-code-pro-fonts

### set goproxy (installing yay time out)

export GOPROXY=https://goproxy.io

#### install ranger pluign

git clone https://github.com/alexanderjeurissen/ranger_devicons ~/.config/ranger/plugins/ranger_devicons
echo "default_linemode devicons" >> ~/.config/rc.conf

### alsamixer to control sound

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

#### ag usage(from tldr)

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

#### not enough swap space to hibernate

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
如果要删除或重置系统，删除 /etc/pacman.d/gnupg 目录并重新运行 pacman-key --init。通过 pacman-key --populate archlinux 重新添加默认密钥。如果 archlinux-keyring 不是最新的，需要在更新系统前先执行 pacman -S archlinux-keyring。

#### 用 whiskermenu 代替默认的 xfce4 开始菜单

whiskermenu 是一个弹出式菜单,可以搜索并启动应用程序.  
使用 `yay -s whiskermenu` 安装即可.
sudo pacman -Q | grep whisker
find the package name,then use **which** to search the path of whiskermenu
在开始菜单-settings-keyboard 中可以绑定一个快捷键用来启动 whiskermenu.

#### use swap file instead of swap space

`sudo dd if=/dev/zero of=/swapfile bs=1M count=6144 status=progress`
sudo chmod 600 /swapfile
sudo makeswap /swapfile
sudo swapon /swapfile
swapon -s

then append to following line to /etc/fstab:  
/swapfile none swap defaults 0 0
see also:  
https://wiki.archlinux.org/index.php/Swap#Swap_file
