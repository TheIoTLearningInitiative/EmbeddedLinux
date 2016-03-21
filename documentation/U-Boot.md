U-Boot
==

> Das U-Boot (Universal Bootloader) is an open source, primary boot loader used in embedded devices to package the instructions to boot the device's operating system kernel. It is available for a number of computer architectures, including 68k, ARM, AVR32, Blackfin, MicroBlaze, MIPS, Nios, SuperH, PPC and x86.- [Wikipedia](https://en.wikipedia.org/wiki/Das_U-Boot)

```sh
    ******************************
    PSH KERNEL VERSION: b0182b2b
                    WR: 20104000
    ******************************
    
    SCU IPC: 0x800000d0  0xfffce92c
    
    PSH miaHOB version: TNG.B0.VVBD.0000000c
    
    microkernel built 11:24:08 Feb  5 2015
    
    ******* PSH loader *******CM page cache size = 192 KB 
    Cache Constrais
    Arming IPC driver ..
    Adding page store pool ..
    PagestoreAddr(IMR Start Address) = 0x04899000
    pagIMR Size)          = 0dy to receive application *** 
    
    
    U-Boot 2014.04 (Dec 19 2015 - 23:30:32)

           Watchdog enabled
    DRAM:  980.6 MiB
    MMC:   tangier_sdhci: 0
    In:    serial
    Out:   serial
    Err:   serial
    Hit any key to stop autoboot:  0
    boot > 
```

## help

```sh
    boot > help
    ?       - alias for 'help'
    askenv  - get environment variables from stdin
    base    - print or set address offset
    bdinfo  - print Board Info structure
    ...
    true    - do nothing, successfully
    version - print monitor, compiler and linker version
    zboot   - Boot bzImage
    boot > 
```
