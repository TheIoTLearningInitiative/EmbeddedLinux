Linux Kernel
==

## Intel Edison Default Version

    VERSION = 3
    PATCHLEVEL = 10
    SUBLEVEL = 17
    EXTRAVERSION =
    NAME = TOSSUG Baby Fish

ToDo Explain Linux Kernel Version, do we have this under Operating System?

Kernel
==

# Explain how we give support ot Linux Kernel

> Intel Silvermont (Atom)

> Mobile Internet Device(MID)

> Medfield is the follow-up of Moorestown, it combines two chip solution into one. Other than that it also added always-on and constant tsc and lapic timers. Medfield is the platform name, and the chip name is called Penwell we treat Medfield/Penwell as a variant of Moorestown. Penwell can be identified via MSRs.

> Intel MID is Intel's Low Power Intel Architecture (LPIA) based Mobile Internet Device(MID) platform. Unlike standard x86 PCs, Intel MID does not have many legacy devices nor standard legacy replacement devices/features. e.g. It does not contain i8259, i8254, HPET, legacy BIOS, most of the io ports.

## Intel Edison Linux Kernel Patched Files

```sh
    Documentation/kernel-parameters.txt
    arch/x86/configs/i386_edison_defconfig
    arch/x86/
    arch/x86/platform/intel-mid/
    arch/x86/platform/mrst/
    drivers/acpi/
    drivers/bluetooth/
    drivers/cpufreq/
    drivers/dma/
    drivers/gpio/
    drivers/hwmon/intel_mcu_common.c
    drivers/hwmon/intel_mcu_common.h
    drivers/hwmon/intel_mid_gpadc.c
    drivers/i2c/busses/
    drivers/idle/
    drivers/iio/adc/
    drivers/iio/adc/iio_basincove_gpadc.c
    drivers/iio/adc/ti-ads7955.c
    drivers/misc/bcm-lpm/bcm_bt_lpm.c
    drivers/misc/emmc_ipanic.c
    drivers/misc/pti.c
    drivers/misc/stm.c
    drivers/misc/stm.h
    drivers/mmc/card/block.c
    drivers/mmc/core/
    drivers/mmc/host/
    drivers/net/wireless/
    drivers/pci/pci-atom_soc.c
    drivers/platform/x86/
    drivers/pci/pci-atom_soc.c
    drivers/pci/pci.c
    drivers/pci/quirks.c
    drivers/platform/x86/Kconfig
    drivers/platform/x86/Makefile
    drivers/platform/x86/intel_mid_powerbtn.c
    drivers/platform/x86/intel_mid_thermal.c
    drivers/platform/x86/intel_pmic_gpio.c
    drivers/platform/x86/intel_psh_ipc.c
    drivers/platform/x86/intel_scu_flis.c
    drivers/platform/x86/intel_scu_fw_update.c
    drivers/platform/x86/intel_scu_ipc.c
    drivers/platform/x86/intel_scu_ipcutil.c
    drivers/platform/x86/intel_scu_mip.c
    drivers/platform/x86/intel_scu_pmic.c
    drivers/power/
    drivers/pwm/
    drivers/regulator/
    drivers/remoteproc/
    drivers/rpmsg/
    drivers/rtc/
    drivers/spi/
    drivers/thermal/
    drivers/tty/serial/
    drivers/usb/core/
    drivers/usb/dwc3/
    drivers/usb/gadget/
    drivers/usb/host/
    drivers/watchdog/
    net/bluetooth/l2cap_core.c
    sound/core/
    sound/soc/
    sound/soc/codecs/sn95031.c
    sound/soc/codecs/wm8994.c
    sound/soc/codecs/wm_hubs.c
    sound/soc/intel/
```

## Kernel Interfaces

### SFI Simple Firmware Interface

> How does SFI relate to ACPI? While some modern platforms can used SFI instead of using ACPI, SFI is not intended to replace ACPI on general purpose systems. If a platform were to export both SFI and ACPI booted an OS that also supports both, the OS should use the platform's ACPI support and ignore SFI.

- http://www.h-online.com/open/news/item/Intel-develops-simpler-alternative-to-ACPI-for-Linux-742161.html    
- https://en.wikipedia.org/wiki/Simple_Firmware_Interface
- https://simplefirmware.org/
- https://www.kernel.org/doc/ols/2009/ols2009-pages-55-60.pdf
- https://lwn.net/Articles/406228/
- https://simplefirmware.org/faq
- http://geektimes.ru/post/255136/
- https://communities.intel.com/message/273743
- https://edison.internet-share.com/w/index.php?title=Using_a_stock_Linux_kernel_with_Intel_Edison&redirect=no

```sh
    User Linux Next
    git clone git://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git
    v4.1-rc6 tag, mrproper'd and rebuilt, 
```sh
