# X File Systems

> A virtual file system (VFS) or virtual filesystem switch is an abstraction layer on top of a more concrete file system. The purpose of a VFS is to allow client applications to access different types of concrete file systems in a uniform way. A VFS can, for example, be used to access local and network storage devices transparently without the client application noticing the difference. It can be used to bridge the differences in Windows, classic Mac OS/macOS and Unix filesystems, so that applications can access files on local file systems of those types without having to know what type of file system they are accessing. [Wikipedia](https://en.wikipedia.org/wiki/Virtual_file_system)

> In Linux, all files are accessed through the Virtual Filesystem Switch, or VFS. This is a layer of code which implements generic filesystem actions and vectors requests to the correct specific code to handle the request. Two main types of code modules take advantage of the VFS services, device drivers and filesystems. [A tour of the Linux VFS](http://www.tldp.org/LDP/khg/HyperNews/get/fs/vfstour.html)

# Procfs

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

```
root@edison:~# ls /dev/
...
char             loop7               ram10      tty14  tty42    ttyPTI0
console          mcelog              ram11      tty15  tty43    ttyPTI1
cpu              mem                 ram12      tty16  tty44    ttymcu0
cpu_dma_latency  mid_ipc             ram13      tty17  tty45    ttymcu1
disk             mmcblk0             ram14      tty18  tty46    ttymcu2
fd               mmcblk0boot0        ram15      tty19  tty47    uhid
full             mmcblk0boot1        ram2       tty2   tty48    uinput
fuse             mmcblk0p1           ram3       tty20  tty49    urandom
i2c-1            mmcblk0p10          ram4       tty21  tty5     usbmon0
i2c-2            mmcblk0p2           ram5       tty22  tty50    vcs
i2c-3            mmcblk0p3           ram6       tty23  tty51    vcs1
i2c-4            mmcblk0p4           ram7       tty24  tty52    vcs2
i2c-5            mmcblk0p5           ram8       tty25  tty53    vcs3
i2c-6            mmcblk0p6           ram9       tty26  tty54    vcs4
i2c-7            mmcblk0p7           random     tty27  tty55    vcs5
iio:device0      mmcblk0p8           rfkill     tty28  tty56    vcs6
iio:device1      mmcblk0p9           rtc        tty29  tty57    vcsa
initctl          mmcblk0rpmb         rtc0       tty3   tty58    vcsa1
input            mmcblk1             shm        tty30  tty59    vcsa2           
intel_sst_ctrl   mqueue              snd        tty31  tty6     vcsa3           
kmem             net                 spidev5.1  tty32  tty60    vcsa4           
kmsg             network_latency     stderr     tty33  tty61    vcsa5           
log              network_throughput  stdin      tty34  tty62    vcsa6           
loop-control     null                stdout     tty35  tty63    vga_arbiter     
loop0            nvram               tty        tty36  tty7     watchdog        
loop1            port                tty0       tty37  tty8     zero            
loop2            pti                 tty1       tty38  tty9                     
loop3            ptmx                tty10      tty39  ttyGS0                   
loop4            pts                 tty11      tty4   ttyMFD0           
```

## Sysfs

> sysfs is a virtual file system provided by the Linux kernel that exports information about various kernel subsystems, hardware devices, and associated device drivers, from the kernel's device model to user space, through virtual files. [Wikipedia](https://en.wikipedia.org/wiki/Sysfs)

- [Driver porting: Device model overview](http://lwn.net/Articles/31185/)
- [Driver porting: An example /sys hierarchy](http://lwn.net/Articles/31511/)
- [Driver porting: Devices and attributes](http://lwn.net/Articles/31220/)

```sh
/sys/
/sys/fs
/sys/fs/ext4
/sys/fs/fuse
/sys/fs/selinux
/sys/fs/cgroup
/sys/fs/pstore
/sys/bus
/sys/bus/cpu
/sys/bus/i2c
/sys/bus/hid
/sys/bus/iio
/sys/bus/mmc
/sys/bus/pci
/sys/bus/spi
/sys/bus/usb
/sys/bus/usb-serial
/sys/bus/scsi
/sys/bus/sdio
sys/bus/clocksource
/sys/bus/media
/sys/bus/rpmsg
/sys/bus/serio
/sys/bus/machinecheck
/sys/bus/event_source
/sys/bus/workqueue
/sys/bus/pci_express
/sys/bus/virtio
/sys/bus/virtio
/sys/bus/platform
/sys/bus/mdio_bus
/sys/dev
/sys/dev/char
/sys/dev/block
/sys/devices
/sys/devices/cpu
/sys/devices/software
/sys/devices/pci0000:00
/sys/devices/tracepoint
/sys/devices/system
/sys/devices/virtual
/sys/devices/platform
/sys/devices/breakpoint
/sys/block
/sys/block/ram0
/sys/block/ram1
/sys/block/ram2
/sys/block/ram3
/sys/block/ram4
/sys/block/ram5
/sys/block/ram7
/sys/block/ram8
/sys/block/ram9
/sys/block/loop0
/sys/block/loop1
/sys/block/loop2
/sys/block/loop3
/sys/block/loop4
/sys/block/loop5
/sys/block/loop6
/sys/block/loop7
/sys/block/ram10
/sys/block/ram11
/sys/block/ram12
/sys/block/ram13
/sys/block/ram14
/sys/block/ram15
/sys/block/mmcblk0rpmb
/sys/block/mmcblk0boot0
/sys/block/mmcblk0boot1
/sys/block/mmcblk0
/sys/block/mmcblk1
/sys/class
/sys/class/vc
/sys/class/bdi
/sys/class/bsg
/sys/class/dma
/sys/class/dmi
/sys/class/drm
/sys/class/mem
/sys/class/net
/sys/class/msr
/sys/class/pps
/sys/class/ptp
/sys/class/pwm
/sys/class/rtc
/sys/class/udc
/sys/class/tty
/sys/class/mmc_host
/sys/class/scsi_disk
/sys/class/scsi_host
/sys/class/gpio
/sys/class/leds
/sys/class/misc
/sys/class/regulator
/sys/class/devfreq
/sys/class/i2c-dev
/sys/class/block
/sys/class/cpuid
/sys/class/hwmon
/sys/class/input
/sys/class/graphics
/sys/class/sound
/sys/class/spi_master
/sys/class/power_supply
/sys/class/ieee80211
/sys/class/thermal
/sys/class/firmware
/sys/class/scsi_generic
/sys/class/extcon
/sys/class/hidraw
/sys/class/scsi_device
/sys/class/rfkill
/sys/class/spidev
/sys/class/usbmon
/sys/class/vtconsole
/sys/class/backlight
/sys/class/i2c-adapter
/sys/class/video_output
/sys/class/pci_bus
/sys/class/mdio_bus
/sys/class/bluetooth
/sys/class/video4linux
/sys/power
/sys/power/state
/sys/power/wake_unlock
/sys/power/pm_freeze_timeout
/sys/power/pm_print_times
/sys/power/wakeup_count
/sys/power/pm_async
/sys/power/wake_lock
/sys/power/pm_test
/sys/firmware
/sys/firmware/sfi
/sys/firmware/memmap
/sys/kernel
/sys/kernel/mm
/sys/kernel/rcu_expedited
/sys/kernel/slab
/sys/kernel/pmic_debug
/sys/kernel/debug
/sys/kernel/notes
/sys/kernel/kexec_crash_size
/sys/kernel/config
/sys/kernel/fscaps
/sys/kernel/kexec_crash_loaded
/sys/kernel/uevent_helper
/sys/kernel/uevent_seqnum
/sys/kernel/profiling
/sys/kernel/fw_update
/sys/kernel/vmcoreinfo
/sys/kernel/kexec_loaded
/sys/module
/sys/module/sg
/sys/module/vt
/sys/module/mmc_core
/sys/module/brd
/sys/module/drm
/sys/module/hid
/sys/module/nfs
/sys/module/otg
/sys/module/pti
/sys/module/sit
/sys/module/snd
/sys/module/stm
/sys/module/tcp_cubic
/sys/module/asix
/sys/module/bnep
/sys/module/fuse
/sys/module/hidp
/sys/module/ipv6
/sys/module/loop
/sys/module/cfg80211
/sys/module/ramoops
/sys/module/bcm4334x
/sys/module/u_serial
/sys/module/cpuidle
/sys/module/rcutree
/sys/module/dns_resolver
...
/sys/module/usbcore
/sys/module/input_polldev
/sys/module/xz_dec
/sys/module/pcie_aspm
/sys/module/dwc3_intel_mrfl
/sys/module/netconsole
/sys/module/oprofile
/sys/module/cdc_ncm
/sys/module/bluetooth
/sys/module/rcupdate
/sys/module/intel_mid
/sys/module/snd_intel_sst
/sys/module/intel_idle
/sys/module/nf_conntrack
/sys/module/keyboard
/sys/module/xhci_hcd
/sys/module/snd_seq_midi
/sys/module/nf_conntrack_ipv4
```

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