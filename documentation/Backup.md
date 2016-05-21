# Backup

Use dd to backup Intel Edison MMC

```sh
root@edison:~# dmesg
[420794.481542] mmc1: new high speed SDHC card at address 1234
[420794.482480] mmcblk1: mmc1:1234 SA16G 14.4 GiB
[420794.484152]  mmcblk1: p1
```

```sh
root@edison:~# dd if=/dev/mmcblk0 of=/dev/mmcblk1
```

```
root@edison:~# fdisk /dev/mmcblk1 
GPT PMBR size mismatch (7634944 != 30367743) will be corrected by w(rite).
The backup GPT table is corrupt, but the primary appears OK, so that will be us.

Welcome to fdisk (util-linux 2.24.2).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Command (m for help): p
Disk /dev/mmcblk1: 14.5 GiB, 15548284928 bytes, 30367744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 21200400-0804-0146-9DCC-A8C51255994F

Device                 Start          End   Size Type                           
/dev/mmcblk1p1          2048         6143     2M Microsoft basic data           
/dev/mmcblk1p2          6144         8191     1M Microsoft basic data           
/dev/mmcblk1p3          8192        12287     2M Microsoft basic data           
/dev/mmcblk1p4         12288        14335     1M Microsoft basic data           
/dev/mmcblk1p5         14336        16383     1M Microsoft basic data           
/dev/mmcblk1p6         16384        65535    24M Microsoft basic data           
/dev/mmcblk1p7         65536       131071    32M Microsoft basic data           
/dev/mmcblk1p8        131072      3276799   1.5G Microsoft basic data           
/dev/mmcblk1p9       3276800      4849663   768M Microsoft basic data           
/dev/mmcblk1p10      4849664      7634910   1.3G Microsoft basic data  
```