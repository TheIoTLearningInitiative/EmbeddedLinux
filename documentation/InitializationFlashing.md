Flashing
==

- [Flasheable Image](https://seven.centos.org/2015/08/a-flashable-centos-image-for-the-intel-edison/)

```sh
dfu-util -d 8087:0a99 -a rootfs -D ~/projects/edison/edison-image-centos.ext4
```
