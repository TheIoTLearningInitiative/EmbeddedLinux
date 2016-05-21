# Dual Boot

## Through Micro SD Card

- [How to boot Edison from an SD card (Linux)](https://communities.intel.com/thread/61048?tstart=0)

### How to boot Edison from an SD card (Linux)

> by Carlos Rodriguez

This tutorial describes a way to boot an Edison board with the Root Filesystem on an external storage (SD card). The kernel and bootloader remain on the local eMMC. For now, we are not able to boot a kernel from an external storage.

#### SD Card Format

First, you need to have a SD card formatted with ext4 file system to store your root file system (do not use FAT/FAT32 for that). You can use gparted or Intel Edison as follows:

```sh
root@edison:~# dmesg
[420794.481542] mmc1: new high speed SDHC card at address 1234
[420794.482480] mmcblk1: mmc1:1234 SA16G 14.4 GiB
[420794.484152]  mmcblk1: p1
```

```sh
root@edison:~# umount /dev/mmcblk1p1
root@edison:~# fdisk /dev/mmcblk1   

Welcome to fdisk (util-linux 2.24.2).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Command (m for help): p
Disk /dev/mmcblk1: 14.5 GiB, 15548284928 bytes, 30367744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device         Boot Start       End   Blocks  Id System
/dev/mmcblk1p1       8192  30367743 15179776   c W95 FAT32 (LBA)

Command (m for help): d

Selected partition 1
Partition 1 has been deleted.

Command (m for help): n                                                         
                                                                                
Partition type:                                                                 
   p   primary (0 primary, 0 extended, 4 free)                                  
   e   extended                                                                 
Select (default p): p                                                           
Partition number (1-4, default 1): 1                                            
First sector (2048-30367743, default 2048):                                     
Last sector, +sectors or +size{K,M,G,T,P} (2048-30367743, default 30367743):    
                                                                                
Created a new partition 1 of type 'Linux' and of size 14.5 GiB.                 
                                                                                
Command (m for help): w                                                         
The partition table has been altered.                                           
Calling ioctl() to re-read partition table.                                     
Re-reading the partition table failed.: Device or resource busy                 
                                                                                
The kernel still uses the old table. The new table will be used at the next reb.
                                                                                
root@edison:~# 
```

```sh
root@edison:~# mkfs.ext4 /dev/mmcblk1p1                                         
mke2fs 1.42.9 (28-Dec-2013)                                                     
Discarding device blocks: done                                                  
Filesystem label=                                                               
OS type: Linux                                                                  
Block size=4096 (log=2)                                                         
Fragment size=4096 (log=2)                                                      
Stride=0 blocks, Stripe width=0 blocks                                          
950272 inodes, 3794944 blocks                                                   
189747 blocks (5.00%) reserved for the super user                               
First data block=0                                                              
Maximum filesystem blocks=3888119808                                            
116 block groups                                                                
32768 blocks per group, 32768 fragments per group                               
8192 inodes per group                                                           
Superblock backups stored on blocks:                                            
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208  
                                                                                
Allocating group tables: done                                                   
Writing inode tables: done                                                      
Creating journal (32768 blocks): done                                           
Writing superblocks and filesystem accounting information: done                 
                                                                                
root@edison:~# 
```

Download and unpack the Edison OS image from the Software Downloads section of the community. 

```sh
user@linux:~/Downloads/unpacked-image$ ls
dnx_fwr_saltbay_pr2.bin     edison_ifwi-dbg-02-dfu.bin  edison-image-edison.ext4    package-list.txt
dnx_osr_saltbay_pr2.bin     edison_ifwi-dbg-03.bin      edison-image-edison.hddimg  pft-config-edison.xml
edison_dnx_fwr.bin          edison_ifwi-dbg-03-dfu.bin  filter-dfu-out.js           pft-config-mcg_sku.xml
edison_dnx_osr.bin          edison_ifwi-dbg-04.bin      flashall.bat                u-boot-edison.bin
edison_ifwi-dbg-00.bin      edison_ifwi-dbg-04-dfu.bin  flashall.sh                 u-boot-edison.img
edison_ifwi-dbg-00-dfu.bin  edison_ifwi-dbg-05.bin      flash.log                   u-boot-envs
edison_ifwi-dbg-01.bin      edison_ifwi-dbg-05-dfu.bin  ifwi_saltbay_pr2.bin
edison_ifwi-dbg-01-dfu.bin  edison_ifwi-dbg-06.bin      ifwi_saltbay_pr2-dfu.bin
edison_ifwi-dbg-02.bin      edison_ifwi-dbg-06-dfu.bin  ota_update.scr
```

```sh
user@linux:~/Downloads/unpacked-image$ mkdir Rootfs
```

```sh
user@linux:~/Downloads/unpacked-image$ sudo mount ./edison-image-edison.ext4 Rootfs
[sudo] password for user:
 ```
 
```sh
user@linux:~/Downloads/unpacked-image$ sudo cp -a Rootfs/* /media/8f88dd49-95ac-4d0c-8c3a-abd445f87fa1/ (or whatever folder name your pc gave to your SD card)
```

```sh
user@linux:~/Downloads/unpacked-image$ sync
```

3. Your SD card is now ready to boot. Find out the SD card device name


On a running Edison board, plug your formatted SD card and get the device name:

```sh
root@edison:~# dmesg |tail -n 10
[    6.387683] g_multi gadget: high-speed config #2: Multifunction with CDC ECM
[    6.522733] EXT4-fs (mmcblk0p5): mounted filesystem without journal. Opts: discard,barrier=1,data=ordered,noauto_da_ac
[    7.375959] systemd-fstab-generator[174]: Checking was requested for "rootfs", but it is not a device.
[   10.001889] systemd[1]: Reloading.
[   10.098201] systemd-fstab-generator[223]: Checking was requested for "rootfs", but it is not a device.
[   20.372477] EXT4-fs (mmcblk0p10): mounted filesystem with ordered data mode. Opts: discard,barrier=1,data=ordered,noac
[  767.952993] mmc1: new high speed SDHC card at address 0007
[  767.953999] mmcblk1: mmc1:0007 SD16G 14.4 GiB 
[  767.956822]  mmcblk1: p1
[  768.275336] EXT4-fs (mmcblk1p1): mounted filesystem with ordered data mode. Opts: (null)
```

Here, the SD card device is “/dev/mmcblk1” and the partition we’ve created is "/dev/mmcblk1p1".
To boot using the external device, you need to modify the U-Boot environment variable named "mmc-bootargs" with kernel boot arguments. In the simplest case you can just change the "root=..." part, but here’s a more elaborated approach, which will help you to switch between booting from eMMC and the SD card more easily.
In the Edison Linux console set the U-Boot environment variables like the below:

```sh
# the below is a single line

root@edison:~# fw_printenv |grep mmc-bootargs=
mmc-bootargs=setenv bootargs root=PARTUUID=${uuid_rootfs} rootfstype=ext4 ${bootargs_console} ${bootargs_debug} systemd.unit=${bootargs_target}.target hardware_id=${hardware_id} g_multi.iSerialNumber=${serial#} g_multi.dev_addr=${usb0addr}
```

```sh
# the below is a single command line
```

```sh
root@edison:~# fw_setenv mmc-bootargs 'setenv bootargs root=${myrootfs} rootdelay=3 rootfstype=ext4 ${bootargs_console} ${bootargs_debug} systemd.unit=${bootargs_target}.target hardware_id=${hardware_id} g_multi.iSerialNumber=${serial#} g_multi.dev_addr=${usb0addr}'
```

```sh
root@edison:~# fw_setenv myrootfs_sdcard '/dev/mmcblk1p1'
```

```sh
# get the UUID for the eMMC rootfs partition
•	root@edison:~# fw_printenv uuid_rootfs
```

```sh
# use the UUID obtained above
•	root@edison:~# fw_setenv myrootfs_emmc 'PARTUUID=012b3303-34ac-284d-99b4-34e03a2335f4'
```

```sh
# this will set the default, use the value we’ve used for myrootfs_emmc
# if you want to boot from eMMC by default
root@edison:~# fw_setenv myrootfs '/dev/mmcblk1p1'
```

```sh
root@edison:~# fw_setenv do_boot_emmc 'setenv myrootfs ${myrootfs_emmc}; run do_boot'
```

```sh
root@edison:~# fw_setenv do_boot_sdcard 'setenv myrootfs ${myrootfs_sdcard}; run do_boot'
```

Reboot Edison

After boot, verify that you are using rootfs stored on your external device:
The root file system is now 14.1 GB (this will depend on your SD card size).
The SD card will still be automounted to /media/sdcard by Edison’s automount daemon. Since it is the rootfs anyway, this m006F	untpoint becomes useless, so disable the systemd service:
Now, you have plenty of room to work on Edison and no unnecessary mounts:

```sh
root@edison:/etc/systemd# df -h
Filesystem                Size      Used Available Use% Mounted on
/dev/root                14.1G    343.5M     13.1G   3% /
devtmpfs                480.2M         0    480.2M   0% /dev
tmpfs                   480.5M         0    480.5M   0% /dev/shm
tmpfs                   480.5M    492.0K    480.0M   0% /run
tmpfs                   480.5M         0    480.5M   0% /sys/fs/cgroup
tmpfs                   480.5M    492.0K    480.0M   0% /etc/machine-id
systemd-1                 5.5M      5.1M    464.0K  92% /boot
tmpfs                   480.5M      4.0K    480.5M   0% /tmp
tmpfs                   480.5M         0    480.5M   0% /var/volatile
/dev/mmcblk0p5         1003.0K     19.0K    913.0K   2% /factory
/dev/mmcblk0p7            5.5M      5.1M    464.0K  92% /boot
```

Source:
https://communities.intel.com/thread/61048?tstart=0
