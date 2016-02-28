Building Blocks
==

```sh
    BBLAYERS ?= " \
      /home/abraham/Projects/RealTime/v25/edison-src/out/linux64/poky/meta \
      /home/abraham/Projects/RealTime/v25/edison-src/out/linux64/poky/meta-yocto \
      /home/abraham/Projects/RealTime/v25/edison-src/out/linux64/poky/meta-yocto-bsp \
      /home/abraham/Projects/RealTime/v25/edison-src/meta-intel-edison/meta-intel-edison-bsp \
      /home/abraham/Projects/RealTime/v25/edison-src/meta-intel-edison/meta-intel-edison-distro \
      /home/abraham/Projects/RealTime/v25/edison-src/out/linux64/poky/meta-intel-iot-middleware \
      /home/abraham/Projects/RealTime/v25/edison-src/meta-intel-edison/meta-intel-arduino \
      /home/abraham/Projects/RealTime/v25/edison-src/meta-arduino \
      \
      "
    BBLAYERS_NON_REMOVABLE ?= " \
      /home/abraham/Projects/RealTime/v25/edison-src/out/linux64/poky/meta \
      /home/abraham/Projects/RealTime/v25/edison-src/out/linux64/poky/meta-yocto \
      "
```

### poky/meta

> Yocto Metadata Layers

It includes:

```sh
    recipes-bsp          - Anything with links to specific hardware or hardware configuration information
    recipes-connectivity - Libraries and applications related to communication with other devices
    recipes-core         - What's needed to build a basic working Linux image including commonly used dependencies
    recipes-devtools     - Tools primarily used by the build system (but can also be used on targets)
    recipes-extended     - Applications which whilst not essential add features compared to the alternatives in
                           core. May be needed for full tool functionality or LSB compliance.
    recipes-gnome        - All things related to the GTK+ application framework
    recipes-graphics     - X and other graphically related system libraries
    recipes-kernel       - The kernel and generic applications/libraries with strong kernel dependencies
    recipes-lsb4         - Recipes added for the sole purpose of supporting the Linux Standard Base (LSB) 4.x
    recipes-multimedia   - Codecs and support utilties for audio, images and video
    recipes-rt           - Provides package and image recipes for using and testing the PREEMPT_RT kernel
    recipes-qt           - All things related to the Qt application framework
    recipes-sato         - The Sato demo/reference UI/UX, its associated apps and configuration
    recipes-support      - Recipes used by other recipes but that are not directly included in images
```

### meta-yocto

> Yocto Project integration layers (Poky distro configuration, reference hardware BSPs) 
> Poky reference distribution for the Yocto Project 

It includes:

- meta-yocto-bsp
- meta-yocto
- scripts

Links

- [Yocto meta-yocto](http://git.yoctoproject.org/cgit/cgit.cgi/meta-yocto)
- [OpenEmbedded meta-yocto](http://layers.openembedded.org/layerindex/branch/master/layer/meta-yocto/)

### meta-yocto-bsp 

> BSP layer for Yocto Project reference hardware

- [OpenEmbedded meta-yocto-bsp](http://layers.openembedded.org/layerindex/branch/master/layer/meta-yocto-bsp/)

### meta-intel-edison-bsp

> BSP layer for the Intel Edison module. 

It includes:

- __bcm43340-bt__ Broadcom Bluetooth fw files and patch utility
- __bcm43340-fw__ Firmware files for use with Linux kernel
- __bcm43340-mod__ Broadcom wifi driver for the 43340
- __linux-externalsrc__ Yocto Kernel
- __mcu-fw-bin__ This is edison mcu fw binary.
- __mcu-fw-load__ This is intel mcu app download daemon.
- __pwr-button-handler__ Daemon listening to Edison PWR long button press, and starting OOBE service when it happens
- __sst-fw-bin__ This is edison sst fw binary.
- __u-boot Universal__ Boot Loader for embedded devices
- __u-boot-fw-utils__ U-boot bootloader fw_printenv/setenv utils
- __u-boot-tools__ U-boot bootloader mkimage tool

Links

- [OpenEmbedded meta-intel-edison-bsp](http://layers.openembedded.org/layerindex/branch/master/layer/meta-intel-edison-bsp/)

### meta-intel-edison-distro

> This is the distro layer used to build official Intel Edison images.

- [OpenEmbedded meta-intel-edison-bsp](http://layers.openembedded.org/layerindex/branch/master/layer/meta-intel-edison-distro/)

### meta-intel-iot-middleware

> Shared middleware recipes for Intel IoT platforms

- recipes-connectivity
- recipes-devtools
- recipes-extended

- [Yocto meta-intel-iot-middleware](http://git.yoctoproject.org/cgit/cgit.cgi/meta-intel-iot-middleware)

## Links

- [Layer for the Intel Edison Development Platform](http://git.yoctoproject.org/cgit/cgit.cgi/meta-intel-edison/tree/)
- [Intel Galileo platform support](http://git.yoctoproject.org/cgit/cgit.cgi/meta-intel-galileo/tree/)
- [Intel Galileo Rebuild](http://www.embarcados.com.br/galileo-yocto/)
