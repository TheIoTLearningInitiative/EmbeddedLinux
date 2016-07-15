# Cross Compilation

# Hello World Kernel Module Cross Compilation

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

```sh
    user@host:~$ nano drivers/helloworld/Kconfig
```

```sh
    menu "Hello Module Kernel Support"
    config HELLO_WORLD
            tristate "Hello Module Driver"
            depends on X86
            help
              Select this option to run a Hello World Module!
    endmenu
```

```sh
    user@host:~$ nano drivers/helloworld/Makefile
```

```sh
    obj-$(CONFIG_HELLO_WORLD)               += helloworld.o
```

    user@host:~$ nano drivers/Kconfig

```sh
    menu "Device Drivers"
    source "drivers/helloworld/Kconfig"
    source "drivers/base/Kconfig"
    ...
```

```sh
    user@host:~$ nano drivers/Makefile
```

```sh
    ...
    # Rewritten to use lists instead of if-statements.
    #
    obj-$(CONFIG_HELLO_WORLD) += helloworld/
    obj-y += irqchip/
    ...
```

```sh
    user@host:~$ cd -
    user@host:~$ bitbake virtual/kernel -c menuconfig
    ...
    edison-src/out/linux64/build/tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux-edison-standard-build/Makefile
    ...
```

```sh
CONFIG_LOCALVERSION
Symbol: LOCALVERSION [=-yocto-xe1gyq]
  Type  : string
  Prompt: Local version - append to kernel release
  Location:
    -> General setup                      │  
  Defined at init/Kconfig:56
```

```sh
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

```sh
    user@host:~$ cp tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux-edison-standard-build/.config tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/defconfig 
    user@host:~$ cp tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux-edison-standard-build/.config tmp/work/edison-poky-linux/linux-yocto/3.10.17-r0/linux/arch/x86/configs/i386_edison_defconfig
    user@host:~$ bitbake virtual/kernel -c configure -f -v
    user@host:~$ cd ../../..
    user@host:~$ make image
    user@host:~$ make flash
```