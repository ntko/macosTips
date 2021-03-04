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

opkg install usbutils

lsusb -t

opkg list | grep samba3

opkg install samba36-server

opkg install luci-app-samba

opkg install luci-i18n-samba-zh-cnopkg list-upgradable | cut -f 1 -d ' ' | xargs opkg upgrade


