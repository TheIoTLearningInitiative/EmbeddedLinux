# Compilation

> In computer programming, the translation of source code into object code by a compiler. [Wikipedia](https://en.wikipedia.org/wiki/Compilation)

- [Intel® Edison Board Support Package](https://software.intel.com/en-us/node/593590)
- [Yocto Linux Image build for Intel Edison – Simple and Easy](https://scratchbuffer.wordpress.com/2015/09/01/yocto-linux-image-build-for-intel-edison-simple-and-easy/)
- [Using Make for Easy Yocto Builds On Intel Edison](http://www.hackgnar.com/2016/01/using-make-for-easy-yocto-builds-on.html)
- [Manually Building Yocto Images for the Intel Edison Board from Source](http://www.hackgnar.com/2016/01/manually-building-yocto-images-for.html)
- [Farit Building Yocto Linux for Intel Edison](http://hobby.farit.ru/building-yocto-linux-for-intel-edison/)

## Host Development Dependencies

```sh
    user@host:~# apt-get install build-essential git diffstat gawk chrpath texinfo libtool gcc-multilib dfu-util screen u-boot-tools
```

## Board Support Package

### Download & Decompression

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



### Building via Make + Bitbake

```sh
    user@host:~$ tar xvf edison-src-ww25.5-15.tgz
    user@host:~$ cd edison-src
    user@host:~$ ls
    Makefile  meta-intel-edison
    user@host:~$ make setup
    user@host:~$ ls
    bbcache  Makefile  meta-arduino  meta-intel-edison  out  pub
    user@host:~$ cd out/linux64 || cd out/current
    user@host:~$ ls
    build  poky
    user@host:~$ source poky/oe-init-build-env
    user@host:~$ bitbake edison-image
    user@host:~$ ls tmp/deploy/images/edison
    bzImage
    bzImage--3.10.17+git0+6ad20f049a_c03195ed6e-r0-edison-20151220135703.bin
    bzImage--3.10.17+git0+6ad20f049a_c03195ed6e-r0-edison-20151220220030.bin
    bzImage-edison.bin
    edison-image-edison-20151220045929.hddimg
    edison-image-edison-20151220045929.rootfs.ext4
    edison-image-edison-20151220045929.rootfs.manifest
    edison-image-edison-20151220122444.hddimg
    edison-image-edison-20151220122444.rootfs.ext4
    edison-image-edison-20151220122444.rootfs.manifest
    edison-image-edison-20151220135703.hddimg
    edison-image-edison-20151220135703.rootfs.ext4
    edison-image-edison-20151220135703.rootfs.manifest
    edison-image-edison-20151220213828.hddimg
    edison-image-edison-20151220213828.rootfs.ext4
    edison-image-edison-20151220213828.rootfs.manifest
    edison-image-edison-20151220220030.hddimg
    edison-image-edison-20151220220030.rootfs.ext4
    edison-image-edison-20151220220030.rootfs.manifest
    edison-image-edison-20151220221248.hddimg
    edison-image-edison-20151220221248.rootfs.ext4
    edison-image-edison-20151220221248.rootfs.manifest
    edison-image-edison.ext4
    edison-image-edison.hddimg
    edison-image-edison.manifest
    modules--3.10.17+git0+6ad20f049a_c03195ed6e-r0-edison-20151220135703.tgz
    modules--3.10.17+git0+6ad20f049a_c03195ed6e-r0-edison-20151220220030.tgz
    modules-edison.tgz
    README_-_DO_NOT_DELETE_FILES_IN_THIS_DIRECTORY.txt
    u-boot.bin
    u-boot-edison-2014.04-1-r0.bin
    u-boot-edison-2014.04-1-r0.img
    u-boot-edison.bin
    u-boot-edison.img
    u-boot-envs
    u-boot.img
    user@host:~$ ls
    bitbake.lock  cache  conf  symbols  tmp  toFlash
    user@host:~$ ../../../meta-intel-edison/utils/flash/postBuild.sh .
    EDISON_ROOTFS_MB = 1536, IMAGE_SIZE_MB = 548
    1+0 records in
    1+0 records out
    ...
    Image Name:   Edison Updater script
    Created:      Sun Dec 20 16:22:46 2015
    Image Type:   PowerPC Linux Script (uncompressed)
    Data Size:    14683 Bytes = 14.34 kB = 0.01 MB
    Load Address: 00010000
    Entry Point:  00010000
    Contents:
       Image 0: 14675 Bytes = 14.33 kB = 0.01 MB
    **** Done ***
    Files ready to flash in ./toFlash/
    Run the flashall script there to start flashing.
    *************
    user@host:~$ ./toFlash/flashall.sh
    Using U-Boot target: edison-blankcdc
    Now waiting for dfu device 8087:0a99
    Please plug and reboot the board
```

### Building via Script

```sh
    user@host:~$ tar xvf edison-src-ww25.5-15.tgz
    user@host:~$ cd edison-src
    user@host:~$ pwd
    /home/xe1gyq/Projects/edison-src
    user@host:~$ ls
    Makefile  meta-intel-edison
    user@host:~$ mkdir bitbake_download_dir
    user@host:~$ mkdir bitbake_sstate_dir
    user@host:~$ ./meta-intel-edison/setup.sh --dl_dir=bitbake_download_dir --sstate_dir=bitbake_sstate_dir
    user@host:~$ source poky/oe-init-build-env
    user@host:~$ bitbake edison-image
    user@host:~$ ../meta-intel-edison/utils/flash/postBuild.sh .
    user@host:~$ build/toFlash/flashall.sh
    user@host:~$ build/toFlash/flashall.sh --keep-data
    user@host:~$ build/toFlash/flashall.sh --recovery
```

## Native SDK

> To cross-compile native applications for your image, you must generate an SDK containing a cross-compiler toolchain and sysroot. You can generate a full SDK for the Edison Development Board.

### Building via Make

```sh
    user@host:~$ make sdk
    user@host:~$ ls out/current/build/tmp/deploy/sdk/
    poky-edison-glibc-x86_64-edison-image-core2-32-toolchain-1.7.2.manifest
    poky-edison-glibc-x86_64-edison-image-core2-32-toolchain-1.7.2.sh
    user@host:~$ out/current/build/tmp/deploy/sdk/poky-edison-glibc-x86_64-edison-image-core2-32-toolchain-1.7.2.sh
```

### Building via BitBake

```sh
    user@host:~$ bitbake edison-image-c populate_sdk
    user@host:~$ ls tmp/deploy/sdk
    user@host:~$ poky-edison-eglibc-x86_64-edison-image-core2-32-toolchain-1.6.1.sh
```

## Packages

### Standard, Common

Review the content of "edison-image.bb" and add some extra packages

```sh
    user@host:~$ nano edison-src/meta-intel-edison/meta-intel-edison-distro/recipes-core/images/edison-image.bb
    IMAGE_INSTALL += “libpng”
    IMAGE_INSTALL += "opencv"
    IMAGE_INSTALL += "python-opencv"
    PACKAGE_EXCLUDE = "libpng"
```

### Third Party, Not Common, AX25

```sh
    user@host:~$ pwd
    edison-src/out/linux64/build
    user@host:~$ cd edison-src/out/current/poky
    user@host:~$ git clone https://github.com/hambedded-linux/meta-hamradio.git
    user@host:~$ nano edison-src/out/current/build/conf/bblayers.conf
    /home/xe1gyq/Projects/edison-src/out/linux64/poky/meta-hamradio
    user@host:~$ rm -rf /home/xe1gyq/Projects/edison-src/out/linux64/poky/meta-hamradio/recipes-kernel
    user@host:~$ nano meta-intel-edison/meta-intel-edison-distro/recipes-core/images/edison-image.bb
    IMAGE_INSTALL += “ax25-apps”
    IMAGE_INSTALL += “ax25-tools”
    IMAGE_INSTALL += “libax25”
    user@host:~$ make image
    user@host:~$ make flash
```
