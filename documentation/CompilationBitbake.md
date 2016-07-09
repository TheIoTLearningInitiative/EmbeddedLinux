# Bitbake


## Building via Make + Bitbake

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

## Building via Script

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
