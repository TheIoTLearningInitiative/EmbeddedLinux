Filesystem
==

- [](http://alextgalileo.altervista.org/blog/changing-partition-setup-edison/)

## File System Disk Space Customization

Under the host

```sh
    user@host:~$ nano edison-src/device-software/meta-edison-distro/recipes-bsp/u-boot/files/edison.env
    user@host:~$ nano edison-src/device-software/meta-edison/recipes-bsp/u-boot/files/edison.env
    user@host:~$ nano edison-src/meta-intel-edison/meta-intel-edison-bsp/recipes-bsp/u-boot/files/edison.env
    Rootfs’ size from 512MB to 1312MB
    user@host:~$ nano edison-src/meta-intel-edison/meta-intel-edison-distro/recipes-core/images/edison-image.bb
    rootfs 1312MB
    user@host:~$ /device-software/utils/flash/postBuild.sh
    user@host:~# apt-get install dfu-util
    user@host:~$ /build/toFlash/flashall.sh --recovery
    user@host:~$ /build/toFlash/flashall.sh
    user@host:~# screen /dev/ttyUSBX 115200
```