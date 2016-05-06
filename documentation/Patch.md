Patch
==

## Patch Location

```sh
    user@host:~$ ls edison-src/meta-intel-edison/meta-intel-edison-bsp/recipes-kernel/linux/files/
    defconfig  upstream_to_edison.patch
```

## Patched Files

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

## Patch Review


```sh
    x86 Intel MID Platform
    bcm43340
    Medfield MID Platform
    Intel MID Platform

arch/x86/Kconfig

    if X86_WANT_INTEL_MID
    config X86_INTEL_MID
    bool "Intel MID Platform"
       depends on PCI
       depends on PCI_GOANY
       depends on X86_IO_APIC
       select X86_INTEL_MID
       select SFI
       select INTEL_SCU_IPC
       select X86_PLATFORM_DEVICES
       select ARCH_HAVE_CUSTOM_GPIO_H
    
    config X86_MDFLD
    bool "Medfield MID platform"
       depends on X86_INTEL_MID
       select DW_APB_TIMER
       select APB_TIMER
       select I2C
       select SPI
       select INTEL_SCU_IPC
       select X86_PLATFORM_DEVICES
       select MFD_INTEL_MSIC
    
    config ATOM_SOC_POWER
    bool "Select Atom SOC Power"
    
    config INTEL_DEBUG_FEATURE
    bool "Debug feature interface on Intel MID platform"
       depends on X86_INTEL_MID
       Provides an interface to list the debug features
        that are enabled on an Intel MID platform. The
        enabling of the debug features depends on the mode
        the device is in (e.g. manufacturing, production,
        end user, etc...).

    config ARCH_NR_GPIO
       depends on ARCH_HAVE_CUSTOM_GPIO_H
       default 512 if X86_INTEL_MID
       default 0
        Maximum number of GPIOs in the system.

arch/x86/Kconfig.cpu

    config MSLM
           bool "Intel Silvermont (Atom)"
           ---help---
    
             Select this for the Intel Silvermont (Atom) platform. Intel Atom
             CPUs have an in-order pipelining architecture and thus can benefit
             from accordingly optimized code. Use a recent GCC with specific
             Atom support in order to fully benefit from selecting this option.
    
    X86_L1_CACHE_SHIFT
    X86_USE_PPRO_CHECKSUM
    X86_TSC
    X86_CMPXCHG64
    X86_CMOV
    
arch/x86/Makefile_32.cpu

            cflags-$(CONFIG_MSLM) += $(call cc-option,-march=slm) \
                $(call cc-option,-mtune=slm,$(call cc-option,-mtune=generic))
```

### Platform

#### Intel MID Specific Setup Code

```sh
    arch/x86/include/asm/intel-mid.h
``

It includes code from:

- SFI
- PCI
- Platform Device
- GPIO
- OEMB Table
- IAFW
- Device Creation (Board Information)
- x86_init, x86_platform_init

```sh
    #define INTEL_MID_OPS_INIT {\
           DECLARE_INTEL_MID_OPS_INIT(penwell, INTEL_MID_CPU_CHIP_PENWELL) \
           DECLARE_INTEL_MID_OPS_INIT(cloverview, INTEL_MID_CPU_CHIP_CLOVERVIEW) \
           DECLARE_INTEL_MID_OPS_INIT(tangier, INTEL_MID_CPU_CHIP_TANGIER) \
```

Related

```sh
    arch/x86/include/asm/intel_mid_gpadc.h
    arch/x86/include/asm/intel_mid_hsu.h
    arch/x86/include/asm/intel_mid_pcihelpers.h
    arch/x86/include/asm/intel_mid_powerbtn.h
    arch/x86/include/asm/intel_mid_pwm.h
    arch/x86/include/asm/intel_mid_remoteproc.h INTEL MID Remote Processor 
    arch/x86/include/asm/intel_mid_rpmsg.h
    arch/x86/include/asm/intel_mid_thermal.h
      SoC level power limits for thermal throttling
      intel mid thermal driver
    arch/x86/include/asm/module.h
      elif (defined CONFIG_MATOM) || (defined CONFIG_MSLM)
    arch/x86/include/asm/required-features.h
      if defined(CONFIG_MATOM) || defined(CONFIG_MSLM)
    arch/x86/include/asm/setup.h
      extern void x86_intel_mid_early_setup(void);
      static inline void x86_intel_mid_early_setup(void) { }
    arch/x86/include/uapi/asm/bootparam.h
    arch/x86/include/uapi/asm/msr-index.h
    arch/x86/kernel/cpu/common.c
    arch/x86/kernel/cpu/intel.c
      case 0x4A:      /* Merrifield */
    arch/x86/kernel/cpu/mcheck/therm_throt.c
    arch/x86/kernel/early_printk.c
    arch/x86/kernel/head32.c
      case X86_SUBARCH_INTEL_MID:
    arch/x86/kernel/irq.c
    arch/x86/kernel/rtc.c
    arch/x86/kernel/smpboot.c
    arch/x86/pci/mrst.c
    arch/x86/platform/Makefile
      obj-y  += intel-mid/
    arch/x86/platform/intel-mid/Makefile
      Very Important!
    arch/x86/platform/intel-mid/board.c | Intel Medfield based board (Blackbay)
      Very Important!
    arch/x86/platform/intel-mid/device_libs/Makefile
    arch/x86/platform/intel-mid/device_libs/pci/platform_sdhci_pci.c | mmc sdhci pci platform data initilization file
    arch/x86/platform/intel-mid/device_libs/pci/platform_sdhci_pci.h
    arch/x86/platform/intel-mid/device_libs/pci/platform_usb_otg.c | USB OTG platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_ads7955.c | ads7955 platform data initialization file
    arch/x86/platform/intel-mid/device_libs/platform_ads7955.h
    arch/x86/platform/intel-mid/device_libs/platform_bq24261.c | Platform data for bq24261 charger driver
    arch/x86/platform/intel-mid/device_libs/platform_bq24261.h
    arch/x86/platform/intel-mid/device_libs/platform_emc1403.c | emc1403 platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_emc1403.h
    arch/x86/platform/intel-mid/device_libs/platform_lis331.c | lis331 platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_lis331.h
    arch/x86/platform/intel-mid/device_libs/platform_max3111.c | max3111 platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_max3111.h
    arch/x86/platform/intel-mid/device_libs/platform_max7315.c | max7315 platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_max7315.h
    arch/x86/platform/intel-mid/device_libs/platform_mid_pwm.c | mid_pwm platform data initilization file
      PWM_LED
      PWM_VIBRATOR
      PWM_LCD_BACKLIGHT
    arch/x86/platform/intel-mid/device_libs/platform_mid_pwm.h
    arch/x86/platform/intel-mid/device_libs/platform_mpu3050.c | mpu3050 platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_mpu3050.h
    arch/x86/platform/intel-mid/device_libs/platform_mrfl_ocd.c | Platform data for Merrifield Platform OCD  Driver
      +#include <asm/intel-mid.h>
      +#include <asm/intel_mid_remoteproc.h>
      +#include <asm/intel_scu_ipc.h>
      +#include <asm/intel_basincove_ocd.h>
    arch/x86/platform/intel-mid/device_libs/platform_mrfl_ocd.h
    arch/x86/platform/intel-mid/device_libs/platform_mrfl_thermal.c | Intel Merrifield Platform thermal driver
    arch/x86/platform/intel-mid/device_libs/platform_mrfl_thermal.h
    arch/x86/platform/intel-mid/device_libs/platform_msic.c | MSIC platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_msic.h
    arch/x86/platform/intel-mid/device_libs/platform_msic_adc.c | MSIC ADC platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_msic_adc.h
    arch/x86/platform/intel-mid/device_libs/platform_msic_audio.c | MSIC audio platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_msic_audio.h
    arch/x86/platform/intel-mid/device_libs/platform_msic_battery.c | MSIC battery platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_msic_battery.h
    arch/x86/platform/intel-mid/device_libs/platform_msic_gpio.c | MSIC GPIO platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_msic_gpio.h
    arch/x86/platform/intel-mid/device_libs/platform_msic_ocd.c | MSIC OCD platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_msic_ocd.h
    arch/x86/platform/intel-mid/device_libs/platform_msic_power_btn.c | MSIC power btn platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_msic_power_btn.h
    arch/x86/platform/intel-mid/device_libs/platform_msic_thermal.c | msic_thermal platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_msic_thermal.h
    arch/x86/platform/intel-mid/device_libs/platform_pcal9555a.c | pcal9555a platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_pcal9555a.h
    arch/x86/platform/intel-mid/device_libs/platform_pmic_gpio.c | PMIC GPIO platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_pmic_gpio.h
    arch/x86/platform/intel-mid/device_libs/platform_scu_flis.c | scu_flis platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_scu_flis.h
    arch/x86/platform/intel-mid/device_libs/platform_sdio_regulator.c | sdio regulator platform device initilization file
    arch/x86/platform/intel-mid/device_libs/platform_soc_thermal.c | Platform data for SoC DTS driver
    arch/x86/platform/intel-mid/device_libs/platform_soc_thermal.h
    arch/x86/platform/intel-mid/device_libs/platform_spidev.c | spidev platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_spidev.h
    arch/x86/platform/intel-mid/device_libs/platform_tc35876x.c | tc35876x platform data initilization file
    arch/x86/platform/intel-mid/device_libs/platform_tc35876x.h
    arch/x86/platform/intel-mid/device_libs/platform_tca6416.c | tca6416 platform data initilization file
```

### APIC

> In computing, Intel's Advanced Programmable Interrupt Controller (APIC) is a family of interrupt controllers. As its name suggests, the APIC is more advanced than Intel's 8259 Programmable Interrupt Controller (PIC), particularly enabling the construction of multiprocessor systems. It is one of several architectural designs intended to solve interrupt routing efficiency issues in multiprocessor computer systems. [Wikipedia](https://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller)

```sh
    arch/x86/kernel/apic/apic.c
    arch/x86/kernel/apic/io_apic.c
```

### APB Timer

> Langwell is the south complex of Intel Moorestown MID platform. There are eight external timers in total that can be used by the operating system. The timer information, such as frequency and addresses, is provided to the OS via SFI tables. 

> Timer interrupts are routed via FW/HW emulated IOAPIC independently via individual redirection table entries (RTE). Unlike HPET, there is no master counter, therefore one of the timers are used as clocksource. The overall allocation looks like:
- timer 0 - NR_CPUs for per cpu timer
- one timer for clocksource
- one timer for watchdog driver.

> It is also worth notice that APB timer does not support true one-shot mode, free-running mode will be used here to emulate one-shot mode. APB timer can also be used as broadcast timer along with per cpu local APIC timer, but by default APB timer has higher rating than local APIC timers.

```sh
    arch/x86/kernel/apb_timer.c | Driver for Langwell APB timers
```
 
### Power

```sh
    arch/x86/include/asm/mwait.h
      +#ifdef CONFIG_ATOM_SOC_POWER
      +#define MWAIT_MAX_NUM_CSTATES          10
      +#else
      +#define MWAIT_MAX_NUM_CSTATES          8
      +#endif
    arch/x86/include/asm/pmic_pdata.h
      pmic_platform_data
      #ifdef CONFIG_PMIC_CCSM
    arch/x86/platform/intel-mid/device_libs/platform_mrfl_pmic.c | latform data for Merrifield PMIC driver
      #include <linux/sfi.h>
      #include <linux/power/bq24261_charger.h>
    arch/x86/platform/intel-mid/device_libs/platform_mrfl_pmic.h | platform data for pmic driver
    arch/x86/platform/intel-mid/device_libs/platform_mrfl_pmic_i2c.c | Platform data for Merrifield PMIC I2C
    arch/x86/platform/intel-mid/device_libs/platform_mrfl_pmic_i2c.h
    arch/x86/platform/intel-mid/device_libs/platform_mrfl_regulator.c
```

### Debug

```sh
    arch/x86/include/asm/intel_soc_debug.h
```

### MIP

```sh
    arch/x86/include/asm/intel_mip.h
```

### SCU IPC

> The IPC is used to bridge the communications between kernel and SCU on some embedded Intel x86 platforms.

> Driver for the Intel SCU IPC mechanism

> SCU runing in ARC processor communicates with other entity running in IA core through IPC mechanism which in turn messaging between IA core ad SCU. SCU has two IPC mechanism IPC-1 and IPC-2. IPC-1 is used between IA32 and SCU where IPC-2 is used between P-Unit and SCU. This driver delas with IPC-1 Driver provides an API for power control unit registers (e.g. MSIC) along with other APIs.

```sh
    obj-$(CONFIG_INTEL_SCU_IPC)	+= intel_scu_ipc.o
    arch/x86/Kconfig | Not Edison Patch 
    arch/x86/include/asm/intel_scu_ipc.h | Not Edison Patch 
    arch/x86/kernel/Makefile | Not Edison Patch 
    arch/x86/kernel/intel_scu_ipc.c | Not Edison Patch
    
    arch/x86/include/asm/intel_scu_flis.h | SCU FLIS Interfaces
    arch/x86/include/asm/intel_scu_ipc.h
    arch/x86/include/asm/intel_scu_ipcutil.h
    arch/x86/include/asm/intel_scu_pmic.h
    arch/x86/include/asm/scu_ipc_rpmsg.h
    
    arch/x86/platform/intel-mid/device_libs/platform_ipc.c | IPC platform library file
    arch/x86/platform/intel-mid/device_libs/platform_ipc.h
    
    OSHOB-OS Handoff Buffer
    OSNIB interface
    scu_ipc_pmdb_buffer
```

### Virtual Real Time Clock (VRTC)

> VRTC is emulated by system controller firmware, the real HW RTC is located in the PMIC device. SCU FW shadows PMIC RTC in a memory mapped IO space that is visible to the host IA processor. This driver is based on RTC CMOS driver.

> Moorestown platform doesn't have a m146818 RTC device like traditional x86 PC, but a firmware emulated virtual RTC device(vrtc), which provides some basic RTC functions like get/set time. vrtc serves as the only wall clock device on Moorestown platform.

> Currently, vrtc init func will be called as arch_initcall() before xtime's init. Also move the sfi vrtc table parsing from mrst.c to vrtc.c

There will be another general vrtc driver for rtc subsystem

```sh
    arch/x86/include/asm/intel_mid_vrtc.h
    
    obj-$(CONFIG_X86_MRST)		+= mrst.o vrtc.o
    arch/x86/include/asm/fixmap.h
    arch/x86/include/asm/vrtc.h
    arch/x86/kernel/mrst.c
    arch/x86/kernel/vrtc.c
    arch/x86/platform/mrst/vrtc.c | Driver for virtual RTC device on Intel MID platform
```    

### HSU

> Intel Medfield platform has a high speed UART device, which could act as a early console. To enable early printk of HSU console, simply add "earlyprintk=hsu" in kernel command line. Currently we put the code in the early_printk_mrst.c as it is also for Intel MID platforms like the mrst early console

#### Upstream patch

- arch/x86/include/asm/intel_mid_hsu.h
- arch/x86/include/asm/mrst.h
- arch/x86/kernel/early_printk.c
- arch/x86/kernel/early_printk_mrst.c
- include/linux/platform_data/dma-hsu.h | Changes for High Speed UART DMA
- drivers/dma/hsu/hsu.c
- drivers/dma/hsu/pci.c
- drivers/external_drivers/drivers/hsu/mfd_pci.c

It includes enums from:

- hsu_port0
- hsu_port1
- hsu_port2
- bt_port
- modem_port
- gps_port
- debug_port
- hsu_intel
- hsu_dw

- arch/x86/platform/intel-mid/device_libs/platform_hsu.c
- arch/x86/platform/intel-mid/device_libs/platform_hsu.h

- https://communities.intel.com/thread/75472
- https://lkml.org/lkml/2010/9/13/33

### Basin Cove GPADC

> GPADC(General Purpose Analog Digital Converter)

    config BASINCOVE_GPADC
    depends on INTEL_SCU_IPC

- Platform data for Merrifield Basincove GPADC driver
- Intel Merrifield Basin Cove GPADC Driver
- BASINCOVE GPADC driver for Intel Merrifield platform

```c
    arch/x86/include/asm/intel_basincove_gpadc.h
    arch/x86/platform/intel-mid/device_libs/platform_bcove_adc.c
    arch/x86/platform/intel-mid/device_libs/platform_bcove_adc.h
    drivers/iio/adc/iio_basincove_gpadc.c
```

Related


```c
    ACPI / PMIC: support PMIC operation region for CrystalCove
    #define DRIVER_NAME "bcove_bcu"
    #define DEVICE_NAME "mrfl_pmic_bcu"
```

arch/x86/include/asm/intel_basincove_gpadc.h
arch/x86/include/asm/intel_basincove_ocd.h

### BlueTooth

Broadcom Bluetooth Low Power Mode
    
    bcm_bt_lpm

```c
    arch/x86/include/asm/bcm_bt_lpm.h
    drivers/misc/bcm-bt-lpm.c
    arch/x86/platform/intel-mid/device_libs/platform_btlpm.c | btlpm platform data initialization file
      Bluetooth is using UART port number 0
      .name = "bcm_bt_lpm",
      device_initcall(bluetooth_init);
```

### GPIO

```sh
arch/x86/include/asm/gpio.h
```

### GPIO Keys

> We will search these buttons in SFI GPIO table (by name) and register them dynamically. Please add all possible buttons here, we will shrink them if no GPIO found.

    arch/x86/platform/intel-mid/device_libs/platform_gpio_keys.c
      late_initcall(pb_keys_init);
    arch/x86/platform/intel-mid/device_libs/platform_gpio_keys.h

### I2C

```c
    arch/x86/platform/intel-mid/device_libs/platform_dw_i2c.c | I2C platform data initilization file
```

### SFI

```c
    config CONFIG_SFI
```

### Multi-Function Device (MFD) for Low Power Subsystem

### System Management Bus (SMBus).

