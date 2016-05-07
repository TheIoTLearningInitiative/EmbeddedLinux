Modules
==

> A loadable kernel module (LKM) is a mechanism for adding code to, or removing code from, the Linux kernel at run time. They are ideal for device drivers, enabling the kernel to communicate with the hardware without it having to know how the hardware. [DerekMolloy](http://derekmolloy.ie/writing-a-linux-kernel-module-part-1-introduction/)

> In computing, a loadable kernel module (or LKM) is an object file that contains code to extend the running kernel, or so-called base kernel, of an operating system. LKMs are typically used to add support for new hardware (as device drivers) and/or filesystems, or for adding system calls. When the functionality provided by a LKM is no longer required, it can be unloaded in order to free memory and other resources. [Wikipedia](https://en.wikipedia.org/wiki/Loadable_kernel_module)

## Hello World Kernel Module Compilation

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

## Hello World Kernel Module Native Compilation

Under the host...

```sh
    user@host:~$ wget https://communities.intel.com/servlet/JiveServlet/downloadBody/23882-102-1-28238/linux-headers-3.10.17-poky-edison_3.10.17-poky-edison-1_i386.deb.zip
    user@host:~$ unzip linux-headers-3.10.17-poky-edison_3.10.17-poky-edison-1_i386.deb.zip
```

Under Intel Edison

```sh
    root@edison:~# scp user@host:/home/user/linux-headers-3.10.17-poky-edison_3.10.17-poky-edison-1_i386.deb .
```
```sh
    root@edison:~# ar x linux-headers-3.10.17-poky-edison_3.10.17-poky-edison-1_i386.deb
```

```sh
    root@edison:~# ls data.tar.gz 
    data.tar.gz
```

```sh
    root@edison:~# tar -xvf data.tar.gz
    ...
    ./usr/src/linux-headers-3.10.17-poky-edison/drivers/iio/frequency/Makefile
    ./usr/src/linux-headers-3.10.17-poky-edison/drivers/iio/frequency/Kconfig
    ./lib/
    ./lib/modules/
    ./lib/modules/3.10.17-poky-edison/
    ./lib/modules/3.10.17-poky-edison/build
```

```sh
    root@edison:~# nano ~/usr/src/linux-headers-3.10.17-poky-edison/include/generated/utsrelease.h
    #define UTS_RELEASE "3.10.17-poky-edison+"
    <Save Changes>
```

```sh
    root@edison:~# cd /lib/modules/3.10.17-poky-edison+
```

```sh
    root@edison:/lib/modules/3.10.17-poky-edison+# ls
    extra                modules.builtin.bin  modules.softdep
    kernel               modules.dep          modules.symbols
    modules.alias        modules.dep.bin      modules.symbols.bin
    modules.alias.bin    modules.devname
    modules.builtin      modules.order

```sh
    root@edison:/lib/modules/3.10.17-poky-edison+# ln -s /home/root/usr/src/linux-headers-3.10.17-poky-edison build
```

```sh
    root@edison:/lib/modules/3.10.17-poky-edison+# cd
    root@edison:~# 
```

```sh
    root@edison:~# mkdir kernelmodule
    root@edison:~# cd kernelmodule/
    root@edison:~/kernelmodule# nano helloworld.c
```

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

```sh
    root@edison:~/kernelmodule# nano Makefile
```

```Makefile
obj-m += helloworld.o

all:
  make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
  make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

```sh
    root@edison:~/kernelmodule# make
    make -C /lib/modules/3.10.17-poky-edison+/build M=/home/root/kernelmodule modules
    make[1]: Entering directory '/home/root/usr/src/linux-headers-3.10.17-poky-edison'
      CC [M]  /home/root/kernelmodule/helloworld.o
      Building modules, stage 2.
      MODPOST 1 modules
      CC      /home/root/kernelmodule/helloworld.mod.o
      LD [M]  /home/root/kernelmodule/helloworld.ko
    make[1]: Leaving directory '/home/root/usr/src/linux-headers-3.10.17-poky-edison'
```

```sh
    root@edison:~/kernelmodule# dmesg
    ...
    [   20.395746] ip (334) used greatest stack depth: 5208 bytes left
    root@edison:~/kernelmodule# insmod helloworld.ko
    root@edison:~/kernelmodule# dmesg
    ...
    [   20.395746] ip (334) used greatest stack depth: 5208 bytes left
    [26227.828425] Module? Hello!
```

```sh
    root@edison:~/kernelmodule# rmmod helloworld.ko
    root@edison:~/kernelmodule# dmesg
    ...
    [   21.122640] snd_intel_sst: runtime_suspend called                                               [96175.271153] Module? Hello! 
    [96185.098677] Module? Bye!
```

- [Compiling drivers for Poky 3.10.17-poky-edison+ directly on EDISON (in 10 steps :))](https://communities.intel.com/thread/62873?start=0&tstart=0)
- [Getting Started with the Edi-Expand](http://www.tektyte.com/docs/docpages/edi-expand/gettingstarted.html)

## Others

    user@host:~$ nano edison-src/meta-intel-edison/meta-intel-edison-bsp/recipes-kernel/linux/files/defconfig
    user@host:~$ nano edison-src/meta-intel-edison/meta-intel-edison-bsp/recipes-kernel/linux/files/upstream_to_edison.patch
    user@host:~$ find -name 
    user@host:~$ cp /build/tmp/work/edison-poky-linux/linuxyocto/3.10.17+gitAUTOINC+6ad20f049a_c03195ed6e-r0/linux-edison-standardbuild/.config build/tmp/work/edison-poky-linux/linuxyocto/3.10.17+gitAUTOINC+6ad20f049a_c03195ed6er0/defconfig
