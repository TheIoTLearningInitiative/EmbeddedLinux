SandBox
==

ToDo Explain Linux Kernel Version, do we have this under Operating System?, Explain how we give support ot Linux Kernel

## Kernel Interfaces

### SFI Simple Firmware Interface

> How does SFI relate to ACPI? While some modern platforms can used SFI instead of using ACPI, SFI is not intended to replace ACPI on general purpose systems. If a platform were to export both SFI and ACPI booted an OS that also supports both, the OS should use the platform's ACPI support and ignore SFI.

```sh
    User Linux Next
    git clone git://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git
    v4.1-rc6 tag, mrproper'd and rebuilt, 
```

## Links

- http://www.h-online.com/open/news/item/Intel-develops-simpler-alternative-to-ACPI-for-Linux-742161.html    
- https://en.wikipedia.org/wiki/Simple_Firmware_Interface
- https://simplefirmware.org/
- https://www.kernel.org/doc/ols/2009/ols2009-pages-55-60.pdf
- https://lwn.net/Articles/406228/
- https://simplefirmware.org/faq
- http://geektimes.ru/post/255136/
- https://communities.intel.com/message/273743
- https://edison.internet-share.com/w/index.php?title=Using_a_stock_Linux_kernel_with_Intel_Edison&redirect=no
