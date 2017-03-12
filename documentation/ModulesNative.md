# Native

# Project: Hello World Kernel Module Native Compilation

## Kernel Headers Setup

```sh
root@edison:~# cd
root@edison:~# wget https://github.com/SourceCodeCat/IoTDownloads/raw/master/linux-headers-3.10.17-poky-edison_3.10.17-poky-edison-1_i386.deb
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
root@edison:~# uname -a
Linux edison 3.10.98-poky-edison+ #1 SMP PREEMPT Mon Jun 6 14:32:08 PDT 2016 i6x
root@edison:~# 
```

## Version 3.10.98-poky-edison+

```sh
root@edison:~# cd ~/usr/src/
root@edison:~# ln -s linux-headers-3.10.17-poky-edison linux-headers-3.10.98-poky-edison
root@edison:~/usr/src# ls ~/usr/src/                                            
linux-headers-3.10.17-poky-edison  linux-headers-3.10.98-poky-edison
```

```sh
root@edison:~# nano ~/usr/src/linux-headers-3.10.98-poky-edison/include/generated/utsrelease.h
#define UTS_RELEASE "3.10.98-poky-edison+"
<Save Changes>
```

```sh
root@edison:~# cd /lib/modules/3.10.98-poky-edison+
```

```sh
root@edison:/lib/modules/3.10.98-poky-edison+# ls
extra                modules.builtin.bin  modules.softdep
kernel               modules.dep          modules.symbols
modules.alias        modules.dep.bin      modules.symbols.bin
modules.alias.bin    modules.devname
modules.builtin      modules.order
```

```sh
root@edison:/lib/modules/3.10.98-poky-edison+# ln -s /home/root/usr/src/linux-headers-3.10.98-poky-edison build
```

```sh
    root@edison:/lib/modules/3.10.98-poky-edison+# cd
    root@edison:~# 
```

## Version 3.10.17-poky-edison+

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
```

```sh
    root@edison:/lib/modules/3.10.17-poky-edison+# ln -s /home/root/usr/src/linux-headers-3.10.17-poky-edison build
```

```sh
    root@edison:/lib/modules/3.10.17-poky-edison+# cd
    root@edison:~# 
```

## Kernel Module Compilation

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

## Project: Hello World Kernel Module Native Compilation Automatic Startup

ToDo