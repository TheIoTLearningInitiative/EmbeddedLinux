Modules
==

> A loadable kernel module (LKM) is a mechanism for adding code to, or removing code from, the Linux kernel at run time. They are ideal for device drivers, enabling the kernel to communicate with the hardware without it having to know how the hardware. [DerekMolloy](http://derekmolloy.ie/writing-a-linux-kernel-module-part-1-introduction/)

> In computing, a loadable kernel module (or LKM) is an object file that contains code to extend the running kernel, or so-called base kernel, of an operating system. LKMs are typically used to add support for new hardware (as device drivers) and/or filesystems, or for adding system calls. When the functionality provided by a LKM is no longer required, it can be unloaded in order to free memory and other resources. [Wikipedia](https://en.wikipedia.org/wiki/Loadable_kernel_module)

## Host Development, Hello World Kernel Module

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

## Board Development, Hello World Kernel Module

```sh
    root@edison:~# wget https://communities.intel.com/servlet/JiveServlet/downloadBody/23882-102-1-28238/linux-headers-3.10.17-poky-edison_3.10.17-poky-edison-1_i386.deb.zip
```

https://communities.intel.com/thread/62873?start=0&tstart=0