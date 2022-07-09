# 概述
本文将教学linux系统的Manjaro kde发行版的安装、源配置、怎么下载想要的软件和美化系统。
# 目录
# 安装
## 1.准备材料：
+ u盘  
先移存u盘的东西，在制作启动盘的时候会清理盘内所有东西。
+ iso镜像  
[Manjaro官网](https://manjaro.org/)，选择对应版本。  
## 2.制作启动盘：
采用Rufus进行刻录，选择下载好的iso镜像，其他默认，完成退出即可。  
## 3.重启，用u盘启动，进入安装界面：    
设置中文，设置shanghai时区，分盘：  
swap类似windows的虚拟内存，efi用来检索系统
|文件系统|大小|标记|挂载点|
|:--:|:--:|:--:|:--:|
|linuxswap|根据RAM大小设置，如果是8g内存这里就是8g|无|/swap|
|AT32|300M|勾选/boot，有esp也勾选|/boot/efi|
|ext4|剩下全部|无|/|
# 配置  
## 1.基本指令：  
```
# 安装xxx  
pacman -S xxx 
# 安装最新xxx  
pacman -Sy xxx 
# 删除XXX（保留依赖的包）  
pacman -R XXX 
# 删除XXX以及其依赖的包  
pacman -Rs XXX 
# 安装自己下载的XXX包或者转换过的deb  
pacman -U XXX  
# 清理未安装的包文件XXX  
pacman -Sc XXX
```
## 2.配置源：  
### 2.1 pacman   
pacman是manjaro库管理工具，可以下载仓库的软件到本地。  
```
# 国外源慢，选择国内源，根据测速排序选择多个源，如果第一个源连接超时会自动会自动访问第二个
sudo pacman-mirrors -i -c China -m rank
```
### 2.2 添加AUR源
Manjaro由archLinux衍生，具有丰富AUR软件库。
```
# 打开conf配置
sudo vim /etc/pacman.conf
# 若无法打开，先下载vim，或者安装基础依赖包
sudo pacman -Sy vim
sudo pacman -S base-devel
# 末尾添加如下，shift+insert粘贴，采用的是清华镜像源
[archlinuxcn]
SigLevel = Optional TrustedOnly
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
# 安装密钥
sudo pacman -S archlinuxcn-keyring antergos-keyring
# 更新软件列表
sudo pacman -Syu
# 更新系统
sudo pacman -Syyu
```
### 2.3 yay   
yay是AUR库管理工具，可以下载仓库的软件到本地。
```
# 下载
sudo pacman -Sy yay
# 配置镜像
yay --aururl "https://aur.tuna.tsinghua.edu.cn" --save
```
### 2.4 下载软件方法   
方法一：去[archlinux官方库](https://wiki.archlinux.org/)找软件详细信息，并下载
![image](https://user-images.githubusercontent.com/75480958/178099440-554c1458-1ca1-4fe0-b678-b18bdd26ceb3.png)
安装命令有：  
1.pacman
sudo pacman -S 软件名
2.yay   
yay -s 软件名

方法二：在软件商店下载
记得启用AUR库支持，扩大软件搜索范围。   
进入软件商店，点击 右上角总览-首选项-第三方-启用AUR支持-检查更新
### 2.5 推荐软件
小企鹅输入法：fcitx
![image](https://user-images.githubusercontent.com/75480958/178099929-3f1142b0-d234-4e3c-913b-a1ec081093ac.png)

![alt 属性文本](https://user-images.githubusercontent.com/75480958/178099929-3f1142b0-d234-4e3c-913b-a1ec081093ac.png))





