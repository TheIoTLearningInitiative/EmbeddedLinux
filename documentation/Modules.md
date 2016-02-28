# Modules

## Hello World Kernel Module

    user@host:~$ pwd
    /home/xe1gyq/.../edison-src
    user@host:~$ cd out/current
    user@host:~$ source poky/oe-init-build-env
    user@host:~$ pwd
    /home/xe1gyq/Projects/edison-src/out/linux64/build
    user@host:~$ cd tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux/
    user@host:~$ mkdir drivers/helloworld
    user@host:~$ nano drivers/helloworld/helloworld.c


```C
#include <linux/init.h>
#include <linux/kernel.h>
#include <linux/module.h>

static int module_init_function(void)
{
    printk(KERN_INFO "Module? Hello!\n");
    return 0;
}

static void module_exit_function(void)
{
    printk(KERN_INFO "Module? Bye!\n");
}

MODULE_LICENSE("GPL");
MODULE_AUTHOR("xe1gyq");
MODULE_DESCRIPTION("My First Linux Kernel Module");

module_init(module_init_function);
module_exit(module_exit_function);
```

    user@host:~$ nano drivers/helloworld/Kconfig

```
    menu "Hello Module Kernel Support"
    config HELLO_WORLD
            tristate "Hello Module Driver"
            depends on X86
            help
              Select this option to run a Hello World Module!
    endmenu
```

    user@host:~$ nano drivers/helloworld/Makefile

```Shell
    obj-$(CONFIG_HELLO_WORLD)               += helloworld.o
```

    user@host:~$ nano drivers/Kconfig

```
    menu "Device Drivers"
    source "drivers/helloworld/Kconfig"
    source "drivers/base/Kconfig"
    ...
```

    user@host:~$ nano drivers/Makefile

```
    ...
    # Rewritten to use lists instead of if-statements.
    #
    obj-$(CONFIG_HELLO_WORLD) += helloworld/
    obj-y += irqchip/
    ...
```

    user@host:~$ cd -
    user@host:~$ bitbake virtual/kernel -c menuconfig
    ...
    edison-src/out/linux64/build/tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux-edison-standard-build/Makefile
    ...

```
CONFIG_LOCALVERSION
Symbol: LOCALVERSION [=-yocto-xe1gyq]
  Type  : string
  Prompt: Local version - append to kernel release
  Location:
    -> General setup                      │  
  Defined at init/Kconfig:56
```


```
CONFIG_HELLO_WORLD:
Select this option to run a Hello World Module!
Symbol: HELLO_WORLD [=y]
Type : tristate
Prompt: Hello Module Driver
   Location:
     -> Device Drivers
       -> Hello Module Kernel Support
   Defined at drivers/helloworld/Kconfig:3
   Depends on: X86 [=y]
```

    user@host:~$ cp tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux-edison-standard-build/.config tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/defconfig 
    user@host:~$ cp tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux-edison-standard-build/.config tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux/arch/x86/configs/i386_edison_defconfig
    user@host:~$ bitbake virtual/kernel -c configure -f -v
    user@host:~$ cd ../../..
    user@host:~$ make image
    user@host:~$ make flash
    
## Others

    user@host:~$ nano edison-src/meta-intel-edison/meta-intel-edison-bsp/recipes-kernel/linux/files/defconfig
    user@host:~$ nano edison-src/meta-intel-edison/meta-intel-edison-bsp/recipes-kernel/linux/files/upstream_to_edison.patch
    user@host:~$ find -name 
    user@host:~$ cp /build/tmp/work/edison-poky-linux/linuxyocto/3.10.17+gitAUTOINC+6ad20f049a_c03195ed6e-r0/linux-edison-standardbuild/.config build/tmp/work/edison-poky-linux/linuxyocto/3.10.17+gitAUTOINC+6ad20f049a_c03195ed6er0/defconfig


Linux Kernel Modules
==

## Intel Edison Linux Kernel Loaded Modules

```sh
    root@edison:~# lsmod
    Module                  Size  Used by
    usb_f_acm              14335  1 
    u_serial               18582  6 usb_f_acm
    g_multi                70924  0 
    libcomposite           39245  2 usb_f_acm,g_multi
    bcm_bt_lpm             13708  0 
    bcm4334x              587105  0 
```
## Intel Edison Linux Kernel All Modules

```sh
    root@edison:~/IntelEdison/examples# find /lib/modules/* -name '*'
    /lib/modules/3.10.17-yocto-standard
    /lib/modules/3.10.17-yocto-standard/modules.devname
    /lib/modules/3.10.17-yocto-standard/modules.dep
    /lib/modules/3.10.17-yocto-standard/modules.alias.bin
    /lib/modules/3.10.17-yocto-standard/modules.builtin.bin
    /lib/modules/3.10.17-yocto-standard/modules.order
    /lib/modules/3.10.17-yocto-standard/modules.softdep
    /lib/modules/3.10.17-yocto-standard/extra
    /lib/modules/3.10.17-yocto-standard/extra/bcm4334x.ko
    /lib/modules/3.10.17-yocto-standard/modules.symbols
    /lib/modules/3.10.17-yocto-standard/modules.builtin
    /lib/modules/3.10.17-yocto-standard/modules.dep.bin
    /lib/modules/3.10.17-yocto-standard/modules.alias
    /lib/modules/3.10.17-yocto-standard/kernel
    /lib/modules/3.10.17-yocto-standard/kernel/net
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_state.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_length.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_NETMAP.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_conntrack.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_conntrack_broadcast.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_connbytes.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_conntrack_proto_sctp.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nfnetlink_queue.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_nat_ftp.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_policy.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_helper.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_CT.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_ecn.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_conntrack_proto_gre.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_conntrack_irc.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_NFQUEUE.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_string.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_limit.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_conntrack_netbios_ns.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_realm.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_CLASSIFY.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_connmark.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_connlimit.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_conntrack_sip.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_conntrack_ftp.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_TRACE.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_nat.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_conntrack_sane.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_tcpmss.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_conntrack_h323.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_mac.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_esp.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_conntrack_amanda.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_pkttype.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_multiport.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_nat_proto_udplite.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nfnetlink_log.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nfnetlink.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_dscp.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_conntrack_proto_udplite.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_NFLOG.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_conntrack_tftp.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_cluster.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_tproxy_core.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_dccp.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_TCPMSS.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_nat_sip.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_conntrack_pptp.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_conntrack_netlink.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_sctp.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_nat_tftp.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_DSCP.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_socket.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_nat_proto_sctp.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_u32.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_nat_amanda.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_statistic.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_quota.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_comment.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_hashlimit.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_REDIRECT.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/nf_nat_irc.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_nat.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/netfilter/xt_conntrack.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/mac80211
    /lib/modules/3.10.17-yocto-standard/kernel/net/mac80211/mac80211.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv6
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv6/netfilter
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv6/netfilter/nf_defrag_ipv6.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/nf_nat_pptp.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/arp_tables.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/nf_nat_h323.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/arptable_filter.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/ipt_ah.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/nf_defrag_ipv4.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/iptable_filter.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/iptable_nat.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/ip_tables.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/iptable_raw.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/ipt_CLUSTERIP.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/nf_conntrack_ipv4.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/ipt_ULOG.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/nf_nat_proto_gre.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/arpt_mangle.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/ipt_REJECT.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/ipt_MASQUERADE.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/iptable_mangle.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/nf_nat_ipv4.ko
    /lib/modules/3.10.17-yocto-standard/kernel/net/ipv4/netfilter/ipt_ECN.ko
    /lib/modules/3.10.17-yocto-standard/kernel/drivers
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/media
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/media/v4l2-core
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/media/v4l2-core/videobuf2-vmalloc.ko
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/media/v4l2-core/videobuf2-memops.ko
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/media/v4l2-core/videobuf2-core.ko
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/media/usb
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/media/usb/uvc
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/media/usb/uvc/uvcvideo.ko
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/media/usb/gspca
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/media/usb/gspca/gspca_main.ko
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/staging
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/staging/iio
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/staging/iio/trigger
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/staging/iio/trigger/iio-trig-sysfs.ko
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/usb
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/usb/serial
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/usb/serial/cp210x.ko
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/usb/gadget
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/usb/gadget/usb_f_acm.ko
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/usb/gadget/u_serial.ko
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/usb/gadget/g_multi.ko
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/usb/gadget/libcomposite.ko
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/misc
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/misc/bcm-lpm
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/misc/bcm-lpm/bcm_bt_lpm.ko
    /lib/modules/3.10.17-yocto-standard/kernel/lib
    /lib/modules/3.10.17-yocto-standard/kernel/lib/ts_kmp.ko
    /lib/modules/3.10.17-yocto-standard/kernel/lib/ts_fsm.ko
    /lib/modules/3.10.17-yocto-standard/kernel/lib/ts_bm.ko
    /lib/modules/3.10.17-yocto-standard/kernel/fs
    /lib/modules/3.10.17-yocto-standard/kernel/fs/aufs
    /lib/modules/3.10.17-yocto-standard/kernel/fs/aufs/aufs.ko
    /lib/modules/3.10.17-yocto-standard/kernel/arch
    /lib/modules/3.10.17-yocto-standard/kernel/arch/x86
    /lib/modules/3.10.17-yocto-standard/kernel/arch/x86/kernel
    /lib/modules/3.10.17-yocto-standard/kernel/arch/x86/kernel/test_nx.ko
    /lib/modules/3.10.17-yocto-standard/modules.symbols.bin
```
## Intel Edison Linux Kernel One Modules

```sh
    root@edison:~/IntelEdison/examples# find /lib/modules/* -name 'uvc'
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/media/usb/uvc
    root@edison:~/IntelEdison/examples# opkg install kernel-module-uvcvideo
    Package kernel-module-uvcvideo (3.10.17-r0) installed in root is up to date.
    root@edison:~/IntelEdison/examples# lsmod | grep uvc
    root@edison:~/IntelEdison/examples# find /lib/modules/* -name 'snd'
    root@edison:~/IntelEdison/examples# find /lib/modules/* -name 'audio'
    root@edison:~/IntelEdison/examples# find /lib/modules/* -name 'alsa'
    root@edison:~/IntelEdison/examples# find /lib/modules/* -name ''
```