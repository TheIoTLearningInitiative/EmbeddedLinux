# Building

- [Yocto Project Linux Kernel Development Manual](http://www.yoctoproject.org/docs/latest/kernel-dev/kernel-dev.html)
- [Creating a Custom Linux Kernel for the Edison](http://shawnhymel.com/585/creating-a-custom-linux-kernel-for-the-edison/)
- [How to compile Intel Edison Linux Kernel](http://www.iduino.cc/index.php/2015/10/20/how-to-compile-intel-edison-linux-kernel/)

- [01 Org Intel Edison Linux Kernel](https://github.com/01org/edison-linux)
  - edison-3.19.5
  - edison-3.10.98
  - edison-3.10.17
- [meta-intel-edison-bsp/recipes-kernel/linux/linux-externalsrc.bb log](http://git.yoctoproject.org/cgit/cgit.cgi/meta-intel-edison/tree/meta-intel-edison-bsp/recipes-kernel/linux/linux-externalsrc.bb)
- [meta-intel-edison-bsp/recipes-kernel/linux/linux-externalsrc.bb log](http://git.yoctoproject.org/cgit/cgit.cgi/meta-intel-edison/log/meta-intel-edison-bsp/recipes-kernel/linux/linux-externalsrc.bb)

# Building via Make Detailed

```sh
    user@host:~$ ls
    bbcache  flash.log  Makefile  meta-arduino  meta-intel-edison  out  pub
```

```sh
    user@host:~$ cd out/current
    user@host:~$ ls
    build  poky
```

```sh
    user@host:~$ source poky/oe-init-build-env
    ### Shell environment set up for builds. ###
    
    You can now run 'bitbake <target>'
    
    Common targets are:
        core-image-minimal
        core-image-sato
        meta-toolchain
        adt-installer
        meta-ide-support
    
    You can also run generated qemu images with a command like 'runqemu qemux86'
```

# Fix Paho-Mqtt

[Problems compiling edison-src-ww25.5-15 using bitbake](https://communities.intel.com/thread/101849)

```sh
    user@host:~$ wget http://git.yoctoproject.org/cgit/cgit.cgi/meta-intel-iot-middleware/plain/recipes-connectivity/paho-mqtt/paho-mqtt_3.1.bb
    user@host:~$ mv paho-mqtt_3.1.bb file/to/paho-mqtt_3.1.bb
```

```sh
    user@host:~$ bitbake virtual/kernel -c menuconfig
    user@host:~$ bitbake virtual/kernel -c configure -f -v
    user@host:~$ bitbake edison-image
```

# Building via Make

```sh
    user@host:~$ pwd
    /home/xe1gyq/.../edison-src
    user@host:~$ cd out/current
    user@host:~$ source poky/oe-init-build-env
    user@host:~$ bitbake virtual/kernel -c menuconfig
    ...
    edison-src/out/linux64/build/tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux-edison-standard-build/Makefile
    ...
    user@host:~$ cp tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux-edison-standard-build/.config tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/defconfig 
    user@host:~$ cp tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux-edison-standard-build/.config tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux/arch/x86/configs/i386_edison_defconfig
    user@host:~$ bitbake virtual/kernel -c configure -f -v
    user@host:~$ cd ../../..
```

# Fix Paho-Mqtt

[Problems compiling edison-src-ww25.5-15 using bitbake](https://communities.intel.com/thread/101849)

```sh
    user@host:~$ wget http://git.yoctoproject.org/cgit/cgit.cgi/meta-intel-iot-middleware/plain/recipes-connectivity/paho-mqtt/paho-mqtt_3.1.bb
    user@host:~$ mv paho-mqtt_3.1.bb file/to/paho-mqtt_3.1.bb
```

```sh
    user@host:~$ make image
    user@host:~$ make flash
    edison-src/out/linux64/build/tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux-edison-standard-build/Makefile
```
# Building via BitBake

```sh
    user@host:~$ pwd
    /home/xe1gyq/.../edison-src
    user@host:~$ cd out/current
    user@host:~$ source poky/oe-init-build-env
    user@host:~$ bitbake virtual/kernel -c menuconfig
    ...
    edison-src/out/linux64/build/tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux-edison-standard-build/Makefile
    ...
    user@host:~$ cp tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux-edison-standard-build/.config tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/defconfig 
    user@host:~$ cp tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux-edison-standard-build/.config tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux/arch/x86/configs/i386_edison_defconfig
    user@host:~$ bitbake virtual/kernel -c configure -f -v
    user@host:~$ bitbake edison-image
```