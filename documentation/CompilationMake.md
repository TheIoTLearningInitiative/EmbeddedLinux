# Make

### Building via Make

#### Make Setup

```sh
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
```

```sh
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
```

```sh
    user@host:~$ ls
    bbcache  Makefile  meta-arduino  meta-intel-edison  out  pub
```

##### Make Building Workflow

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
```
