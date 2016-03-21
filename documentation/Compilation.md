Compilation
==

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
    
    user@host:~$ ls
    Makefile  meta-intel-edison
    
    user@host:~$ ls meta-intel-edison/
    COPYING.MIT  meta-intel-arduino     meta-intel-edison-distro  setup.sh
    MAINTAINERS  meta-intel-edison-bsp  README                    utils
```

### Building via Make

#### Make Setup

```sh
    user@host:~$ make setup
    user@host:~$ make setup
    Setup buildenv for SDK host linux64
    ./meta-intel-edison/setup.sh  --dl_dir=/home/abraham/Projects/RealTime/v25/edison-src/bbcache/downloads --sstate_dir=/home/abraham/Projects/RealTime/v25/edison-src/bbcache/sstate-cache --build_dir=/home/abraham/Projects/RealTime/v25/edison-src/out/linux64 --build_name=custom_build_aarcemor@20151220153244 --sdk_host=linux64
    We are building in external mode
    Fetching origin
    Fetching origin
    Fetching origin
    Fetching origin
    Cloning Poky in the /home/abraham/Projects/RealTime/v25/edison-src/out/linux64/poky directory
    Cloning into 'poky'...
    done.
    Note: checking out 'yocto-1.7.2'.
    You are in 'detached HEAD' state. You can look around, make experimental
    changes and commit them, and you can discard any commits you make in this
    state without impacting any branches by performing another checkout.
    
    If you want to create a new branch to retain commits you create, you may
    do so (now or later) by using -b with the checkout command again. Example:

      git checkout -b new_branch_name

    HEAD is now at 29812e6... busybox: unbreak tar of uncompressed files
    Cloning Mingw layer to /home/abraham/Projects/RealTime/v25/edison-src/out/linux64/poky/meta-mingw directory from local cache
    Cloning into 'meta-mingw'...
    done.
    Cloning Darwin layer to /home/abraham/Projects/RealTime/v25/edison-src/out/linux64/poky/meta-darwin directory from local cache
    Cloning into 'meta-darwin'...
    done.
    Note: checking out '29b5ff31cee24e796f2eb2d2fd1269e3e92c831c'.

    You are in 'detached HEAD' state. You can look around, make experimental
    changes and commit them, and you can discard any commits you make in this
    state without impacting any branches by performing another checkout.
    
    If you want to create a new branch to retain commits you create, you may
    do so (now or later) by using -b with the checkout command again. Example:

      git checkout -b new_branch_name

    HEAD is now at 29b5ff3... gcc-runtime: Don't pollute global export namespace
    Cloning meta-intel-iot-middleware layer to /home/abraham/edison-src/out/linux64/poky/meta-intel-iot-middleware directory from local cache
    Cloning into 'meta-intel-iot-middleware'...
    done.
    Note: checking out 'c6d681475e76107e6c04c5f7a06034dc9e772d1e'.

    You are in 'detached HEAD' state. You can look around, make experimental
    changes and commit them, and you can discard any commits you make in this
    state without impacting any branches by performing another checkout.

    If you want to create a new branch to retain commits you create, you may
    do so (now or later) by using -b with the checkout command again. Example:

      git checkout -b new_branch_name

    HEAD is now at c6d6814... upm: Update to 0.3.1
    Cloning meta-arduino layer to /home/abraham/Projects/RealTime/v25/edison-src directory from GitHub.com/01org/meta-arduino
    Cloning into 'meta-arduino'...
    remote: Counting objects: 72, done.
    remote: Total 72 (delta 0), reused 0 (delta 0), pack-reused 72
    Unpacking objects: 100% (72/72), done.
    Checking connectivity... done.
    Already on '1.6.x'
    Your branch is up-to-date with 'origin/1.6.x'.
    Applying patch on poky
    Initializing yocto build environment
    Setting up yocto configuration file (in build/conf/local.conf)
    ** Success **
    SDK will be generated for linux64 host
    Now run these two commands to setup and build the flashable image:
    cd /home/abraham/edison-src/out/linux64
    source poky/oe-init-build-env
    bitbake edison-image
    *************
    user@host:~$ ls
    bbcache  Makefile  meta-arduino  meta-intel-edison  out  pub
```

#### Make Image

```sh
    user@host:~$ make image
    /bin/bash -c "source out/current/poky/oe-init-build-env /home/abraham/Projects/RealTime/v25/edison-src/out/current/build ; bitbake -c cleansstate edison-image ; bitbake edison-image"
    
    ### Shell environment set up for builds. ###
    
    You can now run 'bitbake <target>'
    
    Common targets are:
        core-image-minimal
        core-image-sato
        meta-toolchain
        adt-installer
        meta-ide-support
        
    You can also run generated qemu images with a command like 'runqemu qemux86'
    Parsing recipes: 100% |#################################################################################################| Time: 00:00:10
    Parsing of 959 .bb files complete (0 cached, 959 parsed). 1364 targets, 117 skipped, 0 masked, 0 errors.
    NOTE: Resolving any missing task queue dependencies
    
    Build Configuration:
    BB_VERSION        = "1.24.0"
    BUILD_SYS         = "x86_64-linux"
    NATIVELSBSTRING   = "Ubuntu-14.04"
    TARGET_SYS        = "i586-poky-linux"
    MACHINE           = "edison"
    DISTRO            = "poky-edison"
    DISTRO_VERSION    = "1.7.2"
    TUNE_FEATURES     = "m32 core2"
    TARGET_FPU        = ""
    meta              
    meta-yocto        
    meta-yocto-bsp    = "(detachedfromyocto-1.7.2):29812e61736a95f1de64b3e9ebbb9c646ebd28dd"
    meta-intel-edison-bsp 
    meta-intel-edison-distro = "<unknown>:<unknown>"
    meta-intel-iot-middleware = "(detachedfromc6d6814):c6d681475e76107e6c04c5f7a06034dc9e772d1e"
    meta-intel-arduino = "<unknown>:<unknown>"
    meta-arduino      = "1.6.x:541b127163acb243109f07141bf249da2ecdcd9a"
    
    NOTE: Preparing runqueue
    NOTE: Executing RunQueue Tasks
    NOTE: Tasks Summary: Attempted 2 tasks of which 0 didn't need to be rerun and all succeeded.
    Loading cache: 100% |###################################################################################################| ETA:  00:00:00
    Loaded 1365 entries from dependency cache.
    NOTE: Resolving any missing task queue dependencies
    
    Build Configuration:
    BB_VERSION        = "1.24.0"
    BUILD_SYS         = "x86_64-linux"
    NATIVELSBSTRING   = "Ubuntu-14.04"
    TARGET_SYS        = "i586-poky-linux"
    MACHINE           = "edison"
    DISTRO            = "poky-edison"
    DISTRO_VERSION    = "1.7.2"
    TUNE_FEATURES     = "m32 core2"
    TARGET_FPU        = ""
    meta              
    meta-yocto        
    meta-yocto-bsp    = "(detachedfromyocto-1.7.2):29812e61736a95f1de64b3e9ebbb9c646ebd28dd"
    meta-intel-edison-bsp 
    meta-intel-edison-distro = "<unknown>:<unknown>"
    meta-intel-iot-middleware = "(detachedfromc6d6814):c6d681475e76107e6c04c5f7a06034dc9e772d1e"
    meta-intel-arduino = "<unknown>:<unknown>"
    meta-arduino      = "1.6.x:541b127163acb243109f07141bf249da2ecdcd9a"
    
    NOTE: Preparing runqueue
    WARNING: /home/abraham/Projects/RealTime/v25/edison-src/out/linux64/poky/meta/recipes-kernel/linux/linux-yocto_3.10.bb.do_configure is tainted from a forced run
    NOTE: Executing SetScene Tasks
    NOTE: Executing RunQueue Tasks
    Currently 1 running tasks (3754 of 3757):
    0: edison-image-1.0-r0 do_rootfs (pid 16950)
    ...
    NOTE: Tasks Summary: Attempted 3757 tasks of which 3750 didn't need to be rerun and all succeeded.

    Summary: There was 1 WARNING message shown.
    ./meta-intel-edison/utils/flash/postBuild.sh /home/abraham/Projects/RealTime/v25/edison-src/out/current/build
    EDISON_ROOTFS_MB = 1536, IMAGE_SIZE_MB = 548
    1+0 records in
    1+0 records out
    4194304 bytes (4.2 MB) copied, 0.00332 s, 1.3 GB/s
    1+0 records in
    1+0 records out
    4194304 bytes (4.2 MB) copied, 0.00321878 s, 1.3 GB/s
    1+0 records in
    1+0 records out
    4194304 bytes (4.2 MB) copied, 0.00323493 s, 1.3 GB/s
    1+0 records in
    1+0 records out
    4194304 bytes (4.2 MB) copied, 0.00343959 s, 1.2 GB/s
    1+0 records in
    1+0 records out
    4194304 bytes (4.2 MB) copied, 0.00328377 s, 1.3 GB/s
    1+0 records in
    1+0 records out
    4194304 bytes (4.2 MB) copied, 0.00338686 s, 1.2 GB/s
    1+0 records in
    1+0 records out
    4194304 bytes (4.2 MB) copied, 0.00324502 s, 1.3 GB/s
    Image Name:   Edison Updater script
    Created:      Sun Dec 20 15:39:48 2015
    Image Type:   PowerPC Linux Script (uncompressed)
    Data Size:    14683 Bytes = 14.34 kB = 0.01 MB
    Load Address: 00010000
    Entry Point:  00010000
    Contents:
       Image 0: 14675 Bytes = 14.33 kB = 0.01 MB
    **** Done ***
    Files ready to flash in /home/abraham/Projects/RealTime/v25/edison-src/out/current/build/toFlash/
    Run the flashall script there to start flashing.
    *************
    user@host:~$ ls
    bbcache  Makefile  meta-arduino  meta-intel-edison  out  pub
```

#### Make Building Workflow

- meta-intel-edison/setup.sh
  - --dl_dir = bbcache/downloads
  - --sstate_dir = bbcache/sstate-cache
  - --build_dir = out/linux64 
  - --build_name = custom_build_xe1gyq@20151001233406
  - --sdk_host = linux64
- Repositories Cloning
  - poky-mirror.git
  - meta-mingw-mirror.git
  - meta-darwin-mirror.git
  - meta-intel-iot-middleware-mirror.git
  - poky
- Yocto Build Environment
  - build/conf/local.conf
  - source poky/oe-init-build-env
  - bitbake edison-image

```sh
    Build Configuration:
    BB_VERSION        = "1.24.0"
    BUILD_SYS         = "i686-linux"
    NATIVELSBSTRING   = "Debian-8.1"
    TARGET_SYS        = "i586-poky-linux"
    MACHINE           = "edison"
    DISTRO            = "poky-edison"
    DISTRO_VERSION    = "1.7.2"
    TUNE_FEATURES     = "m32 core2"
    TARGET_FPU        = ""
    meta              
    meta-yocto        
    meta-yocto-bsp    = "(detachedfromyocto-1.7.2):29812e61736a95f1de64b3e9ebbb9c646ebd28dd"
    meta-intel-edison-bsp 
    meta-intel-edison-distro = "<unknown>:<unknown>"
    meta-intel-iot-middleware = "(detachedfromc6d6814):c6d681475e76107e6c04c5f7a06034dc9e772d1e"
    meta-intel-arduino = "<unknown>:<unknown>"
    meta-arduino      = "1.6.x:541b127163acb243109f07141bf249da2ecdcd9a"
```

#### Make Flash

```sh
    user@host:~$ make flash
    abraham@aarcemor-desk:~/Projects/RealTime/v25/edison-src$ make flash
    ./out/current/build/toFlash/flashall.sh
    Using U-Boot target: edison-blankcdc
    Now waiting for dfu device 8087:0a99
    Please plug and reboot the board
    Flashing IFWI
    ##################################################] finished!
    ##################################################] finished!
    Flashing U-Boot
    ##################################################] finished!
    Flashing U-Boot Environment
    ##################################################] finished!
    Flashing U-Boot Environment Backup
    ##################################################] finished!
    Rebooting to apply partition changes
    Now waiting for dfu device 8087:0a99
    Flashing boot partition (kernel)
    ##################################################] finished!
    Flashing rootfs, (it can take up to 5 minutes... Please be patient)
    ##################################################] finished!
    Rebooting
    U-boot & Kernel System Flash Success...
    Your board needs to reboot to complete the flashing procedure, please do not unplug it for 2 minutes.
    user@host:~$ ls
    bbcache  flash.log  Makefile  meta-arduino  meta-intel-edison  out  pub
    user@host:~$ cd out/current
    user@host:~$ ls
    build  poky
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
    user@host:~$ bitbake virtual/kernel -c menuconfig
    user@host:~$ bitbake virtual/kernel -c configure -f -v
    user@host:~$ bitbake edison-image
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

## Links

- [Intel® Edison Board Support Package](http://download.intel.com/support/edison/sb/edisonbsp_ug_331188007.pdf)

## Under investigation?
    
    - What is it create-debian-image.sh
    user@host:~$ edison-src/meta-intel-edison/utils

- https://software.intel.com/en-us/articles/opencv-300-beta-ipp-tbb-enabled-on-yocto-with-intel-edison
- http://download.intel.com/support/edison/sb/edisonbsp_ug_331188007.pdf
- https://hayestech.files.wordpress.com/2015/01/intel-edison-bsd.pdf
- http://www.instructables.com/id/Securing-IoT-applications-built-on-Intel-Galileo-a/
- http://www.embarcados.com.br/intel-edison-yocto-como-construir-sua-propria-distribuicao-linux-embarcado/
- http://www.embarcados.com.br/raspberry-pi-qt5-yocto-parte-1/
- https://communities.intel.com/docs/DOC-23391
- https://software.intel.com/en-us/articles/intel-edison-developer-resources
- http://download.intel.com/support/edison/sb/edisonbsp_ug_331188007.pdf
- http://drejkim.com/blog/2014/11/22/building-an-edison-image-and-changing-the-root-partition-size/
- https://hayestech.wordpress.com/2015/01/26/building-custom-intel-edison-images/
http://www.yoctoproject.org/docs/1.1/yocto-project-qs/yocto-project-qs.html
http://edplay.weebly.com/how-to/building-linux-for-intel-edison
- https://wiki.debian.org/EmDebian/CrossDebootstrap
- https://communities.intel.com/message/273743
- http://layers.openembedded.org/layerindex/branch/master/layer/meta-intel-edison-bsp/
- http://shawnhymel.com/724/creating-a-custom-linux-kernel-for-the-edison-yocto-2-1/
- http://events.linuxfoundation.org/sites/events/files/slides/LinuxCon2015_meta-debian_r7.pdf


    user@host:~$ tar xvf edison-src-weekly-68.tgz
    user@host:~$ ls edison-src
    arduino  broadcom_cws  device-software  mw

- user@host:~$ ./device-software/setup.sh
- File name: edison-src-weekly-68.tgz @ https://downloadcenter.intel.com/download/24357


- https://scratchbuffer.wordpress.com/2015/09/01/yocto-linux-image-build-for-intel-edison-simple-and-easy/
- https://wiki.lsr.ei.tum.de/nst/documentation/inteledison
- https://hayestech.wordpress.com/2015/01/26/building-custom-intel-edison-images/

### Tbd

    user@host:~$ cd edison-src/meta-intel-edison/
    user@host:~$ git clone https://github.com/openembedded/meta-openembedded.git
    user@host:~$ cd meta-openembedded/
    user@host:~$ git checkout fido
    user@host:~$ cd ../../
    user@host:~$ nano out/current/build/conf/bblayers.conf
    /home/xe1gyq/Projects/edison-src/meta-intel-edison/meta-openembedded \
    user@host:~$ nano meta-intel-edison/meta-intel-edison-distro/recipes-core/images/edison-image.bb
    IMAGE_INSTALL += “opencv”
    PACKAGECONFIG_pn-opencv="eigen jpeg libav png tiff v4l”
    user@host:~$ cd out/current
    user@host:~$ source poky/oe-init-build-env
    user@host:~$ bitbake edison-image
