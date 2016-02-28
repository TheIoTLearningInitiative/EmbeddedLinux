# Yocto

Yocto Customization
==


## Building Yocto

Let's understand what it means to work with Yocto Project by building images for QEMU and Minnowboard MAX.

### Development Workstation, Qemu Image Compilaton

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
### Development Workstation, Minnowboard Image Compilaton

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

#### Development Workstation, Minnowboard MAX Kernel Compilation

```
    user@host:~$ bitbake virtual/kernel -c menuconfig
    user@host:~$ bitbake virtual/kernel -c configure -f -v
```

#### Development Workstation, Minnowboard MAX Flashing

```
    user@host:~$ sudo $HOME/source/poky/scripts/contrib/mkefidisk.sh HOST_DEVICE \
    tmp/deploy/images/intel-corei7-64/core-image-minimal-intel-corei7-64.hddimg \
    TARGET_DEVICE
```

- [Yocto Project @ Minnowboard MAX](http://wiki.minnowboard.org/Yocto_Project)

## Links

- [Code Project Adding 3rd Party Components to Yocto/OpenEmbedded Linux](http://www.codeproject.com/Articles/774826/Adding-rd-party-components-to-Yocto-OpenEmbedded-L)
 
## SandBox

ToDo Important Topics To Cover

- Example Project
- Adding Recipes to the Build System
- Adding New Recipes to the Build System
- Build an Example Package based on a Git Repository Commit
- Build an example package based on a Remote Source Archive
- Build an example package based on a Local Source Archive
