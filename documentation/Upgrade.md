Flashing
==

## DFU-Util
http://dfu-util.sourceforge.net/

- [Flasheable Image](https://seven.centos.org/2015/08/a-flashable-centos-image-for-the-intel-edison/)

```sh
xe1gyq@jessie:~$ dfu-util -d 8087:0a99 -a rootfs -D ~/projects/edison/edison-image-centos.ext4
```
