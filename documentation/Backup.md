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
