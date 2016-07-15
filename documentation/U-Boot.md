# U-Boot

> Das U-Boot (Universal Bootloader) is an open source, primary boot loader used in embedded devices to package the instructions to boot the device's operating system kernel. It is available for a number of computer architectures, including 68k, ARM, AVR32, Blackfin, MicroBlaze, MIPS, Nios, SuperH, PPC and x86.- [Wikipedia](https://en.wikipedia.org/wiki/Das_U-Boot)

# Host Computer / Board Connection

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

# Bootup Cancel

```sh
******************************                                                  
PSH KERNEL VERSION: b0182b2b                                                    
                WR: 20104000                                                    
******************************                                                  
                                                                                
SCU IPC: 0x800000d0  0xfffce92c                                                 
                                                                                
PSH miaHOB version: TNG.B0.VVBD.0000000c                                        
                                                                                
microkernel built 11:24:08 Feb  5 2015                                          
                                                                                
******* PSH loader *******                                                      
PCM page cache size = 192 KB                                                    
Cache Constraint = 0 Pages                                                      
Arming IPC driver ..                                                            
Adding page store pool ..                                                       
PagestoreAddr(IMR Start Address) = 0x04899000                                   
pageStoreSize(IMR Size)          = 0x00080000                                   
                                                                                
*** Ready to receive application ***                                            
                                                                                
                                                                                
U-Boot 2014.04 (Jun 06 2016 - 14:40:07)                                         
                                                                                
       Watchdog enabled                                                         
DRAM:  980.6 MiB                                                                
MMC:   tangier_sdhci: 0                                                         
In:    serial                                                                   
Out:   serial                                                                   
Err:   serial                                                                   
Hit any key to stop autoboot:  1
boot > 
```

# U-Boot Commands from U-Boot

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

## printenv

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

# Bootup Kernel

```sh
U-Boot 2014.04 (Jun 06 2016 - 14:40:07)                                         
                                                                                
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
5461344 bytes read in 134 ms (38.9 MiB/s)                                       
Valid Boot Flag                                                                 
Setup Size = 0x00003c00                                                         
Magic signature found                                                           
Using boot protocol version 2.0c                                                
Linux kernel version 3.10.98-poky-edison+ (neck@flax) #1 SMP PREEMPT Mon Jun 6 6
Building boot_params at 0x00090000                                              
Loading bzImage at address 00100000 (5445984 bytes)                             
Magic signature found                                                           
Kernel command line: "rootwait root=PARTUUID=012b3303-34ac-284d-99b4-34e03a2335"
                                                                                
Starting kernel ...                                                             
                                                                                
[    1.603619] snd_soc_sst_platform: Enter:sst_soc_probe                        
[    2.087155] pmic_ccsm pmic_ccsm: Error reading battery profile from battid fk
[    2.096126] pmic_ccsm pmic_ccsm: Battery Over heat exception                 
[    2.096208] pmic_ccsm pmic_ccsm: Battery0 temperature inside boundary        
                                                                                
Welcome to Linux!                                                               
                                                                                
[    2.771628] systemd[1]: [/lib/systemd/system/wyliodrin-server.service:3] Fait
         Expecting device dev-ttyMFD2.device.../wyliodrin-hypervisor.service:3]t
[  OK  ] Reached target Remote File Systems.                                    
         Expecting device dev-disk-by\x2dpartlabel-factory.device...            
         Expecting device sys-subsystem-net-devices-usb0.device...              
[  OK  ] Reached target Paths.                                                  
[  OK  ] Reached target Swap.                                                   
[  OK  ] Set up automount boot.automount.                                       
[  OK  ] Created slice Root Slice.                                              
[  OK  ] Created slice User and Session Slice.                                  
[  OK  ] Listening on Delayed Shutdown Socket.                                  
[  OK  ] Listening on /dev/initctl Compatibility Named Pipe.                    
[  OK  ] Listening on udev Control Socket.                                      
[  OK  ] Listening on udev Kernel Socket.                                       
[  OK  ] Listening on Journal Socket.                                           
[  OK  ] Created slice System Slice.                                            
         Mounting Temporary Directory...                                        
[  OK  ] Created slice system-serial\x2dgetty.slice.                            
[  OK  ] Created slice system-getty.slice.                                      
         Starting Create list of required static device nodes...rrent kernel... 
         Starting udev Coldplug all Devices...                                  
         Starting Load Kernel Modules...                                        
         Mounting Debug File System...                                          
         Mounting POSIX Message Queue File System...                            
         Starting Apply Kernel Variables...                                     
         Starting Journal Service...                                            
[  OK  ] Started Journal Service.                                               
[  OK  ] Reached target Slices.                                                 
         Starting Remount Root and Kernel File Systems...                       
[  OK  ] Set up automount home.automount.                                       
[  OK  ] Mounted POSIX Message Queue File System.                               
[  OK  ] Mounted Debug File System.                                             
[  OK  ] Mounted Temporary Directory.                                           
[  OK  ] Started Create list of required static device nodes ...current kernel. 
[  OK  ] Started Apply Kernel Variables.                                        
[  OK  ] Started Remount Root and Kernel File Systems.                          
[  OK  ] Started udev Coldplug all Devices.                                     
[  OK  ] Started Load Kernel Modules.                                           
         Mounting Configuration File System...                                  
         Mounting FUSE Control File System...                                   
         Starting Load/Save Random Seed...                                      
         Starting Create Static Device Nodes in /dev...                         
[  OK  ] Mounted FUSE Control File System.                                      
[  OK  ] Mounted Configuration File System.                                     
[  OK  ] Started Load/Save Random Seed.                                         
[  OK  ] Started Create Static Device Nodes in /dev.                            
         Starting udev Kernel Device Manager...                                 
[  OK  ] Reached target Local File Systems (Pre).                               
         Mounting /var/volatile...                                              
[  OK  ] Started udev Kernel Device Manager.                                    
[  OK  ] Mounted /var/volatile.                                                 
[  OK  ] Reached target Local File Systems.                                     
         Starting Trigger Flushing of Journal to Persistent Storage...          
         Starting Create Volatile Files and Directories...                      
[  OK  ] Started Create Volatile Files and Directories.                         
[  OK  ] Started Trigger Flushing of Journal to Persistent Storage.             
         Starting Network Time Synchronization...                               
         Starting Update UTMP about System Boot/Shutdown...                     
[  OK  ] Found device /dev/ttyMFD2.                                             
[  OK  ] Started Network Time Synchronization.                                  
[  OK  ] Found device /dev/disk/by-partlabel/factory.                           
[  OK  ] Started Update UTMP about System Boot/Shutdown.                        
[  OK  ] Created slice system-systemd\x2drfkill.slice.                          
         Starting Load/Save RF Kill Switch Status of rfkill0...                 
         Starting Load/Save RF Kill Switch Status of rfkill1...                 
         Mounting Mount for factory...                                          
[  OK  ] Started Load/Save RF Kill Switch Status of rfkill0.                    
[  OK  ] Started Load/Save RF Kill Switch Status of rfkill1.                    
[  OK  ] Mounted Mount for factory.                                             
[  OK  ] Reached target Sound Card.                                             
[  OK  ] Reached target System Initialization.                                  
[  OK  ] Listening on RPCbind Server Activation Socket.                         
[  OK  ] Listening on D-Bus System Message Bus Socket.                          
[  OK  ] Reached target Timers.                                                 
         Starting Restore Sound Card State...                                   
         Starting Console System Startup Logging...                             
[  OK  ] Started Console System Startup Logging.                                
[  OK  ] Found device /sys/subsystem/net/devices/usb0.                          
[  OK  ] Created slice system-systemd\x2dfsck.slice.                            
         Starting File System Check on /dev/disk/by-partlabel/home...           
         Starting Load/Save RF Kill Switch Status of rfkill2...                 
[  OK  ] Listening on sshd.socket.                                              
[  OK  ] Started Load/Save RF Kill Switch Status of rfkill2.                    
[    7.892042] systemd-fsck[182]: /dev/mmcblk0p10: clean, 15/87120 files, 14184s
[  OK  ] Reached target Sockets.                                                
[  OK  ] Reached target Basic System.                                           
         Starting Edison PWR button handler...                                  
[  OK  ] Started Edison PWR button handler.                                     
         Starting Edison sketch check service...                                
[  OK  ] Started Edison sketch check service.                                   
         Starting Daemon to load edison mcu app binary...                       
[  OK  ] Started Daemon to load edison mcu app binary.                          
         Starting Telephony service...                                          
Application available at (physical) address 0x04819000                          
        VRL mapped to 0xff217000                                                
        App size = 11508 bytes                                                  
                                                                                
        App Authentication feature is disabled!                                 
        Resetting IPC                                                           
                                                                                
*** Ready to receive application ***                                            
         Starting OpenSSH Key Generation...                                     
         Starting Start or stop WiFI AP Mode in Edison...                       
[  OK  ] Started Start or stop WiFI AP Mode in Edison.                          
         Starting Wyliodrin hypervisor...                                       
         Starting Bluetooth rf kill event daemon...                             
[  OK  ] Started Bluetooth rf kill event daemon.                                
         Starting Daemon to handle arduino sketches...                          
[  OK  ] Started Daemon to handle arduino sketches.                             
         Starting Daemon to reset sketches...                                   
[  OK  ] Started Daemon to reset sketches.                                      
         Starting Wyliodrin server...                                           
         Starting Login Service...                                              
         Starting D-Bus System Message Bus...                                   
[  OK  ] Started D-Bus System Message Bus.                                      
[  OK  ] Started Telephony service.                                             
         Starting Network Service...                                            
         Starting Watchdog sample daemon...                                     
[  OK  ] Started Watchdog sample daemon.                                        
         Starting Crashlog service...                                           
[  OK  ] Started Crashlog service.                                              
         Starting Cleanjournal service...                                       
[  OK  ] Started Cleanjournal service.                                          
         Starting Permit User Sessions...                                       
[  OK  ] Started Network Service.                                               
[  OK  ] Started File System Check on /dev/disk/by-partlabel/home.              
[  OK  ] Started OpenSSH Key Generation.                                        
[  OK  ] Started Permit User Sessions.                                          
[  OK  ] Started Login Service.                                                 
         Starting Bluetooth service...                                          
         Starting Serial Getty on ttyMFD2...                                    
[  OK  ] Started Serial Getty on ttyMFD2.                                       
         Starting Getty on tty1...                                              
[  OK  ] Started Getty on tty1.                                                 
[  OK  ] Reached target Login Prompts.                                          
         Mounting /home...                                                      
[  OK  ] Reached target Network.                                                
         Starting Mosquitto - lightweight server implementati...SN protocols... 
         Starting Zero-configuration networking...                              
         Starting Network Name Resolution...                                    
[  OK  ] Mounted /home.                                                         
[  OK  ] Started Mosquitto - lightweight server implementatio...T-SN protocols. 
[  OK  ] Started Network Name Resolution.                                       
[  OK  ] Started Zero-configuration networking.                                 
[  OK  ] Started Bluetooth service.                                             
[  OK  ] Started Restore Sound Card State.                                      
         Starting PulseAudio Sound System...                                    
         Starting Hostname Service...                                           
         Starting The Edison status and configuration service...                
[  OK  ] Started The Edison status and configuration service.                   
         Starting Intel_XDK_Daemon...                                           
[  OK  ] Started Intel_XDK_Daemon.                                              
[  OK  ] Started Hostname Service.                                              
[  OK  ] Created slice user-0.slice.                                            
         Starting User Manager for UID 0...                                     
[  OK  ] Started User Manager for UID 0.                                        
[  OK  ] Started Wyliodrin hypervisor.                                          
[  OK  ] Started PulseAudio Sound System.                                       
[  OK  ] Started Wyliodrin server.                                              
[  OK  ] Reached target Multi-User System.                                      
         Starting Redis Server...                                               
[  OK  ] Started Redis Server.                                                  
                                                                                
Poky (Yocto Project Reference Distro) 1.7.3 edison ttyMFD2                      
                                                                                
edison login: 
```

# U-Boot Commands from Linux

```sh
root@edison:~# fw_
fw_printenv  fw_setenv    
root@edison:~#    
```

```sh
root@edison:~# fw_printenv
...
uuid_update=faec2ecf-8544-e241-b19d-757e796da607
first_install_retry=0
bootargs_target=multi-user
```