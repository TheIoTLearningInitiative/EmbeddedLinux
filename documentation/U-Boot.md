U-Boot
==

> Das U-Boot (Universal Bootloader) is an open source, primary boot loader used in embedded devices to package the instructions to boot the device's operating system kernel. It is available for a number of computer architectures, including 68k, ARM, AVR32, Blackfin, MicroBlaze, MIPS, Nios, SuperH, PPC and x86.- [Wikipedia](https://en.wikipedia.org/wiki/Das_U-Boot)

## Host Computer / Board Connection

Connect Intel Edison to your Host Computer using the registered COM / TTY device and launch your serial interface, e.g. Linux

In Linux

```sh
    $ dmesg
    [11940.538090] ftdi_sio 6-1:1.0: FTDI USB Serial Device converter detected
    [11940.538137] usb 6-1: Detected FT232RL
    [11940.538139] usb 6-1: Number of endpoints 2
    [11940.538142] usb 6-1: Endpoint 1 MaxPacketSize 64
    [11940.538144] usb 6-1: Endpoint 2 MaxPacketSize 64
    [11940.538147] usb 6-1: Setting MaxPacketSize 64
    [11940.540185] usb 6-1: FTDI USB Serial Device converter now attached to ttyUSB0
   $ sudo minicom -D /dev/ttyUSB0 115200
```

## Bootup Cancel

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
    Hit any key to stop autoboot:  1
    boot > 
```

### help

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

### printenv

```sh
boot > printenv
audio_codec_name=audio_codec="dummy"
boot_target_cmd=run do_flash_os;run do_probe_dfu;run do_compute_target;run mmc-bootargs;run load_kernel;zboot ${loadaddr}
bootargs_console=console=ttyMFD2 earlyprintk=ttyMFD2,keep
bootargs_debug=loglevel=4
bootargs_ethconfig=cdc
bootargs_target=multi-user
bootcmd=echo "Target:${target_name}"; run do_partition; run do_handle_bootargs_mode;
bootdelay=1
dfu_alt_info_ram=kernel ram ${loadaddr} 0x800000
dfu_alt_info_reset=reset ram 0x0 0x0
dfu_to_sec=3
do_audio_support=setenv audio_support platform_mrfld_audio.${audio_codec_name}
do_boot=run boot_target_cmd;
do_bootargs_rootfs=setenv bootargs_rootfs rootwait root=PARTUUID=${uuid_rootfs} rootfstype=ext4
do_compute_target=if itest.b ${first_install_retry} -gt ${first_install_max_retries} || itest.b ${ota_update_retry} -gt $i
do_dfu_alt_info_ifwi=setenv dfu_alt_info "ifwi${hardware_id} mmc 0 8192 mmcpart 1;ifwib${hardware_id} mmc 0 8192 mmcpart "
do_dfu_alt_info_mmc=setenv dfu_alt_info "ifwi${hardware_id} mmc 0 8192 mmcpart 1;ifwib${hardware_id} mmc 0 8192 mmcpart 2"
do_dnx=setenv dfu_alt_info ${dfu_alt_info_ram};dfu 0 ram 0 ram;run bootcmd
do_fallback=echo "Unknown boot mode: $bootargs_mode"; env delete -f bootargs_mode; saveenv; echo "Resetting to default bo;
do_flash=run do_force_flash_os;
do_flash_ifwi=run do_dfu_alt_info_ifwi ; dfu 0 mmc 0
do_flash_os=if itest.b ${do_flash_os_done} -eq 1 ; then echo "Flashing already done..." ; else run do_force_flash_os; fi
do_flash_os_done=1
do_flashall=run do_partition;run do_flash_ifwi;run do_flash_os
do_force_flash_os=run do_dfu_alt_info_mmc ; sleep 1 ; setenv do_flash_os_done 1 ; saveenv ; dfu 0 mmc 0
do_force_partition=echo "Partitioning using GPT"; gpt write mmc 0 ${partitions} ; mmc rescan; setenv do_partition_done 1 v
do_handle_bootargs_mode=run do_preprocess_bootargs_mode; if itest.s $bootargs_mode == "ota" ; then run do_ota; fi; if ite;
do_load_ota_scr=if fatload mmc 0:9 $ota_script_addr ota_update.scr ; then setenv ota_status 0 ; else setenv ota_status 1 i
do_ota=run do_ota_init ; run do_load_ota_scr ; run do_source_ota_scr ; run do_ota_clean
do_ota_clean=saveenv ; reset
do_ota_init=setenv ota_status 1 ; env delete -f bootargs_mode
do_partition=if itest.b ${do_partition_done} -eq 1; then echo "Partitioning already done..."; else run do_force_partitioni
do_partition_done=1
do_preprocess_bootargs_mode=if env exists bootargs_mode ; then ; else setenv bootargs_mode "boot" ;fi;
do_probe_dfu=run do_dfu_alt_info_mmc ; dfu 0 mmc 0 $dfu_to_sec
do_source_ota_scr=if test $ota_status -eq 0 ; then if source $ota_script_addr ; then setenv ota_status 0 ; else setenv oti
first_install_max_retries=3
first_install_retry=0
hardware_id=00
init_dfu=run do_dfu_alt_info_mmc ; saveenv
load_kernel=fatload mmc 0:7 ${loadaddr} vmlinuz
loadaddr=0x100000
mmc-bootargs=run do_bootargs_rootfs; run do_audio_support; setenv bootargs ${bootargs_rootfs} ${bootargs_console} ${boota}
ota_done=0
ota_script_addr=0x100000
ota_update_max_retries=3
ota_update_retry=0
partitions=uuid_disk=${uuid_disk};name=u-boot0,start=1MiB,size=2MiB,uuid=${uuid_uboot0};name=u-boot-env0,size=1MiB,uuid=$;
serial#=4d143757d2d7fce20e89640fee58c2af
stderr=serial
stdin=serial
stdout=serial
target_name=blank
usb0addr=02:00:86:58:c2:af
uuid_boot=db88503d-34a5-3e41-836d-c757cb682814
uuid_disk=21200400-0804-0146-9dcc-a8c51255994f
uuid_factory=333a128e-d3e3-b94d-92f4-d3ebd9b3224f
uuid_home=f13a0978-b1b5-1a4e-8821-39438e24b627
uuid_panic=f20aa902-1c5d-294a-9177-97a513e3cae4
uuid_rootfs=012b3303-34ac-284d-99b4-34e03a2335f4
uuid_uboot0=d117f98e-6f2c-d04b-a5b2-331a19f91cb2
uuid_uboot1=8a4bb8b4-e304-ae48-8536-aff5c9c495b1
uuid_uboot_env0=25718777-d0ad-7443-9e60-02cb591c9737
uuid_uboot_env1=08992135-13c6-084b-9322-3391ff571e19
uuid_update=faec2ecf-8544-e241-b19d-757e796da607

Environment size: 4962/65531 bytes
boot > 
```

## Bootup Kernel

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
    Target:blank
    Partitioning already done...
    Flashing already done...
    GADGET DRIVER: usb_dnl_dfu
    reading vmlinuz
    5385504 bytes read in 133 ms (38.6 MiB/s)
    Valid Boot Flag
    Setup Size = 0x00003c00
    Magic signature found
    Using boot protocol version 2.0c
    Linux kernel version 3.10.17-yocto-standard (abraham@aarcemor-desk) #1 SMP PREEMPT Sat Dec 19 23:23:25 CST 2015
    Building boot_params at 0x00090000
    Loading bzImage at address 00100000 (5370144 bytes)
    Magic signature found
    Kernel command line: "rootwait root=PARTUUID=012b3303-34ac-284d-99b4-34e03a2335f4 rootfstype=ext4 console=ttyMFD2 earlyprintk=ttyMFD2,k"
    ...
    ...
    Poky (Yocto Project Reference Distro) 1.7.2 edison ttyMFD2
    
    edison login: root
    root@edison:~# 
```

```sh
root@edison:~# 
```