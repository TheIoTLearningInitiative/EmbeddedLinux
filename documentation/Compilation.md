# Compilation

> In computer programming, the translation of source code into object code by a compiler. [Wikipedia](https://en.wikipedia.org/wiki/Compilation)

- [Intel® Edison Board Support Package](https://software.intel.com/en-us/node/593590)
- [Yocto Linux Image build for Intel Edison – Simple and Easy](https://scratchbuffer.wordpress.com/2015/09/01/yocto-linux-image-build-for-intel-edison-simple-and-easy/)
- [Using Make for Easy Yocto Builds On Intel Edison](http://www.hackgnar.com/2016/01/using-make-for-easy-yocto-builds-on.html)
- [Manually Building Yocto Images for the Intel Edison Board from Source](http://www.hackgnar.com/2016/01/manually-building-yocto-images-for.html)
- [Farit Building Yocto Linux for Intel Edison](http://hobby.farit.ru/building-yocto-linux-for-intel-edison/)

# Host Development Dependencies

```sh
    user@host:~# apt-get install build-essential git diffstat gawk chrpath texinfo libtool gcc-multilib dfu-util screen u-boot-tools
```

# Board Support Package

## Download & Decompression

Go to [Intel® Edison Board Software Downloads](https://software.intel.com/en-us/iot/hardware/edison/downloads)
and copy the link location for "Sources - Linux Sources Files" then download them

```sh
    user@host:~$ wget http://downloadmirror.intel.com/25028/eng/edison-src-ww25.5-15.tgz

    --2016-02-28 14:58:27-- http://downloadmirror.intel.com/25028/eng/edison-src-ww25.5-15.tgz
    Resolving downloadmirror.intel.com (downloadmirror.intel.com)... 23.216.208.166
    Connecting to downloadmirror.intel.com (downloadmirror.intel.com)|23.216.208.166|:80... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 6195269 (5.9M) [application/x-compressed]
    Saving to: ‘edison-src-ww25.5-15.tgz.1’
    
    edison-src-ww25.5-1 100%[=====================>]   5.91M   987KB/s   in 7.1s   
    
    2016-02-28 14:58:34 (857 KB/s) - ‘edison-src-ww25.5-15.tgz.1’ saved [6195269/6195269]
```

```sh
    user@host:~$ tar zxvf edison-src-ww25.5-15.tgz 
    edison-src/
    edison-src/Makefile
    edison-src/meta-intel-edison/
    edison-src/meta-intel-edison/README
    edison-src/meta-intel-edison/MAINTAINERS
    ...
    edison-src/meta-intel-edison/meta-intel-edison-bsp/recipes-kernel/linux/files/upstream_to_edison.patch
    edison-src/meta-intel-edison/meta-intel-edison-bsp/recipes-kernel/linux/files/defconfig
    edison-src/meta-intel-edison/meta-intel-edison-bsp/README.sources
```

```sh
    user@host:~$ ls
    Makefile  meta-intel-edison
```

```sh
    user@host:~$ ls meta-intel-edison/
    COPYING.MIT  meta-intel-arduino     meta-intel-edison-distro  setup.sh
    MAINTAINERS  meta-intel-edison-bsp  README                    utils
```
