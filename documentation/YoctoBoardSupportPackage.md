# Yocto Board Support Package

> In embedded systems, a board support package (BSP) is an implementation of specific support code (software) for a given (device motherboard) board that conforms to a given operating system. It is commonly built with a bootloader that contains the minimal device support to load the operating system and device drivers for all the devices on the board. [Wikipedia](https://en.wikipedia.org/wiki/Board_support_package)

## Intel Edison® Board Firmware Software Release

The Intel® Edison Board Support Package offers these features:

- Kernel image based on Linux kernel 3.10.17
- U-boot second stage bootloader
- Bluetooth and Wi-Fi connectivity
- Intel cloud connectivity middleware
- Many base Linux packages provided by the Yocto project

### Links

- [Search Downloads Intel® Edison](https://downloadcenter.intel.com/search?keyword=edison)
- [Intel® Edison Software Release 2.1](https://downloadcenter.intel.com/download/24910/Intel-Edison-Software-Release-2-1)
- [Intel® Edison Software Downloads](https://software.intel.com/en-us/iot/hardware/edison/downloads)

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

## Intel® Edison Board Support Package Document

> This document is for software and system engineers who are building and customizing images, kernels, and native SDKs for the Intel® Edison Development Platform. Precompiled versions of the BSP are available on the Intel
website. Users who don’t want to modify the default images don’t need to read this document.

- [Intel® Edison Board Support Package](http://download.intel.com/support/edison/sb/edisonbsp_ug_331188005.pdf)
