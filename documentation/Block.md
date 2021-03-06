# Block

> Block devices are hardware devices distinguished by the random (that is, not necessarily sequential) access of fixed-size chunks of data, called blocks. The most common block device is a hard disk, but many other block devices exist, such as floppy drives, CD-ROM drives, and flash memory. Notice how these are all devices on which you mount a filesystemfilesystems are the lingua franca of block devices. [Makelinux](http://www.makelinux.net/books/lkd2/ch13)

- [Differences between flash devices and block drives](http://www.linux-mtd.infradead.org/faq/general.html#L_mtd_vs_hdd)
- [Creating a ram disk on Linux](http://unix.stackexchange.com/questions/66329/creating-a-ram-disk-on-linux)
- [Free Electrons Block Drivers](http://free-electrons.com/doc/block_drivers.pdf)

## Kernel Integration

### Kernel Display Message Card Insertion

```sh
    root@edison:~# dmesg
    ...
    [ 4430.481280] mmc1: new high speed SDHC card at address 1234
    [ 4430.482221] mmcblk1: mmc1:1234 SA04G 3.63 GiB 
    [ 4430.485107]  mmcblk1: p1
```

### Kernel Display Message Default

```sh
    root@edison:~# dmesg | grep mmc
    [    0.190762] SDIO bus = 1, name = bcm43xx_clk_vmmc, ref_clock = 26000000, addr =0x401
    [    0.741385] emmc_ipanic: init success
    [    1.013752] mmc0: no vqmmc regulator found
    [    1.108914] mmc0: BKOPS_EN bit is not set00
    [    1.417542] mmc0: new HS200 MMC card at address 0001
    [    1.418397] mmcblk0: mmc0:0001 H4G1d\x04 3.64 GiB 
    [    1.418943] mmcblk0boot0: mmc0:0001 H4G1d\x04 partition 1 4.00 MiB
    [    1.419442] mmcblk0boot1: mmc0:0001 H4G1d\x04 partition 2 4.00 MiB
    [    1.419935] mmcblk0rpmb: mmc0:0001 H4G1d\x04 partition 3 4.00 MiB
        [    1.426000]  mmcblk0: p1 p2 p3 p4 p5 p6 p7 p8 p9 p10
    [    1.434287]  mmcblk0boot1: unknown partition table
    [    1.437970]  mmcblk0boot0: unknown partition table
    [    1.438383] mmc0: SDHCI controller on PCI [0000:00:01.0] using ADMA
    [    1.454185] emmc_ipanic: panic partition found, label:panic, device:mmcblk0p6
    [    1.557291] emmc_ipanic: emmc_panic_notify_add: Data available in panic partition
    [    1.557341] emmc_ipanic: emmc_panic_notify_add: proc entry created: emmc_ipanic_header
    [    1.557362] emmc_ipanic: emmc_panic_notify_add: log file 0(1024, 52340)
    [    1.557390] emmc_ipanic: emmc_panic_notify_add: proc entry created: emmc_ipanic_console
    [    1.557407] emmc_ipanic: emmc_panic_notify_add: log file 1(4286578688, 0)
    [    1.557420] emmc_ipanic: emmc_panic_notify_add: empty log file 1
    [    1.557436] emmc_ipanic: emmc_panic_notify_add: log file 2(4286578688, 0)
    [    1.557449] emmc_ipanic: emmc_panic_notify_add: empty log file 2
    [    1.584823] mmc1: no vqmmc regulator found
    [    1.585258] mmc1: SDHCI controller on PCI [0000:00:01.2] using ADMA
    [    1.586232] mmc2: no vqmmc regulator found
    [    1.586668] mmc2: SDHCI controller on PCI [0000:00:01.3] using ADMA
    [    1.746719] EXT4-fs (mmcblk0p8): INFO: recovery required on readonly     filesystem
    [    1.746745] EXT4-fs (mmcblk0p8): write access will be enabled during recovery
    [    1.819782] mmc1: error -84 whilst initialising SD card
    [    1.831504] EXT4-fs (mmcblk0p8): recovery complete
    [    1.834101] EXT4-fs (mmcblk0p8): mounted filesystem with ordered data mode. Opts: (null)
    [    1.897473] mmc1: new high speed SDHC card at address 1234
    [    1.898207] mmcblk1: mmc1:1234 SA08G 7.21 GiB 
    [    1.899941]  mmcblk1: p1 p2
    [    2.226457] mmc2: queuing unknown CIS tuple 0x91 (3 bytes)
    [    2.226495] mmc2: new ultra high speed DDR50 SDIO card at address 0001
    [    4.543403] bcmsdh_sdmmc: bcmsdh_sdmmc_probe Enter
    [    4.543666] bcmsdh_sdmmc: bcmsdh_sdmmc_probe Enter
    [    4.567337] bcmsdh_sdmmc: bcmsdh_sdmmc_probe Enter
    [    5.453381] EXT4-fs (mmcblk0p8): re-mounted. Opts: (null)
    [    5.965905]  lun0: LUN: file: /dev/mmcblk0p9
    [    8.512646] FAT-fs (mmcblk0p7): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
    [    8.557697] EXT4-fs (mmcblk0p10): mounted filesystem with ordered data mode. Opts: (null)
```

## Applications / Libraries

### Setup

#### Opkg

```sh
    root@edison:~# opkg update
    root@edison:~# opkg install e2fsprogs dosfstools
```

#### Apt-Get

```sh
    root@edison:~# apt-get update
    root@edison:~# apt-get install e2fsprogs dosfstools xfsprogs
```
### Programs

#### Mount

```sh
    root@edison:~# mount
    /dev/mmcblk0p8 on / type ext4 (rw,nodev,noatime,discard,noauto_da_alloc,data=ordered)
    ...
    /dev/mmcblk0p7 on /boot type vfat (rw,nosuid,nodev,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortna)    
    /dev/mmcblk1p1 on /media/sdcard type ext3 (rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=writeback)
```

### Usage Models

#### SD Cards, Mount

```sh
    root@edison:~# mount
    /dev/mmcblk0p7 on /boot type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,err)
    /dev/mmcblk0p10 on /home type ext4 (rw,relatime,data=ordered)
    /dev/mmcblk1p1 on /media/sdcard type vfat (rw,relatime,uid=65534,fmask=0000,dmask=0000,allow_utime=0022,codepage=437,ioch)
    root@edison:~# mkfs.ext4 /dev/mmcblk1
    mke2fs 1.42.9 (28-Dec-2013)
    /dev/mmcblk1 is apparently in use by the system; will not make a filesystem here!
    root@edison:~# umount
    root@edison:~# umount /media/sdcard/
    root@edison:~# mkfs.ext4 /dev/mmcblk1
    mke2fs 1.42.9 (28-Dec-2013)
    Discarding device blocks: done                            
    Filesystem label=
    OS type: Linux
    Block size=4096 (log=2)
    ...
    Creating journal (16384 blocks): done
    Writing superblocks and filesystem accounting information: done 
    root@edison:~# mkfs.ext4 -t ext4 /dev/mmcblk1
```

#### SD Cards, Manual Mount

```sh
    root@edison:~# mkdir localdirectory
    root@edison:~# mount -t ext4 /dev/mmcblk1 localdirectory
    root@edison:~# mount | grep mmcblk1
    ...
    /dev/mmcblk1 on /root/localdirectory type ext4 (rw,relatime,data=ordered)
    root@edison:~# cd localdirectory/
    root@edison:~/localdirectory# ls
    lost+found
    root@edison:~/localdirectory# 
```

#### SD Cards, Umount

```sh
    root@edison:~# umount localdirectory
    root@edison:~# umount /dev/mmcblk1
```

#### SD Cards, Automatic Mount

```sh
    root@edison:~# vi /etc/fstab
    /dev/mmcblk1  /path/to/localdirectory
```

#### Tmpfs

> tmpfs is a common name for a temporary file storage facility on many Unix-like operating systems. It is intended to appear as a mounted file system, but stored in volatile memory instead of a persistent storage device. [Wikipedia](https://en.wikipedia.org/wiki/Tmpfs)

```sh
    root@edison:~# cd /tmp
    root@edison:~# mkdir temptmpfs
    root@edison:~# mount -o size=16G -t tmpfs none temptmpfs/
    root@edison:~# cd temptmpfs/
    root@edison:~# ls
    root@edison:~# cd ..
    root@edison:~# mount
    ...
    none on /root/temptmpfs type tmpfs (rw,relatime,size=16777216k)
    root@edison:~# umount /root/temptmpfs
```
