Upgrade
==

## DFU-Util

> dfu-util is a host side implementation of the DFU 1.0 and DFU 1.1 specifications of the USB forum. DFU is intended to download and upload firmware to/from devices connected over USB. It ranges from small devices like micro-controller boards to mobile phones. Using dfu-util you can download firmware to your DFU-enabled device or upload firmware from it. [Homepage](http://dfu-util.sourceforge.net/)

- [SeeedStudio DFU-Util](http://www.seeedstudio.com/wiki/Dfu-util)
- [Flasheable Image](https://seven.centos.org/2015/08/a-flashable-centos-image-for-the-intel-edison/)

```sh
xe1gyq@jessie:~$ sudo dfu-util -l -d 8087:0a99
dfu-util 0.8

Copyright 2005-2009 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2014 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Please report bugs to dfu-util@lists.gnumonks.org

Found DFU: [8087:0a99] ver=9999, devnum=14, cfg=1, intf=0, alt=11, name="initrd", serial="UNKNOWN"
Found DFU: [8087:0a99] ver=9999, devnum=14, cfg=1, intf=0, alt=10, name="vmlinuz", serial="UNKNOWN"
Found DFU: [8087:0a99] ver=9999, devnum=14, cfg=1, intf=0, alt=9, name="home", serial="UNKNOWN"
Found DFU: [8087:0a99] ver=9999, devnum=14, cfg=1, intf=0, alt=8, name="update", serial="UNKNOWN"
Found DFU: [8087:0a99] ver=9999, devnum=14, cfg=1, intf=0, alt=7, name="rootfs", serial="UNKNOWN"
Found DFU: [8087:0a99] ver=9999, devnum=14, cfg=1, intf=0, alt=6, name="boot", serial="UNKNOWN"
Found DFU: [8087:0a99] ver=9999, devnum=14, cfg=1, intf=0, alt=5, name="u-boot-env1", serial="UNKNOWN"
Found DFU: [8087:0a99] ver=9999, devnum=14, cfg=1, intf=0, alt=4, name="u-boot1", serial="UNKNOWN"
Found DFU: [8087:0a99] ver=9999, devnum=14, cfg=1, intf=0, alt=3, name="u-boot-env0", serial="UNKNOWN"
Found DFU: [8087:0a99] ver=9999, devnum=14, cfg=1, intf=0, alt=2, name="u-boot0", serial="UNKNOWN"
Found DFU: [8087:0a99] ver=9999, devnum=14, cfg=1, intf=0, alt=1, name="ifwib00", serial="UNKNOWN"
Found DFU: [8087:0a99] ver=9999, devnum=14, cfg=1, intf=0, alt=0, name="ifwi00", serial="UNKNOWN"
```

```sh
xe1gyq@jessie:~$ dfu-util -d 8087:0a99 -a rootfs -D ~/projects/edison/edison-image-centos.ext4
```
