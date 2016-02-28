Yocto
==

> It's not an embedded Linux distribution – it creates a custom one for you. The Yocto Project is an open source collaboration project that provides templates, tools and methods to help you create custom Linux-based systems for embedded products regardless of the hardware architecture. It was founded in 2010 as a collaboration among many hardware manufacturers, open-source operating systems vendors, and electronics companies to bring some order to the chaos of embedded Linux development.

> The Yocto Project is a Linux Foundation workgroup whose goal is to produce tools and processes that will enable the creation of Linux distributions for embedded software that are independent of the underlying architecture of the embedded software itself.

## Links

- [Yocto Project Homepage](https://www.yoctoproject.org/)
- [Yocto Project Quick Start Guide](http://www.yoctoproject.org/docs/2.0/yocto-project-qs/yocto-project-qs.html)
- [Yocto Developer Manual](http://www.yoctoproject.org/docs/1.6.1/dev-manual/dev-manual.html)
- [Yocto Kernel Developer Manual](http://www.yoctoproject.org/docs/1.6.1/kernel-dev/kernel-dev.html)
- [Yocto Project and Embedded OS Webinar](http://www.intel.com/content/www/us/en/education/university/galileo-university-curricula/yocto-project-and-embedded-os-webinar-replay.html#)
- [Yocto Manage a Private Opkg Repository](http://www.jumpnowtek.com/yocto/Managing-a-private-opkg-repository.html)
- [Code Project Adding 3rd Party Components to Yocto/OpenEmbedded Linux](http://www.codeproject.com/Articles/774826/Adding-rd-party-components-to-Yocto-OpenEmbedded-L)

## Building Yocto

Let's understand what it means to work with Yocto Project by building images for QEMU and Minnowboard MAX.

## Qemu Image

```sh
    user@host:~# apt-get install gawk wget git-core diffstat unzip texinfo build-essential chrpath
    user@host:~# apt-get install qemu
    user@host:~$ mkdir source
    user@host:~$ cd source
    user@host:~$ git clone git://git.yoctoproject.org/poky --branch fido
    user@host:~$ source poky/oe-init-build-env yocto-x86-minimal
    user@host:~$ bitbake core-image-minimal
    user@host:~$ bitbake core-image-full-cmdline-x86
    user@host:~$ bitbake core-image-sato-sdk
    user@host:~$ runqemu qemux86
```
### Minnowboard Image

```sh
    user@host:~# apt-get install gawk wget git-core diffstat unzip texinfo build-essential chrpath
    user@host:~$ mkdir source
    user@host:~$ cd source
    user@host:~$ git clone -b fido git://git.yoctoproject.org/poky
    user@host:~$ cd poky
    user@host:~$ git clone -b fido git://git.yoctoproject.org/meta-intel
    user@host:~$ source oe-init-build-env yocto-x86-minnowmax
    user@host:~$ bitbake-layers add-layer "$HOME/source/poky/meta-intel"
    user@host:~$ echo 'MACHINE = "intel-corei7-64"' >> conf/local.conf
    user@host:~$ bitbake core-image-minimal
    user@host:~$ ls
    bitbake.lock  cache  conf  downloads  sstate-cache  tmp
    user@host:~$ ls tmp/deploy/images/intel-corei7-64/
    ...
    core-image-minimal-intel-corei7-64.hddimg
```

##### Development Workstation, Minnowboard MAX Kernel Compilation

```
    user@host:~$ bitbake virtual/kernel -c menuconfig
    user@host:~$ bitbake virtual/kernel -c configure -f -v
```

##### Development Workstation, Minnowboard MAX Flashing

```
    user@host:~$ sudo $HOME/source/poky/scripts/contrib/mkefidisk.sh HOST_DEVICE \
    tmp/deploy/images/intel-corei7-64/core-image-minimal-intel-corei7-64.hddimg \
    TARGET_DEVICE
```

#### Links

- [Yocto Project @ Minnowboard MAX](http://wiki.minnowboard.org/Yocto_Project)

## SandBox

ToDo Important Topics To Cover

- Example Project
- Adding Recipes to the Build System
- Adding New Recipes to the Build System
- Build an Example Package based on a Git Repository Commit
- Build an example package based on a Remote Source Archive
- Build an example package based on a Local Source Archive
