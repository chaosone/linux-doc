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

#### install archlinux(2020 new)
* connect network
```bash
iwctl
>>>device list
>>> station wlan0 scan
>>> station wlan0 connect [ssid]
>>> exit
ping www.baidu.com
``` 

* sync time from ntp server
timedatectl set-ntp true

* set the disk partition
use fdisk or cfdisk

* install base package on /mnt
```
pacstrap /mnt base linux linux-firmware
```
* change root
```bash
mkdir /mnt/efi
mount /dev/sdx1 /mnt/efi
mount /dev/sdx2 /mnt
arch-chroot /mnt
pacman -S iwd
then, run "pacman -S xxx" to install utilities you want
```

### localization 

* hosts & hostname

* set passwd for root
passwd

* install grub and gen the fstab
```bash
pacman -S grub efibootmgr
uname -a
grub install --target=x86_64-efi --efi-directory=/efi --bootloader-id=ArchLinux
grub-mkconfig -o /boot/grub/grub.cfg
```
#### install node & npm(nodejs package manager)
sudo pacman -S nodejs npm

#### pip使用国内镜像源
mkdir -p ~/.pip/pip.conf,edit it:
>>>
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
[install]
trusted-host = https://pypi.tuna.tsinghua.edu.cn
>>>
