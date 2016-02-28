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

### Hands-On

```sh
 user@host:~$ wget http://downloadmirror.intel.com/25384/eng/edison-iotdk-image-280915.zip
```

## Intel® Edison Board Support Package Document

> This document is for software and system engineers who are building and customizing images, kernels, and native SDKs for the Intel® Edison Development Platform. Precompiled versions of the BSP are available on the Intel
website. Users who don’t want to modify the default images don’t need to read this document.

- [Intel® Edison Board Support Package](http://download.intel.com/support/edison/sb/edisonbsp_ug_331188005.pdf)
