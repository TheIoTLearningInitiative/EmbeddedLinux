Upgrade
==

## DFU-Util

> dfu-util is a host side implementation of the DFU 1.0 and DFU 1.1 specifications of the USB forum. DFU is intended to download and upload firmware to/from devices connected over USB. It ranges from small devices like micro-controller boards to mobile phones. Using dfu-util you can download firmware to your DFU-enabled device or upload firmware from it. [Homepage](http://dfu-util.sourceforge.net/)

- [Flasheable Image](https://seven.centos.org/2015/08/a-flashable-centos-image-for-the-intel-edison/)

```sh
xe1gyq@jessie:~$ dfu-util -d 8087:0a99 -a rootfs -D ~/projects/edison/edison-image-centos.ext4
```
