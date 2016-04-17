Filesystem
==

## File System Disk Space Usage

### Yocto v3.0, Fresh Installation

```sh
root@edison:~# df -h
Filesystem       Size  Used Avail Use% Mounted on
/dev/root        1.4G  958M  365M  73% /
devtmpfs         480M     0  480M   0% /dev
tmpfs            481M     0  481M   0% /dev/shm
tmpfs            481M  592K  480M   1% /run
tmpfs            481M     0  481M   0% /sys/fs/cgroup
tmpfs            481M   42M  439M   9% /tmp
tmpfs            481M  6.1M  475M   2% /var/volatile
tmpfs             97M     0   97M   0% /run/user/0
/dev/loop0       767M  4.0K  767M   1% /media/storage
/dev/mmcblk0p10  1.3G  2.1M  1.3G   1% /home
/dev/mmcblk0p5  1003K   19K  913K   3% /factory
```

### Yocto v2.1, Fresh Installation

```sh
    root@edison:~# df -h
    Filesystem                Size      Used Available Use% Mounted on
    /dev/root                 1.4G    428.6M    934.8M  31% /
    devtmpfs                479.8M         0    479.8M   0% /dev
    tmpfs                   480.1M         0    480.1M   0% /dev/shm
    tmpfs                   480.1M    528.0K    479.5M   0% /run
    tmpfs                   480.1M         0    480.1M   0% /sys/fs/cgroup
    tmpfs                   480.1M      4.0K    480.1M   0% /tmp
    systemd-1                 5.8M      5.3M    456.0K  92% /boot
    tmpfs                   480.1M         0    480.1M   0% /var/volatile
    /dev/mmcblk0p7            5.8M      5.3M    456.0K  92% /boot
    /dev/mmcblk0p10           1.3G      2.0M      1.3G   0% /home
    /dev/mmcblk0p5         1003.0K     19.0K    913.0K   2% /factory
```

### Ubilinux, Fresh Installation

```sh
    edison@ubilinux:~$ df -h
    Filesystem       Size  Used Avail Use% Mounted on
    rootfs           1.4G  812M  504M  62% /
    /dev/root        1.4G  812M  504M  62% /
    devtmpfs         480M     0  480M   0% /dev
    tmpfs             97M  292K   96M   1% /run
    tmpfs            5.0M     0  5.0M   0% /run/lock
    tmpfs            193M     0  193M   0% /run/shm
    tmpfs            481M     0  481M   0% /tmp
    /dev/mmcblk0p7    32M  5.3M   27M  17% /boot
    /dev/mmcblk0p10  1.3G  2.0M  1.3G   1% /home
```

## File System Disk Space Free Up

```sh
    root@edison:~# mv /var/cache /home
    root@edison:~# cd /var
    root@edison:~# ln -sf /home/cache cache
    root@edison:~# mv /usr/share /home
    root@edison:~# cd /usr
    root@edison:~# ln -sf /home/share share
```

- [Get additional 800 MB disk space](http://www.helios.de/heliosapp/edison/)
