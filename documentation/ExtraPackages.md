# Extra Packages

## Standard, Common

Review the content of "edison-image.bb" and add some extra packages

```sh
    user@host:~$ nano edison-src/meta-intel-edison/meta-intel-edison-distro/recipes-core/images/edison-image.bb
    IMAGE_INSTALL += “libpng”
    IMAGE_INSTALL += "opencv"
    IMAGE_INSTALL += "python-opencv"
    PACKAGE_EXCLUDE = "libpng"
```

## Third Party, Not Common, AX25

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

