title:  "herbstluftwm安装"
date:   2016-08-20 22:34:44 +0800
comments: true
categories:
- ArchLinux安装
tags:
 - Linux
 - Herbstluftwm
---



## herbstluftwm安装

* 安装herbstluftwm
```
yaourt -S herbstluftwm-git
```

* 在.xinitrc中添加
```
exec herbstluftwm
```

 **确保只有一个exec**

```
mkdir -p ~/.config/herbstluftwm
cp /etc/xdg/herbstluftwm/autostart ~/.config/herbstluftwm/  ##复制配置文件
```

* 建议将autostart中的Mod1 改为Mod4。

 **注意：Mod1是Alt键，Mod4是Meta（或者叫win，再或者叫Super）键，因为alt键可能被很多程序使用，例如irssi，ff。当然也可以更换为其他按键。**
* 在24行中将xterm改为你自己使用的终端
* startx 进入herbstluftwm

## herbstluftwm常用快捷键

* 常用快捷键一览

按键|功能
----|----
Mod+o|横向分割frame
Mod+u|纵向分割frame
Mod+r|删除frame
Mod+h/j/k/l|移动focus
Mod+Shift+h/j/k/l|移动窗口
Mod+数字键|选择tags
Mod+Enter|打开终端
Mod+Shift+r|重新载入配置
Mod+Shift+q|退出herbstluftwm
Mod+f|窗口全屏

## 添加屏幕顶端的panel
* 安装dzen2
```
sudo pacman -S dzen2
```

**按Mod+Shift+r重新加载配置，顶端会出现panel**

```
cp /etc/xdg/herbstluftwm/panel.sh ~/.config/herbstluftwm/  ##复制配置文件
```

## 添加dmenu启动器

* 安装dmenu
```
sudo pacman -S dmenu
```

* 修改autostart文件，添加：
```
hc keybind $Mod-F2 spawn dmenu_run -b
```

**重载后按Mod+F2就可以使用dmenu了。**

## 添加壁纸

* 安装feh
```
sudo pacman -S feh
```

* 在autostart最后一行添加：
```
feh --bg-scale 背景图片路径   ##添加壁纸
fcitx                       ##添加输入法
```

## herbstluftwm截图
<figure>
  <a href="http://ogdmnptnx.bkt.clouddn.com/herbstluftwm.png"><img src="http://ogdmnptnx.bkt.clouddn.com/herbstluftwm.png"></a>
</figure>
