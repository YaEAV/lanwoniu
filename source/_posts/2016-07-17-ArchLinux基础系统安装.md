title:  "Arch Linux基础系统安装"
date:   2016-07-17 14:20:15 +0800
comments: true
categories:
- ArchLinux安装
tags:
- Linux
---

    Archlinux不是在图形界面进行安装的，因此对于新手来说安装很困难。也可以选择基于Arche的发行版manjaro安装简单开箱即用。
<!-- more -->

## 获取ArchISO

[ArchLinux下载地址](https://www.archlinux.org/download/)
**建议使用163的源下载**

## 制作安装盘
```
dd bs=4M if=< archlinux.iso的路径 > of=/dev/sdX && sync
```

**!!! 该命令将清空U盘，并导致U盘不可用。安装完系统后可格式化**

## 进入安装环境，查看是否开启UEFI
```
efivar -l
```

**若系统以UEFI模式启动会正确列出UEFI变量，后面的安装会根据启动方式分成两种情况。**

## 建立网络连接

  * 有线连接
```
  dhcpcd
```

  * 无线连接
```
 wifi-menu
```

  * ADSL 宽带连接
```
    pppoe-setup  # 配置
    pppoe-setup  # 连接
```

## 选择软件源
```
nano /etc/pacman.d/mirrorlist  #将需要的源移至第一行
pacman -Syy                                 #更新本地数据
```

 **大陆用户可以直接执行**

```
grep -A 1 'China' /etc/pacman.d/mirrorlist                                #查看中国大陆的镜像服务器
sed -i '/Score/{/China/!{n;s/^/#/}}' /etc/pacman.d/mirrorlist  #选择所有的中国大陆的镜像服务器
```

## 分区

* 分区基本要求：
  * 至少一个根分区（类型代码：8300）
* 特殊要求 ：
  * BIOS + GPT + Grub：BIOS 引导分区（类型代码：ef02；大小 ≥ 1 MiB）
  * UEFI：UEFI 系统分区（类型代码：ef00；大小 ≥ 256 MiB）
  * 系统休眠：交换分区（类型代码：8200；大小 ≥ 2×内存大小）
* 建议：
  * 若安装目标内存 ≤ 2GB，添加一个交换分区
  * 为 /home 分配一个分区
* 案例
  * BIOS<br>
  ![](http://ogdmnptnx.bkt.clouddn.com/BIOS.png)
  * UEFI<br>
  ![](http://ogdmnptnx.bkt.clouddn.com/UEFI.png)
* 分区
```
    lsblk #查看分区
```

* **通用分区工具：parted、cfdisk、sfdisk**
* **仅GPT：cgdisk、sgdisk**

## 创建系统文件(格式化)
```
mkfs.fat -F32 /dev/sda1      # 创建 FAT32 分区
mkfs.ext4 /dev/sda2           # 创建 ext4 分区
mkswap /dev/sda3             # 创建交换分区
swapon /dev/sda3              # 激活交换分区
mkfs.ext4 /dev/sda2           # 创建 ext4 分区
```
* **注意/dev/后面的分区要与自己的对应，上面是以UEFI分区为例**

## 挂载分区
```
mount /dev/sda2 /mnt                     # 挂载根目录
mkdir /mnt/home                             # 创建 /home 挂载点
mount /dev/sda4 /mnt/home         # 挂载 /home
mkdir -p /mnt/boot/EFI                   # 创建 UEFI 挂载点
mount /dev/sda1 /mnt/boot/EFI    # 挂载 UEFI 分区
```
* **同样以UEFI为例，注意要先挂载/目录**

## 安装基本系统
```
pacstrap -i /mnt base base-devel
```

## 配置fstab
```
genfstab -U <根目录挂载点> >> <根目录挂载点>/etc/fstab
cat <根目录挂载点>/etc/fstab
```

* 对于每一行的最后一部分 <pass> ，/ 分区应该为 1，其他分区为2,btrfs分区（无论是否为/分区)及swap分区的应该为 0
* 若发现错误，请直接对fstab进行修正，勿再次执行 genfstab

## 进入新系统
```
arch-chroot <根目录挂载点> /bin/bash
```

## 为root用户设置密码
```
passwd
```

## 网络配置

* 有线连接：
```
systemctl start dhcpcd       # 连接
systemctl enable dhcpcd   # 自动连接
```

* 无线连接：
```
pacman -S iw wpa_supplicant dialog
wifi-menu	# 连接
```

* ADSL宽带连接：
```
pacman -S rp-pppoe
pppoe-setup                  # 配置
systemctl start adsl       # 连接
systemctl enable adsl   #自动连接
```

## 安装引导器

* BIOS
```
pacman -S grub os-prober
grub-install --recheck /dev/<目标磁盘>
grub-mkconfig -o /boot/grub/grub.cfg
```

* UEFI
```
pacman -S dosfstools grub efibootmgr
grub-install --target=x86_64-efi --efi-directory=<EFI 分区挂载点> --bootloader-id=arch_grub --recheck
grub-mkconfig -o /boot/grub/grub.cfg
```

## 卸载分区并重启

```
exit                                    # 退回安装环境
umount -R < / 挂载点>    # 卸载新分区
reboot                               # 重启
```

* **!!! 记得移除安装介质**

## 用户管理

 **创建一个名为< 用户名 >的用户，指定登陆shell为bash，所属主用户组users，用户文件夹位于/home/< 用户名 >**

```
useradd -m -g users -s /bin/bash <用户名>
passwd <用户名>   # 设置密码
```

## 配置sudo
```
pacman -S sudo                          # 安装sudo
EDITOR=nano visudo                 # 配置sudo
%wheel ALL=(ALL) ALL               # 反注释（删去#）
gpasswd -a <用户名> wheel      # 将允许获取 root 权限的用户加入 wheel 用户组
sudo <命令>                               # 使用方法
```

## 设置Locale

* Locale 决定了软件使用的语言、书写习惯和字符集。
```
nano /etc/locale.gen                   # 反注释需要的 locale
locale-gen                             # 生成 locale
echo LANG=<locale>  > /etc/locale.conf # 设置默认 locale
```

* 简体中文用户可执行
```
sed -i '/zh_CN.UTF-8/{s/#//}' /etc/locale.gen; \
locale-gen; \
echo LANG=zh_CN.UTF-8  > /etc/locale.conf
```

## 设置时区

* 时区
```
ln -s /usr/share/zoneinfo/$(tzselect) /etc/localtime
```

* 中国大陆用户可执行：
```
ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

## 时间设置

* （推荐）UTC 时间：
```
hwclock --systohc --utc
```

* 本地时间:
```
hwclock --systohc --localtime
```

**注意：使用本地时间可能会引起某些不可修复的bug。**

## 主机名
```
echo <主机名> > /etc/hostname
nano /etc/hosts                # 将主机名填入
```

* 完成后像这样<br>
![](http://ogdmnptnx.bkt.clouddn.com/hostname.png)

* 快速填入
```
HOSTNAME='<主机名>'; echo $HOSTNAME > /etc/hostname; \
sed -i '/localhost/s/$/\t'"$HOSTNAME"'/g' /etc/hosts
```

## 声音管理
```
pacman -S alsa-utils
alsamixer
```

* 方向键选中 Master 和 PCM

* [M] 取消静音

## 安装显卡驱动

* 查看显卡型号
```
lspci | grep VGA
```

* 官方仓库提供的驱动包


  厂商|型号|开源|私有
  ----|----|----|----|---
  通用|    |xf86-video-vesa|
  Intel|   |xf86-video-intel|
  Nvidia|GeForce 7+|xf86-video-nouveau|nvidia
  Nvidia|GeForce 6/7|xf86-video-nouveau|nvidia-304xx
  AMD/ATI|   | xf86-video-ati

* 安装显卡驱动
```
pacman -S <驱动包>
```
