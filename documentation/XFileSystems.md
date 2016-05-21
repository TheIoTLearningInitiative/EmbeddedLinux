# X File Systems

## Procfs

> The proc filesystem (procfs) is a special filesystem in Unix-like operating systems that presents information about processes and other system information in a hierarchical file-like structure, providing a more convenient and standardized method for dynamically accessing process data held in the kernel than traditional tracing methods or direct access to kernel memory. Typically, it is mapped to a mount point named /proc at boot time. [Wikipedia](https://en.wikipedia.org/wiki/Procfs)

```sh
root@edison:~# ls /proc/
1    21   290   45    7   93                   filesystems   sched_debug
10   210  291   4504  70  94                   fs            schedstat
11   213  292   451   71  95                   interrupts    scsi
117  214  297   4523  72  96                   iomem         self
12   218  3     4526  73  asound               ioports       slabinfo
125  22   30    4545  76  buddyinfo            irq           softirqs
126  225  309   4549  77  bus                  kallsyms      stat
127  23   310   46    78  cgroups              key-users     sys
13   244  317   460   8   cmdline              keys          sysrq-trigger
131  25   321   47    80  consoles             kmsg          sysvipc
132  251  327   486   82  cpuinfo              kpagecount    timer_list
14   256  331   492   83  crypto               kpageflags    timer_stats
142  26   332   5     84  debug_read_history   loadavg       tty
16   27   387   541   85  devices              locks         uptime
166  270  43    60    86  diskstats            meminfo       version
17   276  434   61    87  dma                  misc          vmallocinfo
18   278  4382  62    88  dri                  modules       vmstat
19   28   4383  63    89  driver               mounts        zoneinfo
2    284  44    65    9   emmc_ipanic_console  mtrr
20   286  4457  66    90  emmc_ipanic_header   net
200  289  4458  67    91  execdomains          pagetypeinfo                     
205  29   447   69    92  fb                   partitions                       
root@edison:~# 
```

## Devfs

> devfs is an obsolete and no longer available virtual filesystem that automatically generated the contents of /dev on some older versions of the Linux kernel. [Wikipedia](https://en.wikipedia.org/wiki/Device_file)

- [How Devfs and Dev Filesystem differ](http://stackoverflow.com/questions/16431554/how-devfs-and-dev-file-system-differ)

## Sysfs

> sysfs is a virtual file system provided by the Linux kernel that exports information about various kernel subsystems, hardware devices, and associated device drivers, from the kernel's device model to user space, through virtual files. [Wikipedia](https://en.wikipedia.org/wiki/Sysfs)

- [Driver porting: Device model overview](http://lwn.net/Articles/31185/)
- [Driver porting: An example /sys hierarchy](http://lwn.net/Articles/31511/)
- [Driver porting: Devices and attributes](http://lwn.net/Articles/31220/)

```sh
    root@edison:~# mount
    /dev/mmcblk0p8 on / type ext4 (rw,nodev,noatime,discard,noauto_da_alloc,data=ordered)
    devtmpfs on /dev type devtmpfs (rw,relatime,size=491272k,nr_inodes=122818,mode=755)
    proc on /proc type proc (rw,relatime)
    sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
    tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
    devpts on /dev/pts type devpts (rw,relatime,gid=5,mode=620)
    tmpfs on /run type tmpfs (rw,nosuid,nodev,mode=755)
    tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
    cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cg)
    pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
    cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
    cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpuacct,cpu)
    cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
    cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
    cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
    cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
    systemd-1 on /boot type autofs (rw,relatime,fd=22,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
    tmpfs on /tmp type tmpfs (rw)
    debugfs on /sys/kernel/debug type debugfs (rw,relatime)
    mqueue on /dev/mqueue type mqueue (rw,relatime)
    systemd-1 on /home type autofs (rw,relatime,fd=31,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
    configfs on /sys/kernel/config type configfs (rw,relatime)
    fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
    tmpfs on /var/volatile type tmpfs (rw,relatime)
    /dev/mmcblk0p5 on /factory type ext4 (ro,nosuid,nodev,noatime,discard,noauto_da_alloc)
    /dev/mmcblk0p10 on /home type ext4 (rw,nosuid,nodev,noatime,discard,noauto_da_alloc,data=ordered)
    /dev/mmcblk0p7 on /boot type vfat (rw,nosuid,nodev,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortna)
```