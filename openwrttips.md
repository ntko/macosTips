opwnwrt添加usb和samba支持

https://openwrt.org/docs/guide-user/services/nas/usb-storage-samba-webinterface

opkg update

opkg list-installed | grep usb

opkg install kmod-usb-storage

opkg install kmod-usb2

opkg install kmod-usb-storage-uas

opkg install block-mount

opkg list | grep ntfs //在可用安装列表中查找

opkg install kmod-fs-ext4

opkg install kmod-fs-exfat

opkg install kmod-fs-ntfs


opkg install ntfs-3g

opkg install  kmod-usb-ohci

opkg install kmod-nls-cp437

opkg install kmod-nls-iso8859-1

opkg install ntfs-3g



opkg install usbutils

lsusb -t

opkg list | grep samba3

opkg install samba36-server

opkg install luci-app-samba



vim /etc/samba/smb.conf

\#invalid users = root //comment this

system->Mount Points->下方的Mount Points，Edit->Advanced Setting FileSystem:ntfs-3g 重点 Mount Options: nls=utf8  常规设置 Enable。保存应用。

services->网络共享->共享用户->root 权限0777






opkg install luci-i18n-samba-zh-cnopkg list-upgradable | cut -f 1 -d ' ' | xargs opkg upgrade


