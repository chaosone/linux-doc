### install archlinux(2020 new)

** - connect network **

```bash
iwctl
>>>device list
>>> station wlan0 scan
>>> station wlan0 connect [ssid]
>>> exit
ping www.baidu.com
```

- sync time from ntp server</br>
  timedatectl set-ntp true

- set the disk partition</br>
  use fdisk or cfdisk

- install base package on /mnt

```
pacstrap /mnt base linux linux-firmware
```

_if you wanna linux-lts kernel,type linux-lts instead linux._

- change root & mount filesystem.

```bash
mkdir /mnt/efi
mount /dev/sdx1 /mnt/efi
mount /dev/sdx2 /mnt
arch-chroot /mnt
pacman -S iwd
```

then, run `pacman -S xxx` to install utilities you want

- localization

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
