opwnwrt添加usb和samba支持

https://openwrt.org/docs/guide-user/services/nas/usb-storage-samba-webinterface

opkg update

opkg list-installed | grep usb

opkg install kmod-usb-storage

opkg install kmod-usb2

opkg install kmod-usb-storage-uas

opkg install kmod-usb-storage-extras
 
opkg install block-mount

opkg list | grep ntfs //在可用安装列表中查找

opkg install kmod-fs-ext4

opkg install kmod-fs-exfat

opkg install kmod-fs-ntfs

opkg install ntfs-3g

opkg install  kmod-usb-ohci

opkg install kmod-nls-cp437

opkg install kmod-nls-cp936

opkg install kmod-nls-iso8859-1

opkg install kmod-nls-utf8


opkg install usbutils

lsusb -t

opkg list | grep samba3


opkg install samba36-server
opkg install samba36-hotplug
opkg install samba36-net
opkg install luci-app-samba



vim /etc/samba/smb.conf

\#invalid users = root //comment this

system->Mount Points->下方的Mount Points，Edit->Advanced Setting FileSystem:ntfs-3g 重点 Mount Options: nls=utf8  常规设置 Enable。保存应用。

```
cat /etc/config/fstab 

config global
	option anon_swap '0'
	option auto_swap '1'
	option auto_mount '1'
	option delay_root '5'
	option check_fs '0'
	option anon_mount '1'

config mount
	option target '/mnt/sda1'
	option uuid 'AA06B37606B3425D'
	option enabled '1'
	option fstype 'ntfs-3g'
	option options 'nls=utf8'
```
```
block info
/dev/mtdblock3: UUID="692974698" VERSION="1" TYPE="ubi"
/dev/mtdblock5: UUID="1316725210" VERSION="1" TYPE="ubi"
/dev/ubiblock0_0: UUID="01c37662-5d8301ff-536c29f1-703fe831" VERSION="4.0" MOUNT="/rom" TYPE="squashfs"
/dev/ubi0_1: UUID="a31227c4-4356-46af-b3ac-ec9583147888" VERSION="w4r0" MOUNT="/overlay" TYPE="ubifs"
/dev/sda1: UUID="AA06B37606B3425D" LABEL="KINGSTON" MOUNT="/mnt/sda1" TYPE="ntfs"


```

smbpasswd -a root , and input SMB password twice.
cat /etc/samba/smbpasswd

services->网络共享->共享用户->root 权限0777

 opkg install luci-i18n-samba-zh-cn

service samba restart

dmesg //显示内核信息

opkg install luci-i18n-samba-zh-cnopkg list-upgradable | cut -f 1 -d ' ' | xargs opkg upgrade


