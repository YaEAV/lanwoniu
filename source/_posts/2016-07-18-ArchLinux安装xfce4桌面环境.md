title:  "Arch Linux安装xfce4"
date:   2016-07-18 16:42:30 +0800
comments: true
categories:
- Linux
tags:
- Linux
- Xfce4

---


<!-- more -->


## 安装X窗口系统

* X 窗口系统（X11 / X）是诸多桌面环境的基础。
```
pacman -S xorg-server xorg-server-utils    # 安装 Xorg Server
pacman -S xf86-input-synaptics             # 可选，触摸板支持
pacman -S ttf-dejavu wqy-microhei          # 可选，Dejavu 与文泉驿 - 微米黑字体
```

## 安装xfce4桌面
```
pacman -S xfce4
pacman -S xfce4-goodies # 可选，包含一些小工具
```

## 启动管理
* 以startx为例
```
pacman -S xorg-xinit
cp /etc/X11/xinit/xinitrc ~/.xinitrc # 将配置文件复制到～/目录里
```
* 编辑.xinitrc
```
exec startxfce4    # 添加在～/.xinitrc
startx             # 启动桌面
```

* [其他管理器](https://wiki.archlinux.org/index.php/Window_manager)

## 安装中文输入法fcitx
* 安装fcitx
```
pacman -S fcitx-im fcitx-configtool
```

* 配置：
```
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS="@im=fcitx"
```

**添加在exec前**

* 添加输入法
```
fcitx-configtool
```

* 添加其他输入法
```
pacman -S <输入法引擎>
```

* 官方仓库提供的 fcitx 输入法引擎：
```
fcitx pinyin                                    # 拼音
fcitx-cloudpinyin
fcitx-googlepinyin                        #google拼音
fcitx-libpinyin
fcitx-sunpinyin
$ pacman -Ssq fcitx zhengma    # 五笔、郑码、仓颉
fcitx-table-extra
```

## 安装AUR软件仓库

* 将源添加到/etc/pacman.conf

 * 源1：
```
[archlinuxfr]
SigLevel = Never
Server = http://repo.archlinux.fr/$arch
```

  *  源2（Arch Linux CN 友情提供）：
```
[archlinuxcn]
SigLevel = Never
Server = http://repo.archlinuxcn.org/$arch
```

* 安装yaourt
```
pacman -Sy base-devel yaourt
```

* 使用方法同pacaman

## xfce4截图
<figure>
	<a href="http://ogdmnptnx.bkt.clouddn.com/xfce4-desktop.png"><img src="http://ogdmnptnx.bkt.clouddn.com/xfce4-desktop.png"></a>
</figure>
