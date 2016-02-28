Kernel
==

## Intel Edison Default Version

    VERSION = 3
    PATCHLEVEL = 10
    SUBLEVEL = 17
    EXTRAVERSION =
    NAME = TOSSUG Baby Fish

ToDo Explain Linux Kernel Version, do we have this under Operating System?


# Explain how we give support ot Linux Kernel

> Intel Silvermont (Atom)

> Mobile Internet Device(MID)

> Medfield is the follow-up of Moorestown, it combines two chip solution into one. Other than that it also added always-on and constant tsc and lapic timers. Medfield is the platform name, and the chip name is called Penwell we treat Medfield/Penwell as a variant of Moorestown. Penwell can be identified via MSRs.

> Intel MID is Intel's Low Power Intel Architecture (LPIA) based Mobile Internet Device(MID) platform. Unlike standard x86 PCs, Intel MID does not have many legacy devices nor standard legacy replacement devices/features. e.g. It does not contain i8259, i8254, HPET, legacy BIOS, most of the io ports.

## Kernel Interfaces

### SFI Simple Firmware Interface

> How does SFI relate to ACPI? While some modern platforms can used SFI instead of using ACPI, SFI is not intended to replace ACPI on general purpose systems. If a platform were to export both SFI and ACPI booted an OS that also supports both, the OS should use the platform's ACPI support and ignore SFI.

```sh
    User Linux Next
    git clone git://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git
    v4.1-rc6 tag, mrproper'd and rebuilt, 
```

## Links

- [Creating a Custom Linux Kernel for the Edison](http://shawnhymel.com/585/creating-a-custom-linux-kernel-for-the-edison/)
- http://www.h-online.com/open/news/item/Intel-develops-simpler-alternative-to-ACPI-for-Linux-742161.html    
- https://en.wikipedia.org/wiki/Simple_Firmware_Interface
- https://simplefirmware.org/
- https://www.kernel.org/doc/ols/2009/ols2009-pages-55-60.pdf
- https://lwn.net/Articles/406228/
- https://simplefirmware.org/faq
- http://geektimes.ru/post/255136/
- https://communities.intel.com/message/273743
- https://edison.internet-share.com/w/index.php?title=Using_a_stock_Linux_kernel_with_Intel_Edison&redirect=no
